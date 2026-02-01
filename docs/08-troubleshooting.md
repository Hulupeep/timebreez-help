# Troubleshooting Guide - Common Issues & Solutions

## Who This Is For
**All Timebreez users** encountering errors or unexpected behavior.

## What You'll Learn
- Diagnosing common errors
- Solutions for all 8 demo mode fixes
- RLS policy violation resolution
- Browser and connectivity issues
- When to contact support

---

## 🚨 Critical Issues (Immediate Action Required)

### Issue: Room shows RED status (understaffed)
**Severity:** CRITICAL (compliance risk)
**Symptoms:** Room tile shows RED badge, present < required
**Impact:** Tusla violation, child safety risk
**Solution:**
1. **Immediate:** Dispatch cover staff (see [Cover Staff Guide](./03-cover-staff-dispatch.md#scenario-4))
2. **If no cover available:** Call in off-duty staff
3. **Last resort:** Move children to another room temporarily
4. **Document:** Create operational decision explaining the situation

---

### Issue: All staff disappeared from Control Desk
**Severity:** CRITICAL (data integrity)
**Symptoms:** All present counts show 0
**Impact:** Cannot monitor room status
**Solution:**
1. **Check Paxton integration:** Verify Net2 server is online
2. **Refresh page:** Force data reload
3. **Check attendance events:** Query `attendance_events` table directly
4. **If persists:** Contact support immediately (possible database issue)

---

## 🔧 Demo Mode Fixes (Waves 31-32)

### Fix #1: Control Desk Shows "No Rooms Configured"

**Symptoms:**
- Empty Control Desk page
- Error message "No rooms configured"
- OR only 0-2 rooms appear instead of 7

**Cause:**
- RLS (Row Level Security) policy missing on `get_room_snapshots()` RPC
- User not in demo org context
- Rooms not seeded for demo org

**Solution:**

**Step 1: Verify you're in demo mode**
```
1. Check URL: www.timebreez.com/login (not /signup)
2. Check org name: Should show "Sunshine Early Learning Centre"
3. Check demo org ID: 00000000-0000-0000-0000-000000000001
```

**Step 2: Refresh the page**
```
1. Click browser refresh (F5)
2. OR clear cache (Ctrl+Shift+R)
3. Expected: 7 room tiles appear
```

**Step 3: Check database (admin only)**
```sql
-- Verify RLS policy exists
SELECT * FROM pg_policies WHERE tablename = 'rooms';

-- Verify get_room_snapshots RPC has SECURITY DEFINER
SELECT proname, prosecdef FROM pg_proc WHERE proname = 'get_room_snapshots';

-- Verify demo rooms exist
SELECT COUNT(*) FROM rooms WHERE organization_id = '00000000-0000-0000-0000-000000000001';
-- Expected: 7
```

**Step 4: If still broken**
```
1. Report as critical bug
2. Include screenshot
3. Include browser console errors (F12 > Console)
```

**Related:**
- **Invariant:** I-DEMO-005
- **Wave:** 31 (Fix #1)
- **Test:** `tests/e2e/demo/demo_journey_comprehensive.spec.ts`

---

### Fix #2: Leave Coverage Shows "No Room Assignment Found"

**Symptoms:**
- Leave request cards show error instead of room name
- "No room assignment found" message
- Cannot determine coverage impact

**Cause:**
- Employee missing primary room assignment
- `employee_room_assignments.is_primary` is false for all rooms
- Employee has no room assignments at all

**Solution:**

**Step 1: Verify employee has room assignment**
```
1. Navigate to Employees
2. Click the employee with the issue
3. Check "Room Assignments" section
4. Expected: At least one room with "Primary" badge
```

**Step 2: Set primary room (if missing)**
```
1. Click "Edit" on employee
2. Scroll to "Room Assignments"
3. Check at least one room
4. Set one room as "Primary"
5. Click "Save"
```

**Step 3: Verify in database (admin only)**
```sql
-- Check employee room assignments
SELECT e.full_name, r.name, era.is_primary
FROM employees e
LEFT JOIN employee_room_assignments era ON e.id = era.employee_id
LEFT JOIN rooms r ON era.room_id = r.id
WHERE e.organization_id = '00000000-0000-0000-0000-000000000001';

-- Expected: Every employee has at least one is_primary = true
```

**Step 4: Re-seed demo data (if all broken)**
```sql
-- Run demo data migration again
-- supabase/migrations/090_demo_toil_and_payroll_data.sql
```

**Related:**
- **Invariant:** I-DEMO-004, I-DEMO-006
- **Wave:** 31 (Fix #2)
- **Test:** `tests/e2e/demo/demo_journey_comprehensive.spec.ts`

---

### Fix #3: Org Notifications Page Crashes

**Symptoms:**
- Navigate to Settings > Org Notifications
- White screen appears
- OR "RLS policy violation" error
- OR "permission denied for table notification_rules"

**Cause:**
- RLS policy missing on `notification_rules` table
- User not granted SELECT permission on `notification_rules`

**Solution:**

**Step 1: Refresh the page**
```
1. Press F5 or Ctrl+R
2. Expected: Page loads with notification rules visible
```

**Step 2: Check RLS policies (admin only)**
```sql
-- Verify RLS enabled
SELECT tablename, rowsecurity FROM pg_tables WHERE tablename = 'notification_rules';
-- rowsecurity should be true

-- Verify policy exists
SELECT * FROM pg_policies WHERE tablename = 'notification_rules';
-- Expected: Policy for SELECT allowing org members
```

**Step 3: Grant permissions (if missing)**
```sql
-- Create RLS policy for notification_rules
CREATE POLICY "Users can view notification_rules in their org"
  ON notification_rules FOR SELECT
  USING (
    organization_id IN (
      SELECT organization_id FROM employees WHERE user_id = auth.uid()
    )
  );
```

**Step 4: Verify fix**
```
1. Navigate to Settings > Org Notifications
2. Expected: Page loads, 4+ notification rules visible
3. Toggle switches should be functional
```

**Related:**
- **Invariant:** I-DEMO-003
- **Wave:** 31 (Fix #3)
- **Migration:** `supabase/migrations/103_fix_notifications_leave_types.sql`

---

### Fix #4: My Notifications Page Crashes

**Symptoms:**
- Navigate to Settings > My Notifications
- "RLS policy violation" error
- "permission denied for table notification_preferences"

**Cause:**
- RLS policy missing on `notification_preferences` table

**Solution:**

**Step 1: Refresh the page**
```
1. Press F5
2. Expected: Notification preferences form loads
```

**Step 2: Check RLS policies (admin only)**
```sql
-- Verify policy exists
SELECT * FROM pg_policies WHERE tablename = 'notification_preferences';

-- Create policy if missing
CREATE POLICY "Users can manage own notification_preferences"
  ON notification_preferences FOR ALL
  USING (employee_id IN (
    SELECT id FROM employees WHERE user_id = auth.uid()
  ));
```

**Step 3: Verify fix**
```
1. Navigate to Settings > My Notifications
2. Expected: Form loads with notification preferences
3. Can toggle settings and save
```

**Related:**
- **Invariant:** I-DEMO-003
- **Wave:** 31 (Fix #4)
- **Migration:** `supabase/migrations/103_fix_notifications_leave_types.sql`

---

### Fix #5: Leave Types Not Editable (UUID Validation Error)

**Symptoms:**
- Click "Edit" on a leave type
- "UUID validation error" or "invalid UUID" message
- Form won't open or won't save

**Cause:**
- Leave type ID not in valid UUID format
- Frontend validation too strict

**Solution:**

**Step 1: Verify leave type IDs (admin only)**
```sql
-- Check leave_types table
SELECT id, name, organization_id FROM leave_types
WHERE organization_id = '00000000-0000-0000-0000-000000000001';

-- All IDs should be valid UUIDs (format: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx)
```

**Step 2: Re-seed if invalid**
```sql
-- Delete invalid leave types
DELETE FROM leave_types WHERE organization_id = '00000000-0000-0000-0000-000000000001';

-- Re-run demo data migration
-- supabase/migrations/090_demo_toil_and_payroll_data.sql
```

**Step 3: Verify fix**
```
1. Navigate to Leave Types
2. Click "Edit" on any leave type
3. Expected: Edit form opens without error
4. Make a change and save
5. Expected: Success toast appears
```

**Related:**
- **Invariant:** I-DEMO-003
- **Wave:** 31 (Fix #5)
- **Migration:** `supabase/migrations/103_fix_notifications_leave_types.sql`

---

### Fix #6: Calendar Feed Doesn't Generate

**Symptoms:**
- Click "Generate Feed" button
- Nothing happens OR error appears
- No feed URL appears

**Cause:**
- `generate_calendar_feed_token` RPC missing or has permission issues

**Solution:**

**Step 1: Check if RPC exists**
```sql
SELECT proname FROM pg_proc WHERE proname = 'generate_calendar_feed_token';
-- Expected: One row returned
```

**Step 2: Verify RPC permissions**
```sql
-- RPC should be SECURITY DEFINER
SELECT proname, prosecdef FROM pg_proc WHERE proname = 'generate_calendar_feed_token';
-- prosecdef should be true

-- Grant execute permission
GRANT EXECUTE ON FUNCTION generate_calendar_feed_token TO authenticated;
```

**Step 3: Test RPC directly**
```sql
SELECT generate_calendar_feed_token();
-- Expected: Returns a UUID token
```

**Step 4: Verify fix**
```
1. Navigate to Settings > Calendar Feeds
2. Click "Generate Feed"
3. Expected: Feed URL appears within 2-3 seconds
4. URL format: webcal://timebreez.com/feeds/{token}
```

**Related:**
- **Invariant:** I-DEMO-003
- **Wave:** 32 (Fix #6)
- **Migration:** `supabase/migrations/104_fix_demo_integration_features.sql`

---

### Fix #7: Burnout Board Shows No Data

**Symptoms:**
- Navigate to Burnout Board
- Empty page or "No flagged employees"
- Demo org should have 2 flagged employees

**Cause:**
- Demo data not seeded for `burnout_flags` table

**Solution:**

**Step 1: Verify burnout flags exist**
```sql
SELECT * FROM burnout_flags WHERE organization_id = '00000000-0000-0000-0000-000000000001';
-- Expected: At least 2 rows
```

**Step 2: Re-seed demo data**
```sql
-- Insert demo burnout flags
INSERT INTO burnout_flags (id, organization_id, employee_id, severity, reason, flagged_at)
VALUES
  (gen_random_uuid(), '00000000-0000-0000-0000-000000000001', {employee_id_1}, 'high', 'Consecutive overtime shifts', NOW() - INTERVAL '2 days'),
  (gen_random_uuid(), '00000000-0000-0000-0000-000000000001', {employee_id_2}, 'medium', 'No time off in 60 days', NOW() - INTERVAL '5 days');
```

**Step 3: Verify fix**
```
1. Navigate to Burnout Board
2. Expected: 2 employee cards visible
3. Each card shows severity (high/medium) and reason
```

**Related:**
- **Invariant:** I-DEMO-002 (uses relative dates)
- **Wave:** 32 (Fix #7)
- **Migration:** `supabase/migrations/104_fix_demo_integration_features.sql`

---

### Fix #8: Vocabulary Shows Placeholders (Not "Room/Rooms")

**Symptoms:**
- Admin > Vocabulary shows "Zone/Zones" instead of "Room/Rooms"
- Placeholders like "{zone_singular}" appear

**Cause:**
- `get_vocabulary_defaults()` RPC returns wrong data type
- Migration 044 vs 045 conflict (TABLE vs JSON return type)

**Solution:**

**Step 1: Check RPC return type**
```sql
SELECT proname, prorettype::regtype FROM pg_proc WHERE proname = 'get_vocabulary_defaults';
-- Expected: json (NOT setof record)
```

**Step 2: Update RPC to return JSON (admin only)**
```sql
-- Drop old TABLE-based version
DROP FUNCTION IF EXISTS get_vocabulary_defaults();

-- Create JSON-based version
CREATE OR REPLACE FUNCTION get_vocabulary_defaults()
RETURNS JSON AS $$
BEGIN
  RETURN json_build_object(
    'zone_singular', 'Room',
    'zone_plural', 'Rooms',
    'employee_singular', 'Staff',
    'employee_plural', 'Staff'
  );
END;
$$ LANGUAGE plpgsql SECURITY DEFINER;
```

**Step 3: Update RPC that uses it**
```sql
-- Ensure RPCs use JSON access (->>'key') not column access (.column)
-- Example fix in migration 052:
v_vocab := get_vocabulary_defaults();
v_zone_singular := v_vocab->>'zone_singular'; -- JSON access
-- NOT: v_zone_singular := v_vocab.zone_singular; -- Column access (breaks)
```

**Step 4: Verify fix**
```
1. Navigate to Admin > Vocabulary
2. Expected:
   - Zone Singular: "Room"
   - Zone Plural: "Rooms"
   - Employee Singular: "Staff"
   - Employee Plural: "Staff"
```

**Related:**
- **Invariant:** I-DEMO-003
- **Wave:** 32 (Fix #8)
- **Migration:** `supabase/migrations/104_fix_demo_integration_features.sql`
- **Lesson:** Migration 044→045→052 function signature conflict

---

## 🌐 Browser & Connectivity Issues

### Issue: Page won't load / infinite loading spinner

**Symptoms:**
- Page shows loading spinner forever
- No content appears
- Network tab shows pending requests

**Cause:**
- Network connectivity issue
- Supabase outage
- CORS error
- Service worker cache issue

**Solution:**

**Step 1: Check network**
```
1. Open browser DevTools (F12)
2. Go to Network tab
3. Refresh page (F5)
4. Look for failed requests (red status codes)
5. Check error messages
```

**Step 2: Common fixes**
```
1. Clear browser cache (Ctrl+Shift+Delete)
2. Hard refresh (Ctrl+Shift+R)
3. Try incognito mode (Ctrl+Shift+N)
4. Try different browser (Chrome, Firefox, Safari)
5. Check internet connection
```

**Step 3: Check Supabase status**
```
1. Visit status.supabase.com
2. Verify no active incidents
3. If incident active, wait for resolution
```

**Step 4: Disable service worker (if PWA installed)**
```
1. F12 > Application tab
2. Service Workers section
3. Click "Unregister"
4. Refresh page
```

---

### Issue: "Failed to fetch" or CORS errors

**Symptoms:**
- Console shows "Failed to fetch" errors
- CORS policy errors
- Requests blocked

**Cause:**
- Browser extension blocking requests
- CORS misconfiguration
- Ad blocker interference

**Solution:**

**Step 1: Disable browser extensions**
```
1. Open Extensions (chrome://extensions or about:addons)
2. Disable all extensions
3. Refresh page
4. If works, re-enable one-by-one to find culprit
```

**Step 2: Check ad blockers**
```
1. Disable uBlock Origin, Adblock Plus, etc.
2. Refresh page
3. Whitelist timebreez.com if needed
```

**Step 3: Check CORS (admin only)**
```
1. Verify VITE_SUPABASE_URL matches actual Supabase project
2. Verify Supabase authentication settings allow your domain
```

---

## 🔐 Authentication & Permissions

### Issue: "Not authenticated" or "Session expired"

**Symptoms:**
- Redirect to login page
- "Please log in" message
- Unauthorized errors

**Cause:**
- Session expired (timeout)
- Auth token cleared
- Demo mode cache cleared

**Solution:**

**Step 1: Re-login**
```
1. Go to www.timebreez.com/login
2. Should auto-login in demo mode
3. If production, enter email/password
```

**Step 2: Check session storage**
```
1. F12 > Application > Local Storage
2. Look for key: sb-{project-id}-auth-token
3. If missing, session expired (normal after 1 hour)
```

**Step 3: Clear and re-authenticate**
```
1. Clear all site data (F12 > Application > Clear storage)
2. Refresh page
3. Re-login
```

---

### Issue: "Permission denied" or "RLS policy violation"

**Symptoms:**
- Error message "permission denied for table {table}"
- "Row level security policy violation"
- Cannot view/edit data

**Cause:**
- Missing RLS policy on table
- User not in correct organization
- User role insufficient

**Solution:**

**Step 1: Verify org context**
```
1. Check org name in header (should be "Sunshine Early Learning Centre" for demo)
2. Check your role (should be Manager or Admin)
```

**Step 2: Check RLS policies (admin only)**
```sql
-- List all policies for a table
SELECT * FROM pg_policies WHERE tablename = '{table_name}';

-- Common fix: Grant SELECT for org members
CREATE POLICY "Users can view {table} in their org"
  ON {table_name} FOR SELECT
  USING (
    organization_id IN (
      SELECT organization_id FROM employees WHERE user_id = auth.uid()
    )
  );
```

**Step 3: Report missing policies**
```
1. Note the table name from error message
2. Note the operation (SELECT, INSERT, UPDATE, DELETE)
3. Report as bug with table name and operation
```

---

## 💾 Data Issues

### Issue: Changes don't save / data reverts

**Symptoms:**
- Click Save, success toast appears
- Refresh page, changes are gone
- Data reverts to previous state

**Cause:**
- Demo mode (resets daily)
- Database transaction failed
- Trigger or constraint rejected change

**Solution:**

**Step 1: Verify demo vs production**
```
Demo mode:
- Org name: "Sunshine Early Learning Centre"
- URL: www.timebreez.com/login
- Data resets: Daily at midnight UTC
- Expected: Changes lost after reset

Production:
- Your org name
- URL: www.timebreez.com (signed in)
- Data persists: Permanent
```

**Step 2: Check browser console**
```
1. F12 > Console
2. Look for errors during save
3. Common errors:
   - Constraint violation (e.g., unique email)
   - Trigger failure (e.g., leave balance check)
   - Foreign key violation (e.g., invalid room_id)
```

**Step 3: Retry with valid data**
```
1. Fix validation errors
2. Ensure required fields filled
3. Ensure foreign keys valid (e.g., room exists)
4. Save again
```

---

### Issue: Duplicate entries or missing data

**Symptoms:**
- Same employee/room appears twice
- Data missing that should exist
- Counts don't match expectations

**Cause:**
- Race condition (multiple tabs open)
- Database constraint issue
- Data migration incomplete

**Solution:**

**Step 1: Close duplicate tabs**
```
1. Close all Timebreez tabs except one
2. Refresh remaining tab
3. Verify data appears correctly
```

**Step 2: Check database (admin only)**
```sql
-- Find duplicates
SELECT name, COUNT(*) FROM rooms
WHERE organization_id = '00000000-0000-0000-0000-000000000001'
GROUP BY name HAVING COUNT(*) > 1;

-- Delete duplicates (keep oldest)
DELETE FROM rooms WHERE id NOT IN (
  SELECT MIN(id) FROM rooms
  WHERE organization_id = '00000000-0000-0000-0000-000000000001'
  GROUP BY name
);
```

**Step 3: Re-run migrations**
```bash
# Reset demo data (admin only)
supabase db reset
```

---

## 🧪 Testing & Debugging

### How to Debug Like a Developer

**Step 1: Open Browser DevTools**
```
1. Press F12 (Windows/Linux) or Cmd+Opt+I (Mac)
2. Go to Console tab
3. Look for red errors
```

**Step 2: Check Network Tab**
```
1. F12 > Network tab
2. Refresh page (F5)
3. Look for:
   - Failed requests (red, status 400/403/500)
   - Slow requests (>2 seconds)
   - RPC calls (e.g., /rest/v1/rpc/get_room_snapshots)
```

**Step 3: Inspect Element**
```
1. Right-click any UI element
2. Click "Inspect" or "Inspect Element"
3. Check data-testid attribute
4. Verify element is visible (not display:none)
```

**Step 4: Check Database (admin only)**
```sql
-- View demo org data
SELECT * FROM organizations WHERE id = '00000000-0000-0000-0000-000000000001';

-- View demo rooms
SELECT * FROM rooms WHERE organization_id = '00000000-0000-0000-0000-000000000001';

-- View demo employees
SELECT * FROM employees WHERE organization_id = '00000000-0000-0000-0000-000000000001';
```

---

## 📞 When to Contact Support

### Contact support if:
- ✅ Issue persists after following all troubleshooting steps
- ✅ Critical issue (room understaffed, data lost)
- ✅ Security concern (unauthorized access)
- ✅ Billing issue
- ✅ Feature request

### DO NOT contact support for:
- ❌ How to use a feature (read the guides first)
- ❌ Demo mode data resetting (expected behavior)
- ❌ Browser extension conflicts (disable extensions)
- ❌ Slow internet (network issue, not Timebreez)

### What to include in support email:
1. **Subject:** Clear description (e.g., "Control Desk shows no rooms")
2. **Environment:** Demo mode or Production + org name
3. **Steps to reproduce:**
   ```
   1. Go to Control Desk
   2. Observe no rooms appear
   3. Check console, see RLS error
   ```
4. **Screenshot:** Attach screenshot of error
5. **Browser console:** Copy/paste errors from Console tab
6. **Expected vs Actual:**
   ```
   Expected: 7 room tiles visible
   Actual: "No rooms configured" error
   ```

---

## 📚 Related Guides
- [Demo Mode - Getting Started](./01-demo-mode-onboarding.md)
- [Control Desk Operations](./05-control-desk-operations.md)
- [Session Scheduling](./02-session-scheduling-ecce-aims.md)
- [Cover Staff Dispatch](./03-cover-staff-dispatch.md)
- [Daily Reconciliation](./04-daily-reconciliation.md)

## 📞 Support
- **Email:** support@timebreez.com
- **Demo mode:** www.timebreez.com/login
- **Status:** status.supabase.com
- **GitHub:** github.com/Hulupeep/timebreez/issues

# Staff CSV Import - Adding Your Team From a Spreadsheet

## Who This Is For
**Admins** setting up a new organisation, or adding a group of new starters at once, who would rather upload a spreadsheet than type each person in by hand.

## What You'll Learn
- When to use the CSV import instead of the Timetastic import
- Exactly which columns the file needs
- What counts as an error (stops the row) versus a warning (lets it through)
- What happens to people who are already in Timebreez
- How to find the page, which is currently not linked from the menu

## Prerequisites
- **Admin** role in Timebreez
- A CSV file of your staff
- Any rooms you want to assign people to should already exist

---

## Quick Start (TL;DR)

1. Go to **`/admin/import-staff`** (see [Finding the page](#finding-the-page) - it is not in the menu yet)
2. Upload your CSV
3. Timebreez validates it and shows **Issues** before importing anything
4. Fix any errors in your spreadsheet and re-upload
5. Import - existing people are **updated**, new people are **created**

---

## CSV Import or Timetastic Import?

Use the **right** one:

| Use the CSV import when | Use the [Timetastic import](./20-timetastic-import.md) when |
|---|---|
| You just need people in the system | You are migrating from Timetastic |
| You have a spreadsheet of staff | You have a Timetastic export |
| You do not need leave history | You need leave history and opening balances |
| Adding a batch of new starters | Doing a one-off organisation cutover |

The CSV import creates **people only**. It does not bring across any leave history or balances.

---

## Finding the Page

The staff CSV import lives at **`/admin/import-staff`**.

> **Note:** this page is not currently linked from the Employees page or the navigation menu. You need to type the address in directly. This is a known gap and is being tracked.

You will see **Import Staff**, with the subtitle *"Upload a CSV file to bulk import employees"*, and an **Import History** list of what you have uploaded before.

---

## The Columns

| Column | Required? | Notes |
|---|---|---|
| `full_name` | **Required** | Cannot be blank |
| `email` | **Required** | Must be a valid email address, and unique within the file |
| `role` | Optional | Must be `admin`, `manager` or `employee` |
| `payroll_id` | Optional | Your payroll reference for this person |
| `phone` | Optional | Should be international format, e.g. `+353871234567` |
| `start_date` | Optional | When they started |
| `default_room` | Optional | Must match the name of a room that already exists |
| `contract_hours` | Optional | Contracted hours per week |

### Example

```csv
full_name,email,role,payroll_id,phone,start_date,default_room,contract_hours
Emma Byrne,emma.byrne@example.ie,employee,PAY-001,+353871234567,2026-01-15,Baby Room,39
Sean Murphy,sean.murphy@example.ie,manager,PAY-002,+353871234568,2025-09-01,Toddlers,39
Aoife Kelly,aoife.kelly@example.ie,employee,PAY-003,,2026-02-01,Preschool,25
```

---

## Errors and Warnings

Timebreez checks the whole file **before** importing anything, and shows the results under **Issues**.

### Errors - the row will not import

| Message | What to do |
|---|---|
| *Full name is required* | Fill in the name |
| *Email is required* | Fill in the email |
| *Invalid email format* | Fix the address |
| *Duplicate email in CSV* | The same email appears twice in your file - remove one |
| *Invalid role. Must be admin, manager, or employee* | Correct the role, or leave it blank |

### Warnings - the row still imports

| Message | What it means |
|---|---|
| *Employee exists - will be updated* | This email is already in Timebreez. Their record will be **updated**, not duplicated. |
| *Phone should be E.164 format (+353...)* | The number will import, but may not work for WhatsApp notifications until corrected. |

> **Errors block a row. Warnings do not.** Read the warnings before importing - "Employee exists - will be updated" in particular means you are about to change existing records.

---

## What Happens to People Already in Timebreez

Matching is by **email address**.

- **Email not found** - a new employee is created
- **Email already exists** - that employee is **updated** with the values in your file

This makes the import safe to re-run: uploading a corrected file updates the same people rather than creating duplicates. It also means a typo in an email address creates a *second* person rather than updating the first, so check your emails carefully.

---

## Rooms

If you fill in `default_room`, the name must match an existing room **exactly**. If Timebreez cannot find a room with that name, you will be told - it will not create the room for you.

Set your rooms up first, then import. See [Room settings](./admin/roster.md).

---

## Common Questions

**Can I re-upload a corrected file?**
Yes. People are matched by email, so existing records are updated rather than duplicated.

**Will this give everyone leave balances?**
No. The CSV import creates people only. For balances and history, use the [Timetastic import](./20-timetastic-import.md), or set allowances on each employee.

**Can I use it to change roles in bulk?**
Yes - include `email` and `role`, and existing people will be updated.

**What if one row is broken?**
Only that row is held back. Fix it and re-upload; the people who already imported will simply be updated.

**Why isn't it in the menu?**
A known gap. Use `/admin/import-staff` directly for now.

---

## Related

- [Timetastic Import](./20-timetastic-import.md) - full migration with leave history and balances
- [Managing employees](./admin/index.md)
- [Troubleshooting](./08-troubleshooting.md)

# Child-side grooming ledger

Read first each night. Body of truth for specs is GitHub; this file tracks grooming state and artifacts.

## Artifacts
- Pitch deck (Slides, private until Colm shares): https://claude.ai/artifact/VxYydcbQJaxs4hoBt6PPGD (rev 2, 26 Nov 2026, 14 slides)
- Mockup: Toddlers check-in tablet (#1455, #1461): https://claude.ai/artifact/Gf2ekv1LwxHTpc216WPj19
- Mockup: Ratio proof report (#1471, #1502): https://claude.ai/artifact/3dWemvAYRM8YDEpwuF7VWB
- Mockup: Pickup collector check (#1457): https://claude.ai/artifact/7wCVAAWt2Sq64y6vwfdmkq
- Mockup: Country rules + Why this number (#1508, #1509, #1511): https://claude.ai/artifact/2Ymu3A6nNVJazgtAmWy4UQ
- Mockup: Child absences, staff + parent (#1458): https://claude.ai/artifact/8yZ2xWu8hzCPwkr1hNTjqq
- Mockup: Emergency roll call + drill record (#1464, #1577): https://claude.ai/artifact/3RFSn75y9a6ZwyzBtd5cs9
- Mockup: Morning room balance (#1469, #1600): https://claude.ai/artifact/383wzXDGzHno5tqLdA8oGr
- Mockup: Room tablet devices + quick PIN (#1504, #1579): https://claude.ai/artifact/2wYQgngUYeSBQ8BFmowo5z
- Mockup: Childcare module + inspector links (#1507, #1582): https://claude.ai/artifact/2czJ3dXgben2nzH8EbnvGD
- Mockup: Allergen badges + kitchen view (#1587, #1588): https://claude.ai/artifact/4XjvvcTGQTgBw3j9YXHDMT
- Mockup: Medication administration record (#1590): https://claude.ai/artifact/D6tvstcbqtSDXzxur2KeR6
- Mockup: Toddlers room tablet, my room now + step-out (#1594, #1595): https://claude.ai/artifact/6twbYHGmAPPAijbv7xuEBm
- Living docs: CHILD-REG #1496, CHILD-REG funding #1497, CHILD-REG part 3 #1601, CHILD-ARCH #1498, CHILD-ARCH part 2 #1499, CHILD-ARCH part 3 #1602

## Night log
- 2026-11-26 (night 2): 10 agents. 47 IE rules sourced (now 163 IE), incl. school-age 1:12 (S.I. 575/2018), Tusla medication guidance (two-person check, parent signs on collection), sleep. 31 stories spec:contracted (#1458 #1459 #1462 #1463 #1464 #1503 #1577 #1504 #1507 #1510 #1512 #1579 #1580 #1582 #1583-#1590 #1592 #1593 #1594 #1596-#1600 #1469). 24 new issues (#1577-#1602). 8 mockups. Deck rev 2. Living docs split: #1601, #1602. Still thin: #1470 #1578 #1581 #1591 #1595. Next nights: #1451 (funding stories CHILD-FUND-001..009 from #1497 netting rules), #1450 (care log, incidents: LOG-001..007; rules now in #1601 INC), #1453 (parent comms, CHILD-PAR-010 first), #1466, #1468; also CHILD-ENR-001 enrolments (D-39), CHILD-GDPR rights rules for #1581.
- 2026-11-25 (night 1): 10 agents. 116 IE rules sourced (60 care + 56 funding), GB-ENG sketch. 15 stories spec:contracted, 14 new issues, 4 mockups, deck rev 1. Next epics in order: #1449 (no stories yet), #1452, #1451 (stories from netting rules), #1450, #1453, #1466, #1468; also finish #1448 (#1458 #1459 #1462 #1463 #1464 #1469 #1470 #1472-1474 still thin).

## Issues
| Issue | Title | Label | Last groomed | Mockup | Open questions |
|---|---|---|---|---|---|
| #1448 | EPIC: Child-side A: Staff-confirmed offline child check-in/out + Hive-grade roll book (Pha | spec:thin | 2026-11-26 | - | - |
| #1449 | EPIC: Child-side B: Child profile, dietary needs, allergens and medication | spec:thin | 2026-11-26 | - | - |
| #1450 | EPIC: Child-side C: Teacher notes, daily care log and incidents | spec:thin | - | - | - |
| #1451 | EPIC: Child-side D: ECCE/NCS funding, Hive week worklist and family invoicing | spec:thin | - | - | - |
| #1452 | EPIC: Child-side E: Teacher tools (room tablet: my room now, step-out guard, handover, hea | spec:thin | 2026-11-26 | - | - |
| #1453 | EPIC: Child-side F: Parent communications (portal, messages with read receipts, absences,  | spec:thin | - | - | - |
| #1454 | EPIC: Child-side G: Country policy layer (child policy packs: IE first; GB-ENG, US-state a | spec:thin | 2026-11-26 | - | - |
| #1455 | CHILD-ATT-001: Staff-confirmed child check-in/out that parents can start (pack-driven; IE  | spec:contracted | 2026-11-25 | https://claude.ai/artifact/Gf2ekv1LwxHTpc216WPj19 | build after #1504 online path |
| #1456 | CHILD-ATT-002: Offline kiosk/tablet: queue signed check-in events and sync later | spec:contracted | 2026-11-25 | - | build after #1504 online path |
| #1457 | CHILD-ATT-003: Collector checks at pickup: photos, authorised list, one-time codes | spec:contracted | 2026-11-25 | https://claude.ai/artifact/7wCVAAWt2Sq64y6vwfdmkq | - |
| #1458 | CHILD-ATT-004: Child absences: staff-marked, parent-reported (portal) and auto no-show, wi | spec:contracted | 2026-11-26 | https://claude.ai/artifact/8yZ2xWu8hzCPwkr1hNTjqq | - |
| #1459 | CHILD-ATT-005: Room moves, outings and school runs as attendance segments | spec:contracted | 2026-11-26 | - | - |
| #1460 | CHILD-ATT-006: Weekly attendance register (roll book) export: times, recorder, absences | spec:contracted | 2026-11-25 | - | - |
| #1461 | CHILD-ATT-007: Live ratio feed from staff-confirmed child attendance and real staff presen | spec:contracted | 2026-11-25 | https://claude.ai/artifact/Gf2ekv1LwxHTpc216WPj19 | - |
| #1462 | CHILD-ATT-008: Late pickup escalation in guardian contact order, with the staffing consequ | spec:contracted | 2026-11-26 | - | - |
| #1463 | CHILD-ATT-009: Visitor log: approved entry, pack-driven register fields and logged 1-year  | spec:contracted | 2026-11-26 | - | - |
| #1464 | CHILD-ATT-010: Emergency roll call: one tap, offline list of everyone on site, accounted-f | spec:contracted | 2026-11-26 | https://claude.ai/artifact/3RFSn75y9a6ZwyzBtd5cs9 | - |
| #1466 | EPIC: Child-side H: Hermes chief-of-staff agent for crèche admins (optional, MCP-connected | spec:thin | - | - | - |
| #1468 | EPIC: Multi-location and multi-organisation tenancy (shared staff, site isolation, group r | spec:thin | - | - | - |
| #1469 | CHILD-TT-006a: Morning room balance: suggested child moves, merges, splits and staff moves | spec:contracted | 2026-11-26 | https://claude.ai/artifact/383wzXDGzHno5tqLdA8oGr | - |
| #1470 | CHILD-TT-007: Staff tap into a room with their Paxton fob on the room tablet | spec:thin | 2026-11-26 | - | Q-A2 (D-09); Paxton fob Web NFC hardware test |
| #1471 | CHILD-ATT-011: Ratio proof report for any room and time window | spec:contracted | 2026-11-25 | https://claude.ai/artifact/3dWemvAYRM8YDEpwuF7VWB | - |
| #1472 | CHILD-MIG-001: Import children from TeachKloud and cut over safely | spec:thin | - | - | - |
| #1473 | CHILD-P0: TeachKloud exit test with Sandra (discovery, no code) | spec:thin | - | - | - |
| #1474 | CHILD-LOG-006: Safety checklists and policy acknowledgement | spec:thin | 2026-11-26 | - | - |
| #1500 | CHILD-ATT-000: Append-only `child_attendance_events`, legacy `child_attendance` backfill a | spec:contracted | 2026-11-25 | - | - |
| #1501 | CHILD-ATT-002b: Manager review queue for held attendance events (clock drift, conflicts, g | spec:contracted | 2026-11-25 | - | - |
| #1502 | CHILD-ATT-007b: Persisted 15-minute ratio slots and the room ratio timeline (with revision | spec:contracted | 2026-11-25 | https://claude.ai/artifact/3dWemvAYRM8YDEpwuF7VWB | - |
| #1503 | CHILD-ATT-011b: Staff roster record export per area per day (QRF3 Reg 11 CR3; S.I. 221/201 | spec:contracted | 2026-11-26 | - | - |
| #1504 | CHILD-SEC-002: Enrolled, revocable room tablets and kiosks (device keys, device API, quick | spec:contracted | 2026-11-26 | https://claude.ai/artifact/2wYQgngUYeSBQ8BFmowo5z | - |
| #1505 | CHILD-GDPR-001: Consent register, lawful basis per data class and processor register (pare | spec:contracted | 2026-11-25 | - | - |
| #1506 | CHILD-GDPR-002: Retention classes from the pack, a single logged purge, and "left" status  | spec:contracted | 2026-11-25 | - | - |
| #1507 | CHILD-MOD-001: Childcare module on/off switch per org, and child staff roles | spec:contracted | 2026-11-26 | https://claude.ai/artifact/2czJ3dXgben2nzH8EbnvGD | - |
| #1508 | CHILD-POL-001: Child policy packs, selection and org overrides | spec:contracted | 2026-11-25 | https://claude.ai/artifact/2Ymu3A6nNVJazgtAmWy4UQ | - |
| #1509 | CHILD-POL-002: IE child policy pack v1.0.0 (care, records, safety, data protection rules) | spec:contracted | 2026-11-25 | https://claude.ai/artifact/2Ymu3A6nNVJazgtAmWy4UQ | - |
| #1510 | CHILD-POL-002b: IE child policy pack 1.1.0 funding content (ECCE, NCS, Core Funding, AIM) | spec:contracted | 2026-11-26 | - | - |
| #1511 | CHILD-POL-003: "Why this number" trace for every pack-driven output (decision records + sh | spec:contracted | 2026-11-25 | https://claude.ai/artifact/2Ymu3A6nNVJazgtAmWy4UQ | - |
| #1512 | CHILD-POL-004: GB-ENG skeleton child pack as a schema test (proves a new country needs no  | spec:contracted | 2026-11-26 | - | - |
| #1513 | CHILD-SEC-001: No-anon contract and per-table RLS test harness for child data | spec:contracted | 2026-11-25 | - | - |
| #1577 | CHILD-SAFE-001: Fire drill and fire equipment records (pack-driven; IE S.I. 221/2016 Reg 2 | spec:contracted | 2026-11-26 | https://claude.ai/artifact/3RFSn75y9a6ZwyzBtd5cs9 | - |
| #1578 | CHILD-ATT-004b: Absences from parent chat messages, and the no-show prompt to the guardian | spec:thin | 2026-11-26 | - | Q-P3: chat absence on staff tap or portal tap (Sandra); CHILD-PAR-010 not filed |
| #1579 | CHILD-SEC-002b: Offline quick-PIN check on enrolled devices (device-bound same-day verifie | spec:contracted | 2026-11-26 | https://claude.ai/artifact/2wYQgngUYeSBQ8BFmowo5z | - |
| #1580 | CHILD-GDPR-003: DPIA template and controller pack, pre-filled from live data | spec:contracted | 2026-11-26 | - | - |
| #1581 | CHILD-GDPR-004: Data subject requests for child records (access with welfare withhold, era | spec:thin | 2026-11-26 | - | no CHILD-REG ids for GDPR subject rights |
| #1582 | CHILD-SEC-005: Inspector time-boxed read-only links to the pack's inspection exports | spec:contracted | 2026-11-26 | https://claude.ai/artifact/2czJ3dXgben2nzH8EbnvGD | - |
| #1583 | CHILD-DIET-001a: Art 9 health tables, H0/H1/H2 read tiers and locked legacy medical_notes  | spec:contracted | 2026-11-26 | - | - |
| #1584 | CHILD-DIET-001b: Structured allergens from the pack taxonomy, portal change requests and s | spec:contracted | 2026-11-26 | - | - |
| #1585 | CHILD-PROF-001: Child record core: GP, immunisations, conditions, emergency contacts, emer | spec:contracted | 2026-11-26 | - | - |
| #1586 | CHILD-DIET-002: Dietary requirements, effective-dated (codes for the kitchen, detail for t | spec:contracted | 2026-11-26 | - | - |
| #1587 | CHILD-DIET-003: Allergen badges everywhere, including cover staff the moment they are rost | spec:contracted | 2026-11-26 | https://claude.ai/artifact/4XjvvcTGQTgBw3j9YXHDMT | - |
| #1588 | CHILD-DIET-004: Kitchen view: menu x children present x conflicts, per-dish allergen decla | spec:contracted | 2026-11-26 | https://claude.ai/artifact/4XjvvcTGQTgBw3j9YXHDMT | - |
| #1589 | CHILD-DIET-005a: Medication consent per medicine (portal only), medicine receipt check and | spec:contracted | 2026-11-26 | - | - |
| #1590 | CHILD-DIET-005b: Medication administration record with pack-driven two-person check and pa | spec:contracted | 2026-11-26 | https://claude.ai/artifact/D6tvstcbqtSDXzxur2KeR6 | - |
| #1591 | CHILD-DIET-005c: Emergency administration, offline medication recording and school-age sel | spec:thin | 2026-11-26 | - | Q-H3 emergency administration basis, Q-H4 offline medication recording |
| #1592 | CHILD-DIET-006: Child record completeness check from the pack's required fields | spec:contracted | 2026-11-26 | - | - |
| #1593 | CHILD-STAFF-001: Ratio-countable staff facts: category, qualification, first aid, person-i | spec:contracted | 2026-11-26 | - | - |
| #1594 | CHILD-TT-001: "My room now" on the room tablet: children in/expected/absent, staff in the  | spec:contracted | 2026-11-26 | https://claude.ai/artifact/6twbYHGmAPPAijbv7xuEBm | - |
| #1595 | CHILD-TT-002: Step-out and break guard on the room tablet: ratio effect, pack checks, cove | spec:thin | 2026-11-26 | https://claude.ai/artifact/6twbYHGmAPPAijbv7xuEBm | Q-A2: Colm to confirm D-09 (where room taps are written) |
| #1596 | CHILD-TT-003: Room handover checklist and end-of-day room close (everyone accounted for) | spec:contracted | 2026-11-26 | - | - |
| #1597 | CHILD-TT-004: Scheduled room headcount checks with drift alerts and recorded missed checks | spec:contracted | 2026-11-26 | - | - |
| #1598 | CHILD-TT-005a: Shared room tablet operator mode: staff PIN/fob unlock, switch, auto-lock,  | spec:contracted | 2026-11-26 | - | - |
| #1599 | CHILD-TT-005b: Minimal encrypted room tablet caches and wipe evidence (incl. the emergency | spec:contracted | 2026-11-26 | - | - |
| #1600 | CHILD-TT-006b: Room balance cost effect and morning notice to the person in charge | spec:contracted | 2026-11-26 | https://claude.ai/artifact/383wzXDGzHno5tqLdA8oGr | - |
| #1601 | CHILD-REG (part 3): IE allergens, medication, incidents, sleep and school-age rules (night | doc | 2026-11-26 | - | - |
| #1602 | CHILD-ARCH (part 3): health data, room tablet tools, devices and night-2 decisions | doc | 2026-11-26 | - | - |

## Cross-night open questions
- Pam's day-to-day role (not on record; ask Colm).
- Named competent reviewer for IE rule content (care, and separately funding) (Q-R2).
- Attendance retention: 2 years after leaving (care) vs 6 years (funding) (Q-R1).
- Who does the Hive return and payroll at SSST day to day (Mella per memory, #1447 says Sandra's Hive week).
- Q-A2: Colm to confirm D-09 (staff room taps written to staff_room_presence_events). Blocks #1595, #1470.
- Q-P1: who owns the DPIA / is DPO at Timebreez and at each centre (blocks DPIA sign-off #1580 and any pilot with real children, not the build).
- Q-H1: does a portal typed-name signature meet "signed parental consent" (MED-001, MED-007)? Named reviewer.

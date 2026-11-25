# Child-side grooming ledger

Read first each night. Body of truth for specs is GitHub; this file tracks grooming state and artifacts.

## Artifacts
- Pitch deck (Slides, private until Colm shares): https://claude.ai/artifact/VxYydcbQJaxs4hoBt6PPGD (rev 1, 25 Nov 2026, 12 slides)
- Mockup: Toddlers check-in tablet (#1455, #1461): https://claude.ai/artifact/Gf2ekv1LwxHTpc216WPj19
- Mockup: Ratio proof report (#1471, #1502): https://claude.ai/artifact/3dWemvAYRM8YDEpwuF7VWB
- Mockup: Pickup collector check (#1457): https://claude.ai/artifact/7wCVAAWt2Sq64y6vwfdmkq
- Mockup: Country rules + Why this number (#1508, #1509, #1511): https://claude.ai/artifact/2Ymu3A6nNVJazgtAmWy4UQ
- Living docs: CHILD-REG #1496, CHILD-REG funding #1497, CHILD-ARCH #1498, CHILD-ARCH part 2 #1499

## Night log
- 2026-11-25 (night 1): 10 agents. 116 IE rules sourced (60 care + 56 funding), GB-ENG sketch. 15 stories spec:contracted, 14 new issues, 4 mockups, deck rev 1. Next epics in order: #1449 (no stories yet), #1452, #1451 (stories from netting rules), #1450, #1453, #1466, #1468; also finish #1448 (#1458 #1459 #1462 #1463 #1464 #1469 #1470 #1472-1474 still thin).

## Issues
| Issue | Title | Label | Last groomed | Mockup | Open questions |
|---|---|---|---|---|---|
| #1454 | EPIC: Child-side G: Country policy layer (child policy packs: IE first; GB-ENG, US-state a | spec:thin | 2026-11-25 | - | - |
| #1448 | EPIC: Child-side A: Staff-confirmed offline child check-in/out + Hive-grade roll book (Pha | spec:thin | 2026-11-25 | - | - |
| #1455 | CHILD-ATT-001: Staff-confirmed child check-in/out that parents can start (pack-driven; IE  | spec:contracted | 2026-11-25 | https://claude.ai/artifact/Gf2ekv1LwxHTpc216WPj19 | build after #1504 online path |
| #1456 | CHILD-ATT-002: Offline kiosk/tablet: queue signed check-in events and sync later | spec:contracted | 2026-11-25 | - | build after #1504 online path |
| #1457 | CHILD-ATT-003: Collector checks at pickup: photos, authorised list, one-time codes | spec:contracted | 2026-11-25 | https://claude.ai/artifact/7wCVAAWt2Sq64y6vwfdmkq | - |
| #1458 | CHILD-ATT-004: Child absences: parent-reported, staff-marked and auto no-show, with reason | spec:thin | - | - | - |
| #1459 | CHILD-ATT-005: Room moves, outings and school runs as attendance segments | spec:thin | - | - | - |
| #1460 | CHILD-ATT-006: Weekly attendance register (roll book) export: times, recorder, absences | spec:contracted | 2026-11-25 | - | - |
| #1461 | CHILD-ATT-007: Live ratio feed from staff-confirmed child attendance and real staff presen | spec:contracted | 2026-11-25 | https://claude.ai/artifact/Gf2ekv1LwxHTpc216WPj19 | - |
| #1462 | CHILD-ATT-008: Late pickup escalation using guardian contact order | spec:thin | - | - | - |
| #1463 | CHILD-ATT-009: Visitor log (Tusla Reg 24(3)), approved entry and 1-year retention | spec:thin | - | - | - |
| #1464 | CHILD-ATT-010: Emergency roll call: offline list of everyone on site + drill record | spec:thin | - | - | - |
| #1466 | EPIC: Child-side H: Hermes chief-of-staff agent for crèche admins (optional, MCP-connected | spec:thin | - | - | - |
| #1468 | EPIC: Multi-location and multi-organisation tenancy (shared staff, site isolation, group r | spec:thin | - | - | - |
| #1469 | CHILD-TT-006: Morning room balance: suggested child moves, merges and splits | spec:thin | - | - | - |
| #1470 | CHILD-TT-007: Staff tap into a room with their Paxton fob on the room tablet | spec:thin | - | - | - |
| #1471 | CHILD-ATT-011: Ratio proof report for any room and time window | spec:contracted | 2026-11-25 | https://claude.ai/artifact/3dWemvAYRM8YDEpwuF7VWB | - |
| #1472 | CHILD-MIG-001: Import children from TeachKloud and cut over safely | spec:thin | - | - | - |
| #1473 | CHILD-P0: TeachKloud exit test with Sandra (discovery, no code) | spec:thin | - | - | - |
| #1474 | CHILD-LOG-006: Safety checklists and policy acknowledgement | spec:thin | - | - | - |
| #1500 | CHILD-ATT-000: Append-only `child_attendance_events`, legacy `child_attendance` backfill a | spec:contracted | 2026-11-25 | - | - |
| #1501 | CHILD-ATT-002b: Manager review queue for held attendance events (clock drift, conflicts, g | spec:contracted | 2026-11-25 | - | - |
| #1502 | CHILD-ATT-007b: Persisted 15-minute ratio slots and the room ratio timeline (with revision | spec:contracted | 2026-11-25 | https://claude.ai/artifact/3dWemvAYRM8YDEpwuF7VWB | - |
| #1503 | CHILD-ATT-011b: Staff roster record export per area per day (QRF3 Reg 11 CR3; S.I. 221/201 | spec:thin | 2026-11-25 | - | QRF3 CR3 column mapping needs a named reviewer (Q-R2) |
| #1504 | CHILD-SEC-002: Enrolled, revocable room tablets and kiosks (device keys, device API, quick | spec:thin | 2026-11-25 | - | offline PIN check design (Q-S1) |
| #1505 | CHILD-GDPR-001: Consent register, lawful basis per data class and processor register (pare | spec:contracted | 2026-11-25 | - | - |
| #1506 | CHILD-GDPR-002: Retention classes from the pack, a single logged purge, and "left" status  | spec:contracted | 2026-11-25 | - | - |
| #1507 | CHILD-MOD-001: Childcare module on/off switch per org, and child staff roles | spec:thin | 2026-11-25 | - | org_type vs business_type canonical; where hotels sit |
| #1508 | CHILD-POL-001: Child policy packs, selection and org overrides | spec:contracted | 2026-11-25 | https://claude.ai/artifact/2Ymu3A6nNVJazgtAmWy4UQ | - |
| #1509 | CHILD-POL-002: IE child policy pack v1.0.0 (care, records, safety, data protection rules) | spec:contracted | 2026-11-25 | https://claude.ai/artifact/2Ymu3A6nNVJazgtAmWy4UQ | - |
| #1510 | CHILD-POL-002b: IE child policy pack 1.1.0 funding content (ECCE, NCS, Core Funding, AIM) | spec:thin | 2026-11-25 | - | scheme key names (ncs vs ncsUniversal/ncsIncome); NCS weekly return deadline unsourced |
| #1511 | CHILD-POL-003: "Why this number" trace for every pack-driven output (decision records + sh | spec:contracted | 2026-11-25 | https://claude.ai/artifact/2Ymu3A6nNVJazgtAmWy4UQ | - |
| #1512 | CHILD-POL-004: GB-ENG skeleton child pack as a schema test (proves a new country needs no  | spec:thin | 2026-11-25 | - | GB-ENG CHILD-REG ids not assigned |
| #1513 | CHILD-SEC-001: No-anon contract and per-table RLS test harness for child data | spec:contracted | 2026-11-25 | - | - |

## Cross-night open questions
- Pam's day-to-day role (not on record; ask Colm).
- Named competent reviewer for IE rule content (care, and separately funding) (Q-R2).
- Attendance retention: 2 years after leaving (care) vs 6 years (funding) (Q-R1).
- Who does the Hive return and payroll at SSST day to day (Mella per memory, #1447 says Sandra's Hive week).

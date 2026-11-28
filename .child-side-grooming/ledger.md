# Child-side grooming ledger

Read first each night. Body of truth for specs is GitHub; this file tracks grooming state and artifacts.

## Standing rules for the nightly run (read before writing anything)
- **PLAIN WORDS (Colm, 27 Nov 2026):** every question, decision or blocker put to Colm (summary, open questions in issues, this ledger) is explained in plain words with 1-3 short scenarios: an invented staff member or child, a time, a room, what happens if he says yes, what happens if he says no. Then the recommendation. Ids go after the explanation, in brackets, never instead of it.
- **Living docs are split** (65k body limit); later parts win: CHILD-REG #1496, #1497, **#1601**, **#1668**; CHILD-REG part 5 **#1761**; CHILD-ARCH #1498, #1499, **#1602**, **#1669**, **#1762** (decisions up to D-122; #1762 body is FULL, next decisions go in a part 6; next free decision id D-123; next free FUND id FUND-078). Start a new part when a body nears 60k.
- **Existing ADRs come first (27 Nov 2026):** before writing any D-row, the architect reads every docs/architecture/**/ADR-*.md on main (leave ADR-001..015, platform ADR-016..020: org isolation, thin channels, rule packs not code, migration numbers, closed periods). Each D-row names the ADR it applies or extends; a D-row that conflicts with an ADR is flagged, never silently decided. Nights 1-2 cited only ADR-003; night 3 began citing ADR-006..020. Back-check D-01..D-39 vs ADR-016..020 DONE night 4 (#1762 §Z, BC-01..BC-17). ADR candidates 027 (group aggregates), 028 (Hermes thin client), 029 (retention purge vs LEDGER-003), 030 (family money ledger): not yet written.
- **D-09 confirmed by Colm, 27 Nov 2026:** staff room taps, step-outs and breaks are their own workforce record, separate from Paxton clock-ins.

## Artifacts
- Pitch deck (Slides, private until Colm shares): https://claude.ai/artifact/VxYydcbQJaxs4hoBt6PPGD (rev 4, 28 Nov 2026, 14 slides; not yet checked by eye for text overflow on payments, parents, ask slides)
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
- Mockup: Monday funder return (#1673): https://claude.ai/artifact/NtnD5Nh5mRAnmgEgLutLKY
- Mockup: Billing preview, netted lines (#1677): https://claude.ai/artifact/GYQccBfVV4eS2K7vBEdxee
- Mockup: Wobblers care log (#1680): https://claude.ai/artifact/XCjP5XC314tKi2CdiLaGfD
- Mockup: Toddlers incident record (#1681, #1682): https://claude.ai/artifact/APSnMwcygu5TSJHJiHxswu
- Mockup: Parent portal (#1686): https://claude.ai/artifact/YTg1yAeTvNG9hoCVqZEjGu
- Mockup: Family messages, read receipts (#1690): https://claude.ai/artifact/5Tia2pq339ut6jknSkPUFp
- Mockup: Extra session request (#1693): https://claude.ai/artifact/Ph2yhZaAQ6NbqVxBvuojGp
- Mockup: Murphy Payer Account (#1770): https://claude.ai/artifact/RiN8pKnzkW6sNMbgWuouL9
- Mockup: Riverside Bank Reconcile (#1773): https://claude.ai/artifact/VsxzTMbEmdk3FEBoWJPcbK
- Mockup: Family Statements (#1774): https://claude.ai/artifact/8fYzqKcNXzwkFqgnu9Pfcf
- Mockup: Aged Debt Reminders (#1775): https://claude.ai/artifact/U8ULDvWsFmhPiiRK3E3NBX
- Mockup: Per-Service Funding (#1776): https://claude.ai/artifact/KyU4vpmDGxBa5nxAkEMizx
- Mockup: November Invoice Run (#1678): https://claude.ai/artifact/U3aGrsZLo6uPWtECE9aesJ
- Mockup: Seán's Day Delivery (#1763): https://claude.ai/artifact/RLRueqreEUvY5haTgw1UqQ
- Mockup: Toddlers Room Photos (#1764): https://claude.ai/artifact/Qth8JXHC1Mi8evriWJcLqw
- Mockup: Kelly Family Billing (#1765): https://claude.ai/artifact/UhfddTNL1d4MzwCCCTBC4t
- Mockup: Rose's Week Sign-off (#1767): https://claude.ai/artifact/8YLciJjZinhANWT98tXN8q
- Mockup: Little Acorns Complaints (#1768): https://claude.ai/artifact/FfUfStHiFKyMHcCFaRBNAP
- Mockup: Complaints Review Q4 (#1769): https://claude.ai/artifact/WA6bE6Q2HbqoBHQqB9yfUm
- Mockup: Hermes Switch-on (#1777): https://claude.ai/artifact/M4WDTsNhBVCYwXjeGRDEkQ
- Mockup: Hermes Morning Brief (#1778): https://claude.ai/artifact/QKxqGPXrt6FCejj1Ecgiez
- Mockup: Hermes Approvals Inbox (#1779): https://claude.ai/artifact/Wf28G4rqAAzaBozkJM3BwG
- Mockup: Riverside Services Settings (#1780): https://claude.ai/artifact/CMSLBA2kdF9RT4fNGNFEEz
- Mockup: Shared Staff Counting (#1781): https://claude.ai/artifact/TzAXmz53JSGyotRkvgykMz
- Mockup: Riverside Child Import (#1472): https://claude.ai/artifact/MNYFRFbDwyJ7zzb7vYEPnK
- Mockup: Riverside Cut-over Day (#1783): https://claude.ai/artifact/B8KHKjLAWDLJAPZiKqakbh
- Living docs: CHILD-REG #1496, CHILD-REG funding #1497, CHILD-REG part 3 #1601, CHILD-ARCH #1498, CHILD-ARCH part 2 #1499, CHILD-ARCH part 3 #1602, CHILD-REG part 4 #1668, CHILD-ARCH part 4 #1669, CHILD-REG part 5 #1761, CHILD-ARCH part 5 #1762

## Night log
- 2026-11-28 (night 4): 10 agents. 66 rules sourced in #1761 (FUND-066..077, PAY-001..007, CONS-001..007, TAX-001..002, PAR-012..018, SVC-001..008, STAFF-009..012, GDPR-022..028, AI-001..005, MIG-001..002, US-CA-ATT-001, 4 GB-ENG sketch rows). Decisions D-87..D-122 in #1762 + back-check BC-01..17; security SEC-01..05 fixed 5 unsafe D-rows (amendment block in #1762). 19 stories spec:contracted: #1770 #1773 #1774 #1775 #1776 #1678 (payments), #1763 #1764 #1765 #1767 #1768 #1769 (parent comms), #1777 #1778 #1779 (Hermes), #1780 #1781 (multi-site), #1472 #1783 (TeachKloud import). Thin: #1766 #1771 #1772 (Q-B1 merchant account), #1782 (ADR-027 + same company or two). 21 new issues (#1761-#1783). 19 mockups. Deck rev 4. Next nights: write ADR-027..030 as docs; #1591; #1672 (Hive sample); #1474; light re-check of ECCE 2026/27 agreement copy (E27 cites one #1497 says missing); NCS 2026 thresholds confirm on ncs.gov.ie (FUND-071).
- 2026-11-27 (night 3): 10 agents. 52 rules sourced in #1668 (FUND-057..065, GDPR-006..021, PAR-001..011, LOG-001..005, SAFEG-001..006, GB-ENG sketch); decisions D-40..D-86 in #1669. 25 stories spec:contracted: funding #1670 #1671 #1673 #1674 #1675 #1676 #1677 #1679; care log #1680-#1685; parent comms #1686-#1693 #1694, plus #1578 and #1581 re-groomed. 27 new issues (#1668-#1694) + security #1697 (staff whatsapp-webhook fails open without secret, static reading). 7 mockups. Deck rev 3 (parent comms slide, edge join table; step-out slide removed). Still thin: #1672 (Q-F2 Hive sample), #1678 (Q-B5 VAT), #1474 (Timebreez vs Hubduck). Epic bodies #1447 #1448 #1450 #1451 #1453 #1454 updated; #1450 headline corrected per D-55. Next nights: CHILD-FUND-006 payments (Q-B1) + FUND-009, CHILD-PAR-004..006 and PAR-012 complaints, #1466, #1468, #1449 leftovers (#1591), #1595/#1470 once D-09 is answered.
- 2026-11-26 (night 2): 10 agents. 47 IE rules sourced (now 163 IE), incl. school-age 1:12 (S.I. 575/2018), Tusla medication guidance (two-person check, parent signs on collection), sleep. 31 stories spec:contracted (#1458 #1459 #1462 #1463 #1464 #1503 #1577 #1504 #1507 #1510 #1512 #1579 #1580 #1582 #1583-#1590 #1592 #1593 #1594 #1596-#1600 #1469). 24 new issues (#1577-#1602). 8 mockups. Deck rev 2. Living docs split: #1601, #1602. Still thin: #1470 #1578 #1581 #1591 #1595. Next nights: #1451 (funding stories CHILD-FUND-001..009 from #1497 netting rules), #1450 (care log, incidents: LOG-001..007; rules now in #1601 INC), #1453 (parent comms, CHILD-PAR-010 first), #1466, #1468; also CHILD-ENR-001 enrolments (D-39), CHILD-GDPR rights rules for #1581.
- 2026-11-25 (night 1): 10 agents. 116 IE rules sourced (60 care + 56 funding), GB-ENG sketch. 15 stories spec:contracted, 14 new issues, 4 mockups, deck rev 1. Next epics in order: #1449 (no stories yet), #1452, #1451 (stories from netting rules), #1450, #1453, #1466, #1468; also finish #1448 (#1458 #1459 #1462 #1463 #1464 #1469 #1470 #1472-1474 still thin).

## Issues
| Issue | Title | Label | Last groomed | Mockup | Open questions |
|---|---|---|---|---|---|
| #1448 | EPIC: Child-side A: Staff-confirmed offline child check-in/out + Hive-grade roll book (Pha | spec:thin | 2026-11-27 | - | - |
| #1449 | EPIC: Child-side B: Child profile, dietary needs, allergens and medication | spec:thin | 2026-11-26 | - | - |
| #1450 | EPIC: Child-side C: Teacher notes, daily care log and incidents | spec:thin | 2026-11-27 | - | - |
| #1451 | EPIC: Child-side D: ECCE/NCS funding, Hive week worklist and family invoicing | spec:thin | 2026-11-28 | - | - |
| #1452 | EPIC: Child-side E: Teacher tools (room tablet: my room now, step-out guard, handover, hea | spec:thin | 2026-11-26 | - | - |
| #1453 | EPIC: Child-side F: Parent communications (portal, messages with read receipts, absences,  | spec:thin | 2026-11-28 | - | - |
| #1454 | EPIC: Child-side G: Country policy layer (child policy packs: IE first; GB-ENG, US-state a | spec:thin | 2026-11-27 | - | - |
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
| #1466 | EPIC: Child-side H: Hermes chief-of-staff agent for crèche admins (optional, MCP-connected | spec:thin | 2026-11-28 | - | - |
| #1468 | EPIC: Multi-location and multi-organisation tenancy (shared staff, site isolation, group r | spec:thin | 2026-11-28 | - | - |
| #1469 | CHILD-TT-006a: Morning room balance: suggested child moves, merges, splits and staff moves | spec:contracted | 2026-11-26 | https://claude.ai/artifact/383wzXDGzHno5tqLdA8oGr | - |
| #1470 | CHILD-TT-007: Staff tap into a room with their Paxton fob on the room tablet | spec:contracted | 2026-11-27 | - | Paxton fob Web NFC test result to record (not blocking) |
| #1471 | CHILD-ATT-011: Ratio proof report for any room and time window | spec:contracted | 2026-11-25 | https://claude.ai/artifact/3dWemvAYRM8YDEpwuF7VWB | - |
| #1472 | CHILD-MIG-001a: Staged child import for the move off TeachKloud: signed-off mapping report | spec:contracted | 2026-11-28 | https://claude.ai/artifact/MNYFRFbDwyJ7zzb7vYEPnK | - |
| #1473 | CHILD-P0: TeachKloud exit test with Sandra (discovery, no code) | spec:thin | - | - | - |
| #1474 | CHILD-LOG-006: Safety checklists and policy acknowledgement | spec:thin | 2026-11-27 | - | Colm: build in Timebreez or via Hubduck |
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
| #1578 | CHILD-ATT-004b: Absences from parent chat messages, and the no-show prompt to the guardian | spec:contracted | 2026-11-27 | - | - |
| #1579 | CHILD-SEC-002b: Offline quick-PIN check on enrolled devices (device-bound same-day verifie | spec:contracted | 2026-11-26 | https://claude.ai/artifact/2wYQgngUYeSBQ8BFmowo5z | - |
| #1580 | CHILD-GDPR-003: DPIA template and controller pack, pre-filled from live data | spec:contracted | 2026-11-26 | - | - |
| #1581 | CHILD-GDPR-004: Data subject requests for child records (access with welfare withhold, era | spec:contracted | 2026-11-27 | - | - |
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
| #1595 | CHILD-TT-002: Step-out and break guard on the room tablet: ratio effect, pack checks, cove | spec:contracted | 2026-11-27 | https://claude.ai/artifact/6twbYHGmAPPAijbv7xuEBm | - |
| #1596 | CHILD-TT-003: Room handover checklist and end-of-day room close (everyone accounted for) | spec:contracted | 2026-11-26 | - | - |
| #1597 | CHILD-TT-004: Scheduled room headcount checks with drift alerts and recorded missed checks | spec:contracted | 2026-11-26 | - | - |
| #1598 | CHILD-TT-005a: Shared room tablet operator mode: staff PIN/fob unlock, switch, auto-lock,  | spec:contracted | 2026-11-26 | - | - |
| #1599 | CHILD-TT-005b: Minimal encrypted room tablet caches and wipe evidence (incl. the emergency | spec:contracted | 2026-11-26 | - | - |
| #1600 | CHILD-TT-006b: Room balance cost effect and morning notice to the person in charge | spec:contracted | 2026-11-26 | https://claude.ai/artifact/383wzXDGzHno5tqLdA8oGr | - |
| #1601 | CHILD-REG (part 3): IE allergens, medication, incidents, sleep and school-age rules (night | doc | 2026-11-26 | - | - |
| #1602 | CHILD-ARCH (part 3): health data, room tablet tools, devices and night-2 decisions | doc | 2026-11-26 | - | - |
| #1668 | CHILD-REG (part 4): IE funding 2026/27 updates, GDPR rights, parent comms and care log rul | doc | 2026-11-27 | - | - |
| #1669 | CHILD-ARCH (part 4): funding ledger, care log, parent comms data model and security (night | doc | 2026-11-27 | - | - |
| #1670 | CHILD-ENR-001: Enrolments, weekly booking patterns and exceptions, checked against the liv | spec:contracted | 2026-11-27 | - | - |
| #1671 | CHILD-FUND-001: Funding registrations copied from the funder award, with overlap and award | spec:contracted | 2026-11-27 | - | - |
| #1672 | CHILD-FUND-002: Funder export import and reconcile (read-only towards the funder; IE Hive  | spec:thin | 2026-11-27 | - | Q-F2: sample Hive export (Sandra) |
| #1673 | CHILD-FUND-003: Monday funder worklist from the roll book, with the days and recorders beh | spec:contracted | 2026-11-27 | https://claude.ai/artifact/NtnD5Nh5mRAnmgEgLutLKY | - |
| #1674 | CHILD-FUND-004: Programme year, service calendar, readiness checklist and AIM supports (ro | spec:contracted | 2026-11-27 | - | - |
| #1675 | CHILD-FUND-005a: Fee schedules with sourced cap, fee-freeze and notice checks before publi | spec:contracted | 2026-11-27 | - | - |
| #1676 | CHILD-FUND-008: Universal payer model: family and agency payers, guardian members and per- | spec:contracted | 2026-11-27 | - | - |
| #1677 | CHILD-FUND-005b: Billing preview with ECCE and NCS netted per line and the rule shown on e | spec:contracted | 2026-11-27 | https://claude.ai/artifact/GYQccBfVV4eS2K7vBEdxee | - |
| #1678 | CHILD-FUND-005c: Hash-checked invoice run, gap-free numbering and self-explaining invoice  | spec:contracted | 2026-11-28 | https://claude.ai/artifact/U3aGrsZLo6uPWtECE9aesJ | - |
| #1679 | CHILD-FUND-007: Expected vs received subsidy with each variance explained from recorded ev | spec:contracted | 2026-11-27 | - | - |
| #1680 | CHILD-LOG-001: Quick-entry care log per child or whole room on the room tablet (meals, bot | spec:contracted | 2026-11-27 | https://claude.ai/artifact/XCjP5XC314tKi2CdiLaGfD | - |
| #1681 | CHILD-LOG-002a: Accident and incident record with coded body map, witnesses and first-aide | spec:contracted | 2026-11-27 | https://claude.ai/artifact/APSnMwcygu5TSJHJiHxswu | - |
| #1682 | CHILD-LOG-002b: Incident shared with parents and acknowledged at pickup (never blocks chec | spec:contracted | 2026-11-27 | https://claude.ai/artifact/APSnMwcygu5TSJHJiHxswu | - |
| #1683 | CHILD-LOG-003: Handover notes addressed to a room and time window, reaching whoever the ro | spec:contracted | 2026-11-27 | - | - |
| #1684 | CHILD-LOG-004: Parent daily summary generated by template from each child's own care log,  | spec:contracted | 2026-11-27 | - | - |
| #1685 | CHILD-LOG-005: Restricted safeguarding notes and mandated report tracking (DLP only, never | spec:contracted | 2026-11-27 | - | - |
| #1686 | CHILD-PAR-001: Passwordless parent portal with multiple guardians and separated-parent vis | spec:contracted | 2026-11-27 | https://claude.ai/artifact/YTg1yAeTvNG9hoCVqZEjGu | - |
| #1687 | CHILD-PAR-001b: Pre-enrolment information pack and About this centre, generated from live  | spec:contracted | 2026-11-27 | - | - |
| #1688 | CHILD-PAR-010: Parent-only WhatsApp and Telegram channels: fail-closed webhooks, store-fir | spec:contracted | 2026-11-27 | - | Q-S4/Q-S5: WhatsApp transfer basis, Telegram for IE controller |
| #1689 | CHILD-PAR-007: Parent channel preference with opt-in proved from the phone, one-tap switch | spec:contracted | 2026-11-27 | - | - |
| #1690 | CHILD-PAR-002: Per-child threads and room/centre broadcasts with per-guardian read receipt | spec:contracted | 2026-11-27 | https://claude.ai/artifact/5Tia2pq339ut6jknSkPUFp | - |
| #1691 | CHILD-PAR-008: Sensitive actions portal-only via single-use action links that never sign i | spec:contracted | 2026-11-27 | - | - |
| #1692 | CHILD-PAR-009: Chat safeguards: data-classed templates, sensitive messages portal-only, mi | spec:contracted | 2026-11-27 | - | Q-S10: free text off until DPIA owner accepts |
| #1693 | CHILD-PAR-003: Parent actions hub and requests (extra session, change a day, add a collect | spec:contracted | 2026-11-27 | https://claude.ai/artifact/Ph2yhZaAQ6NbqVxBvuojGp | - |
| #1694 | CHILD-GDPR-004b: Rectification with parent statements, erasure checked against retention,  | spec:contracted | 2026-11-27 | - | - |
| #1697 | Security: whatsapp-webhook accepts unsigned requests when WHATSAPP_APP_SECRET is unset (fa | security | 2026-11-27 | - | is WHATSAPP_APP_SECRET set on staging/live (unchecked) |
| #1761 | CHILD-REG (part 5): IE payments, complaints, multi-site, AI assistant and migration rules  | doc | 2026-11-28 | - | - |
| #1762 | CHILD-ARCH (part 5): payments ledger, complaints, multi-site tenancy, AI assistant and imp | doc | 2026-11-28 | - | - |
| #1763 | CHILD-PAR-004a: Daily summary delivered on each guardian's channel, chat-safe sections onl | spec:contracted | 2026-11-28 | https://claude.ai/artifact/RLRueqreEUvY5haTgw1UqQ | - |
| #1764 | CHILD-PAR-004b: Room photos with every child in the frame tagged, sent only under unbundle | spec:contracted | 2026-11-28 | https://claude.ai/artifact/Qth8JXHC1Mi8evriWJcLqw | - |
| #1765 | CHILD-PAR-005a: Parent billing view (read only): invoices with subsidy lines and rules, pa | spec:contracted | 2026-11-28 | https://claude.ai/artifact/UhfddTNL1d4MzwCCCTBC4t | - |
| #1766 | CHILD-PAR-005b: Pay now and Direct Debit set-up in the parent portal (blocked: whose merch | spec:thin | 2026-11-28 | - | Q-B1 whose merchant account |
| #1767 | CHILD-PAR-006: Optional parent attendance sign-off over the staff-recorded entries, with p | spec:contracted | 2026-11-28 | https://claude.ai/artifact/8YLciJjZinhANWT98tXN8q | - |
| #1768 | CHILD-PAR-012a: Complaint case with dated events, impartial handler and named-person locko | spec:contracted | 2026-11-28 | https://claude.ai/artifact/FfUfStHiFKyMHcCFaRBNAP | - |
| #1769 | CHILD-PAR-012b: Complaints review (trends, training evidence), inspector complaints file,  | spec:contracted | 2026-11-28 | https://claude.ai/artifact/WA6bE6Q2HbqoBHQqB9yfUm | - |
| #1770 | CHILD-FUND-006a: Family payment ledger: record and allocate payments, receipts, credit not | spec:contracted | 2026-11-28 | https://claude.ai/artifact/RiN8pKnzkW6sNMbgWuouL9 | - |
| #1771 | CHILD-FUND-006b: Centre's own payment account (two-person payee change) and one-off card p | spec:thin | 2026-11-28 | - | Q-B1 + provider choice |
| #1772 | CHILD-FUND-006c: SEPA Direct Debit mandates, pre-notices, collections and reversals (block | spec:thin | 2026-11-28 | - | Q-B1, Q-S15 IBAN storage |
| #1773 | CHILD-FUND-006d: Bank transfer and standing order reconciliation from an imported statemen | spec:contracted | 2026-11-28 | https://claude.ai/artifact/VsxzTMbEmdk3FEBoWJPcbK | - |
| #1774 | CHILD-FUND-006e: Family statements built from the ledger and sealed with a hash, with refu | spec:contracted | 2026-11-28 | https://claude.ai/artifact/8fYzqKcNXzwkFqgnu9Pfcf | - |
| #1775 | CHILD-FUND-006f: Aged debt and reminders that never reach a paid, queried, scheduled or re | spec:contracted | 2026-11-28 | https://claude.ai/artifact/U8ULDvWsFmhPiiRK3E3NBX | - |
| #1776 | CHILD-FUND-009: Per-service funding, never merged across services, with wrong-location and | spec:contracted | 2026-11-28 | https://claude.ai/artifact/KyU4vpmDGxBa5nxAkEMizx | - |
| #1777 | CHILD-COS-001: Hermes switch-on: DPIA and processor gates, per-call delegated identity, ar | spec:contracted | 2026-11-28 | https://claude.ai/artifact/M4WDTsNhBVCYwXjeGRDEkQ | - |
| #1778 | CHILD-COS-005: Hermes read-only morning brief over the same read functions, every number l | spec:contracted | 2026-11-28 | https://claude.ai/artifact/QKxqGPXrt6FCejj1Ecgiez | - |
| #1779 | CHILD-COS-006: Hermes drafts that a named person approves: exact payload, run once in the  | spec:contracted | 2026-11-28 | https://claude.ai/artifact/Wf28G4rqAAzaBozkJM3BwG | - |
| #1780 | CHILD-TEN-001: Services under one organisation: registration per premises, deadlines from  | spec:contracted | 2026-11-28 | https://claude.ai/artifact/CMSLBA2kdF9RT4fNGNFEEz | - |
| #1781 | CHILD-TEN-002: Shared staff counted per site: latest room tap on an enrolled device, vetti | spec:contracted | 2026-11-28 | https://claude.ai/artifact/TzAXmz53JSGyotRkvgykMz | - |
| #1782 | CHILD-TEN-003: Group reports as guarded totals: sharing agreement per organisation, group  | spec:thin | 2026-11-28 | - | ADR-027 + same company or two (Q-T2, C-55) |
| #1783 | CHILD-MIG-001b: Cut-over day, rehearsal that never counts, first-week head-count check, le | spec:contracted | 2026-11-28 | https://claude.ai/artifact/B8KHKjLAWDLJAPZiKqakbh | - |

## Cross-night open questions
- Pam's day-to-day role (not on record; ask Colm).
- Named competent reviewer for IE rule content (care, and separately funding) (Q-R2).
- Attendance retention: 2 years after leaving (care) vs 6 years (funding) (Q-R1).
- Who does the Hive return and payroll at SSST day to day (Mella per memory, #1447 says Sandra's Hive week).
- Q-P1: who owns the DPIA / is DPO at Timebreez and at each centre (blocks DPIA sign-off #1580 and any pilot with real children, not the build).
- Q-B1: whose merchant account takes family money (blocks #1766 #1771 #1772; ledger, statements, bank reconcile and debt are contracted without it).
- Q-F2: a sample Hive export from Sandra (blocks #1672).
- Q-B5: answered from sources night 4 (childcare exempt, family invoice not a VAT invoice; TAX-001/002); #1678 contracted; accountant still to confirm.
- Q-S4 / Q-S5: lawful transfer basis for WhatsApp (Meta); is Telegram acceptable for an IE controller (#1688). Named data-protection reviewer.
- #1474: build checklists and policy sign-off in Timebreez, or deliver through Hubduck (Colm).
- Pack key name for netting order (#1510) and ECCE expected-subsidy model (D-51 vs #1679).
- Q-H1: does a portal typed-name signature meet "signed parental consent" (MED-001, MED-007)? Named reviewer.

- ADRs (27 Nov, Colm "adrs now"): child-side ADR-021..026 live in timebreez docs/architecture/child/ with static CI ratchets (scripts/adr/childChecks.ts), PR #1745 (#1742). New child decisions that are load-bearing go in an ADR, not only a D-row. Next free ADR: 027.

- Night 4: is the university crèche the same company as the first or a separate one (#1468, #1782)? Can one person be in charge of both? Who reviews payment, contract and VAT rules (an accountant and a solicitor)? Which LLM vendor would Hermes use and where does it process data? Absence/closure charging terms (solicitor). Current Tusla complaints process (2017 SOP vs current page).

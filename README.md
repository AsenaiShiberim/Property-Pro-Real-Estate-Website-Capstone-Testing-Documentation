# Property-Pro-Real-Estate-Website-Capstone-Testing-Documentation

# Property Pro – QA Testing & Documentation

**My Role:** Front-End Developer & QA Tester  
**Project Type:** Group Capstone Project — SAIT Software Development Diploma  
**Testing Period:** October – December 2024  
**Tech Stack:** Next.js, Tailwind CSS, Node.js, MongoDB, Firebase, Clerk, Jest, Postman, Vercel

---

## A bit of background

Property Pro is a real estate marketplace our team built for our capstone at SAIT. The idea behind it came from Calgary's rapid population growth — the city grew by 5.6% in 2023 alone, so there was a real story behind why a platform like this would matter.

The app connects three types of users: buyers looking for properties, sellers managing their listings, and property managers handling bookings and inquiries. Each group has their own dashboard and permissions, which made the testing side of things genuinely interesting — there were a lot of moving parts to validate.

My personal contributions covered front-end development and QA testing. This repo focuses specifically on the testing work — the strategy, execution, findings, and lessons learned along the way.

---

## What we were testing

The platform had a lot going on, so we scoped our testing around the features that mattered most to each type of user:

**For Sellers:**
- Could they view, edit, and manage their listings from their dashboard?
- Did the property submission forms properly validate data and handle image uploads?

**For Buyers:**
- Did search filters, sorting, and results display work correctly?
- Could new users register and log in without issues?

**For Property Managers:**
- Did the management dashboard correctly track listings?
- Could managers book and handle viewing appointments?

We also intentionally kept some things out of scope — third-party payment gateways, mobile app testing, and multi-language support were all excluded since they were outside the boundaries of the project.

---

## The numbers

By the end of testing we had executed **128 test cases** across the platform. Here's how it shook out:

| Metric | Result |
|--------|--------|
| Total Test Cases Executed | 128 |
| Passed | 100 |
| Failed | 28 |
| Overall Success Rate | 73.3% |

The 73.3% success rate sounds like it has room to grow, but context matters here — a lot of the failures were caught early in the sprint cycle and fixed before the next round. The success rate trended upward week over week, which was the real indicator that the process was working.

**Sprint-by-sprint breakdown:**

| Sprint | Total Cases | Attempted | Failed | Success Rate |
|--------|-------------|-----------|--------|--------------|
| Oct 6–12 | 40 | 10 | 4 | 60% |
| Oct 13–17 | 20 | 10 | 3 | 70% |
| Oct 20–26 | 20 | 15 | 5 | 66.7% |
| Oct 27–Nov 3 | 20 | 18 | 6 | 66.6% |
| Nov 4–9 | 25 | 15 | 4 | 73.3% |

---

## What we tested and how

We covered five main types of testing:

**Functional Testing** — The bread and butter. Verified CRUD operations, authentication flows, search and filtering, and role-based access. This is where most of the bugs lived.

**Security Testing** — Made sure users couldn't access pages they weren't supposed to. Admin dashboards, seller-only features, and login/logout flows were all tested for unauthorized access.

**API Testing** — Checked that the frontend was correctly talking to the backend when fetching property data, and that errors were handled gracefully when API calls failed.

**Performance Testing** — Simulated load to see how the system held up with multiple users active at the same time, especially during data-heavy operations like search.

**Usability Testing** — Went through the app on different screen sizes to check responsiveness, navigation flow, and whether the UI made sense for non-technical users.

---

## Defect log

| Date | TC ID | Tester | What Was Tested | Result | Notes |
|------|-------|--------|-----------------|--------|-------|
| 2024-11-05 | TC001 | Asenai | Login/logout with Clerk | ✅ Pass | Working correctly end to end |
| 2024-11-05 | TC002 | Robel | Property click navigates to details page | ✅ Pass | Correct property info displaying |
| 2024-11-05 | TC003 | Miebaka | Adding property to favourites | ✅ Pass | Saved to user profile successfully |
| 2024-11-06 | TC004 | Jerome | Manager can delete property | ✅ Pass | Role-based permissions working |
| 2024-11-06 | TC005 | Robel | Manager can edit property | ❌ Fail | Didn't navigate to the correct property |
| 2024-11-07 | TC006 | Asenai | All new attributes display correctly | ❌ Fail | Some properties missing attributes like build date |
| 2024-11-07 | TC007 | Miebaka | Calculation accuracy | ✅ Pass | Correct values displayed |

---

## Key findings

**Finding 1 — Property Edit Navigation Failure**  
When a manager tried to edit a property, the system wasn't routing them to the right page. This was a high severity issue because it completely blocked a core admin workflow. We flagged it immediately and it was escalated to the dev team.

**Finding 2 — Missing Property Attributes**  
Some listings weren't showing all their expected fields — things like build date were just absent on certain properties. Medium severity, but it affected the completeness of what buyers were seeing. Documented and sent to the backend team.

**Finding 3 — Map API Integration Issues**  
The map API was throwing integration errors in certain scenarios. This one took a few rounds to fully resolve but was caught through regression testing before deployment.

**Finding 4 — Filtering Inconsistencies**  
Search filters weren't always returning consistent results. Flagged, fixed, and re-verified during regression.

---

## What went well

Role-based access control was actually our strongest area — we hit a **100% success rate** across all admin, buyer, and seller permission tests. That was a big deal for a platform where different users have very different levels of access.

Search and filter integration also came together well once the inconsistencies were resolved. By the final sprint it was working cleanly across all the criteria we tested.

---

## What I'd do differently

Honestly, the biggest thing I learned from this project is that a passing response code doesn't mean the feature works end to end. TC005 was a perfect example — the edit flow returned no errors but the navigation was broken. You have to actually follow the full user journey, not just check that individual pieces respond correctly.

I'd also push for earlier performance testing next time. We left load testing a bit late in the cycle and it would have been useful to know sooner how the system held up under concurrent users.

---

## Files in this repo

- `README.md` — this file
- `Test_Strategy.pdf` — full risk analysis and testing approach
- `Test_Plan.pdf` — 50 test case documentation and objectives
- `Test_Execution.pdf` — defect log, sprint tracking, and results
- `SoftwareTestingPresentation.pdf` — final capstone presentation slides

---

*Group capstone project built with a team of 4 at SAIT, Software Development Diploma, 2024.*

| Test Strategy for CINELORA AI |
| :---: |

**Summary**

* [1. Purpose of the document](#1-purpose-of-the-document)
* [2. Objective](#2-objective)
* [3. Description of the project](#3-description-of-the-project)
* [4. Scope of work](#4-scope-of-work)
* [4.1. Components and functions to be tested](#41-components-and-functions-to-be-tested)
* [4.2. Components and functions not to be tested](#42-components-and-functions-not-to-be-tested)
* [5. Quality criteria](#5-quality-criteria)
* [6. Resources](#6-resources)
* [6.1. Tools for testing](#61-tools-for-testing)
* [6.2. Browsers and devices](#62-browsers-and-devices)
* [7. Deliverables](#7-deliverables)
* [8. Points of Contact](#8-points-of-contact)
* [9. Communication Plan](#9-communication-plan)
* [10. Responsibilities](#10-responsibilities)
* [11. Development Process and QA Involvement](#11-development-process-and-qa-involvement)
* [12. Testing phases](#12-testing-phases)
* [13. Risk-based Testing Approach](#13-risk-based-testing-approach)
* [14. Testing methods and test types](#14-testing-methods-and-test-types)
* [14.1. Testing methods](#141-testing-methods)
* [14.2. Test types](#142-test-types)
* [14.3. Automation Testing Strategy](#143-automation-testing-strategy)
* [14.4. Non-functional Testing Approach](#144-non-functional-testing-approach)
* [15. Defect tracking and documentation](#15-defect-tracking-and-documentation)
* [15.1. Defect severity](#151-defect-severity)
* [15.2. Defect priority](#152-defect-priority)
* [15.3. Bug report content](#153-bug-report-content)
* [16. Risks](#16-risks)
* [17. Test completion criteria](#17-test-completion-criteria)

# 1. Purpose of the document

This document describes the test strategy for the Cinelora AI web application – an AI‑driven web SaaS platform focused on text‑to‑image and text‑to‑video generation. It defines the approaches that the test team will use to verify the quality of the product prior to release.

The document also lists the main resources, test types and rules of interaction that are needed for successful testing of the project.

# 2. Objective

The purpose of this test strategy is to formalize the testing process, plans and approaches, and to interface the testing process with the development team and the project team in order to achieve high quality of the Cinelora AI web platform.

The strategy explicitly takes into account AI‑specific aspects of Cinelora AI:

* probabilistic and non‑deterministic behavior of image/video generation;  
* dependency on external AI model providers and their limits/quotas;  
* usage‑based billing and credit consumption for AI jobs;  
* risks related to NSFW and harmful content and the need for effective content moderation.

# 3. Description of the project

Cinelora AI is a web‑based AI platform that allows users to:

* generate images from text prompts;  
* generate short videos from text prompts (and optionally from images);  
* store, view, download, and share generated media content;  
* use the service under a Freemium model (free tier \+ paid plans/credits).

The project is developed and tested by internal teams; external testing services may be involved if needed.

As an AI‑driven product, Cinelora AI has the following characteristics that influence the testing strategy:

* Generated outputs (images/videos) are not strictly deterministic even with similar prompts;  
* Quality, speed and stability of generation depend on external AI model providers and their current load;  
* There is an inherent risk of generating inappropriate or unsafe content, which requires special attention to moderation flows, NSFW filters and user reporting tools.

# 4. Scope of work

## 4.1. Components and functions to be tested

The following components and functions of the Cinelora AI web portal are in scope:

1. Registration & Authentication (registration, login, logout, password recovery).  
2. User profile (settings, password, account deletion)  
3. Plans, billing and credits (plans, purchases, credit deduction, history)  
4. Prompt creation (Prompting UI) and generation parameters  
5. Generation queue and statuses (queued/processing/succeeded/failed, limits)  
6. User gallery (My creations), filters, sorting, search, bulk actions  
7. Item details view (metadata, download, favorites, variations)  
8. Public links and sharing, global gallery / Explore  
9. Content moderation and NSFW filters  
10. Admin part (user management, content reports, basic analytics)  
11. UI/UX, responsiveness and cross‑browser behavior

The scope focuses on end‑to‑end user flows that are typical for AI‑generation platforms: from prompt creation and credit consumption to content generation, moderation and sharing.

## 4.2. Components and functions not to be tested

The following are out of scope for this strategy:

* Native mobile applications (iOS/Android).  
* Full‑scale security / penetration testing.  
* Full‑scale performance / load / stress testing.  
* Evaluation of artistic or creative quality of AI output (only basic checks that files are generated and can be opened).

# 5. Quality criteria

The product should operate in accordance with the approved requirements and the functional specification.
The product should not contain critical and blocking defects in the final (release) version.

Key success factors:

* All planned tests are performed.  
* There are no show‑stopping (blocking/critical) errors.  
* Core business flows are stable, including:  
  * registration, login, password recovery;  
  * prompt creation;  
  * image/video generation;  
  * viewing and downloading media;  
  * plan/credit purchase and deduction;  
  * public links and basic moderation.  
* Test results are evaluated, discussed and approved by responsible stakeholders (PM, Tech Lead, Product Owner).

# 6. Resources

## 6.1. Tools for testing

The following tools are used for testing and documentation:

| Tool | Comment |
| ----- | ----- |
| Jira | Defect tracking |
| TestRail / Google Sheets | Test case management |
| Teams / e‑mail | Daily communication and status |
| Browser DevTools | Layout checks and technical analysis |
| Figma | Checking UI against design mockups |
| Postman / DB tools | Specific API/DB checks |
| OS/browser built‑in tools, Snagit/Loom | Screenshots and video capture |

## 6.2. Browsers and devices

**Browsers (web only):**

* Chrome – latest;  
* Firefox – latest;  
* Edge – latest;  
* Safari – latest.

**Devices (web only):**

* Desktop: Windows 10/11, macOS.  
* Mobile web: current iOS and Android OS. 

# 7. Deliverables

**Testing Documentation and Reports**

| Title | Responsible person | Frequency (delivery time) | Delivery method |
| ----- | ----- | ----- | ----- |
| Test Plan | QA Team | One time before testing start | e‑mail / Google Docs |
| Test cases | QA Team | Before start of test execution | TestRail / Google Sheets |
| Checklists | QA Team | One time before main test runs | Google Sheets |
| Bug reports | QA Team | After bug detection | Jira |
| Test Summary Report / Test report | QA Lead | After every major test run / before release | e‑mail / Google Docs |

# 8. Points of Contact

**The team of external testing**

| Company | Name | Role | Contact Information |
| ----- | ----- | ----- | ----- |
| TestComp | Anna Petrenko | Program Manager | Email: anna.petrenko@test.com |
| TestComp | Dmytro Ivanenko | QA Tester | Email: dmytro.ivanenko@test.com |

**The team on Customer side**

| Company | Name | Role | Contact Information |
| ----- | ----- | ----- | ----- |
| Cinelora AI | Oleksii Tarasenko | Product Owner | Email: support@cinelora.ai |
| Cinelora AI | Anna Kovalenko | Project Manager | Email: pm@cinelora.ai |

# 9. Communication Plan

| What | Who/Target | Purpose | When/Frequency | Type/Method |
| ----- | ----- | ----- | ----- | ----- |
| Initiation Meeting | Project Manager / QA Lead, QA team | Gather information for Test Strategy, introduction to project | Before project start | Meeting (online/office) |
| Status Update | Project Manager / QA Lead, QA team | QA status update about schedule and scope | Every working day | Daily reports via e‑mail, questions in Teams  |
| Team planning / review  | PM / QA Lead, QA team | Review detailed plans, tasks, urgent questions | Weekly | Meeting with meeting notes |
| Retrospective  | PM / QA Lead, QA team | Review overall health of the process and areas for improvement | Once a month | Meeting with meeting notes |

# 10. Responsibilities

**Project Manager / Product Owner:**

* Plan releases and sprints.  
* Prioritize features and bug fixes.  
* Provide resources for testing.  
* Approve final test results.

**QA Tech Lead:**

* Define testing approaches, tools, and processes.  
* Analyze risks.  
* Distribute QA tasks.  
* Coordinate with development and PM.

**QA Engineer:**

* Analyze requirements.  
* Prepare test documentation (test cases, checklists, Test Plan).  
* Execute tests, log defects in Jira.  
* Maintain test status in TestRail.  
* Prepare interim and final test reports.

# 11. Development Process and QA Involvement

The project follows an iterative development process (Scrum‑like with sprints / continuous delivery).  
QA involvement:

* Participate in refinement and planning sessions to clarify requirements and acceptance criteria.  
* Review user stories in Jira before development (shift‑left testing).  
* Prepare test cases in parallel with development.  
* Perform smoke testing on each new build; perform full regression testing before major releases.  
* Provide continuous feedback on quality/risk and propose improvements to the process during retrospectives.

# 12. Testing phases

Main stages of work of the testing team:

1. Development of the Test Strategy.  
2. Coordination and approval of the Test Strategy.  
3. Receiving and studying the final version of the specification / requirements.  
4. Writing test cases for new and existing functionality.  
5. Setting up the test environment and test accounts (Free, Pro, Admin).  
6. Smoke testing of a new build.  
7. Functional testing of new functionality (executing test cases).  
8. Writing bug reports and logging issues into the bug tracking system.  
9. Regression testing, including retest of fixed defects.  
10. Writing a Test Summary Report.

# 13. Risk-based Testing Approach

Testing activities and priorities will be driven by business and technical risks:

* **Highest‑priority areas (must have, maximum coverage):**  
  * Authentication and access (registration, login, password recovery).  
  * Billing and credits (purchases, credit deduction, error handling).  
  * Core AI generation (image/video generation, queue, statuses).  
  * Media access (viewing, downloading generated content).  
  * Content moderation and NSFW filters.  
  * Admin tools for user management and basic analytics.  
* **Medium‑priority areas (good coverage, but can be optimized):**  
  * Advanced generation options (styles, history, variations).  
  * Global gallery / Explore, social sharing.  
  * Non‑critical profile settings and preferences.  
* **Lower‑priority areas (minimal necessary coverage):**  
  * Minor UI cosmetic differences from design that do not affect usability.  
  * Rare edge cases with low business impact.

In case of limited time or resources, test execution will focus first on high‑risk / high‑impact areas. Any planned tests that are skipped due to constraints will be explicitly listed in the Test Summary Report together with justification.

# 14. Testing methods and test types

## 14.1. Testing methods

Manual functional testing is regarded as the primary method of testing the application.

## 14.2. Test types

The following test types are planned for Cinelora AI:

* **Functional Testing**  
  Verification of all business functions: registration, profile, generation, billing, gallery, sharing, moderation, admin panel.  
* **UI Testing**  
  Layout correctness, consistency with designs, responsive behavior.  
* **Usability Testing (basic)**  
  Verifying clarity and simplicity of critical flows from entering a prompt to receiving and downloading the result.  
* **Compatibility Testing**  
  Verification on supported desktop and mobile web browsers.  
* **Mobile Web Testing**  
  Testing on different phones/tablets (mobile devices) with different browsers and operating systems to check functionality and appearance on different screen sizes.  
* **Regression Testing**  
  Ensuring no regressions after changes and bug fixes.  
* **Retesting**  
  Verifying fixes for previously reported defects.

## 14.3. Automation Testing Strategy

At the current stage, manual functional testing is the primary method of testing. However, the following automation directions are considered for future iterations:

* **UI regression smoke:**  
  * Automate a small set of end‑to‑end smoke tests for critical flows (login, prompt creation, basic generation, billing flow, download).  
  * Purpose: fast validation of main user scenarios on each build.  
* **API‑level checks:**  
  * Automate key API endpoints for generation, billing, and user management to detect regressions early.  
* **Test data management:**  
  * Where feasible, use scripts or tools to prepare and clean test data (test users, credits, content) to speed up manual and automated tests.

Decisions about actual implementation, tools and coverage for automation will be made based on project priorities, stability of the UI/API, and available resources.

## 14.4. Non-functional Testing Approach

Full‑scale performance, load and security testing are out of scope for this phase. However, the following basic non‑functional checks will be included in the general testing process:

* **Basic performance sanity:**  
  * Observe generation times and page load times for the main flows; report any obvious degradations compared to previous builds.  
* **Basic security sanity:**  
  * Verify that authentication and session handling behave as expected (no access to protected pages without login, no obvious data leaks in UI).  
* **Stability of external integrations:**  
  * Monitor error rates and timeouts from AI providers and payment gateways during normal use.

A separate Performance/Security testing strategy can be defined for future phases or dedicated test cycles.

# 15. Defect tracking and documentation

The tools described in the Tools for testing section will be used to track defects and testing documentation. Metrics and statistics will be included in the test reports where applicable.

Severity describes the level of impact of a bug on the overall functionality of the product under test.  
Priority is used to display how quickly a bug needs to be fixed.

## 15.1. Defect severity

* **Critical (Blocker)**  
  Complete system or critical subsystem failure; inability to execute key flows (login, generation, payment, download); data loss or inconsistent database state.  
* **Major**  
  Serious failures in essential functionality where a workaround exists, but user experience is significantly degraded; crashes in non‑critical flows.  
* **Minor**  
  Incorrect or incomplete results that do not block main flows.  
* **Trivial**  
  Small UI issues, typos, minor visual differences from design.

## 15.2. Defect priority

* High – impact the business in a big way; need immediate attention and must be addressed as soon as possible.  
* Medium – moderate/low impact on business; can be fixed in an upcoming release.  
* Low – negligible impact on business; can be fixed when higher‑priority work is done.

## 15.3. Bug report content

Each bug report in Jira should contain at least:

* Product/module name.  
* Build/version.  
* Environment details (browser, OS, account type: Free/Pro/Admin).  
* Summary (short problem description).  
* Location (URL, page, component).  
* Steps to Reproduce (clear, ordered steps).  
* Actual Result.  
* Expected Result.  
* Frequency (always / sometimes / once).  
* Severity and Priority.  
* Attachments where applicable:  
  * screenshots;  
  * video(if necessary);  
  * console/network logs(if relevant).

All bugs must be recorded in the bug tracking system.

# 16. Risks

Potential risks affecting quality and schedule:

* Unplanned changes in functionality or architecture without prior QA involvement.  
* Requirement changes without updating documentation.  
* Delays in fixing critical defects.  
* Delays in delivering new builds to the test environment.  
* Instability of external services:  
  * AI providers;  
  * payment gateways.  
* Limited QA resources (small team, tight deadlines).

**AI‑specific risk:**

* Staging vs Production AI models: Staging may use different (cheaper/faster) AI model versions or configurations than Production, which can affect:  
  * generation time;  
  * request limits;  
  * response stability.  
* As a result, behavior observed on Staging (especially performance‑related) might not fully represent Production behavior.  
* Non‑deterministic AI output: The same or similar prompts can produce different results over time, which complicates exact reproducibility of some defects and requires more focus on business acceptance criteria (e.g. “an image is generated and downloadable, no obvious artifacts, content is correctly marked as NSFW/non‑NSFW”) rather than strict pixel‑perfect output comparison.  
* Inappropriate content generation: Despite filters, the AI model may occasionally generate NSFW or otherwise harmful content. This requires thorough testing of:  
  * prompt blocking for forbidden keywords and patterns;  
  * user‑facing warnings and error messages;  
  * content reporting flows;  
  * admin review and decision flows for reported/flagged content.

# 17. Test completion criteria

Testing can be considered complete for a given release if the following conditions are met:

* Smoke testing of the release build is completed and passed.  
* All planned test cases for the current scope have been executed (or reasonably skipped).  
* All found bugs are listed in the bug tracker and have a defined priority.  
* All fixed bugs have been retested.  
* No critical or blocking defects remain in the release build.  
* Core user flows are stable:  
  * registration, login, password recovery;  
  * image/video prompt creation;  
  * media generation, viewing, downloading;  
  * credit/plan purchase and deduction;  
  * public links and basic moderation.  
* Test results (Test Summary Report) are reviewed and accepted by responsible stakeholders (PM, Tech Lead, Product Owner).
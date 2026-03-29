| Test Plan for CINELORA AI |
| :---: |

| General information  |  |
| ----- | :---- |
| **Customer** | Cinelora AI |
| **Created by**  | Larysa S. |
| **Preparation date** | 14.03.2026 |
| **Version** | 1.0 |
| **Status** | Ready for Review |

| Revision History |  |  |  |  |
| ----- | ----- | ----- | ----- | ----- |
| **Version** | **Description** | **Author** | **Date** | **Approved by** |
| 1.0 | Initial version of Test Plan | Larysa S. | 14.03.2026 |  |

**Summary**

* [1. Introduction](#1-introduction)
* [1.1. General information](#11-general-information)
* [1.2. Purpose](#12-purpose)
* [1.3. Requirements and Traceability](#13-requirements-and-traceability)
* [2. Scope of project](#2-scope-of-project)
* [2.1. Scope of Cinelora AI web portal](#21-scope-of-cinelora-ai-web-portal)
* [2.2. Out of scope](#22-out-of-scope)
* [2.3. Assumptions and Constraints](#23-assumptions-and-constraints)
* [3. Work plan](#3-work-plan)
* [3.1. Test Cycle 1 – MVP](#31-test-cycle-1--mvp)
* [3.2. Test Cycle 2 – Extended features](#32-test-cycle-2--extended-features)
* [3.3. Pre-release regression and reporting](#33-pre-release-regression-and-reporting)
* [4. Test Approach](#4-test-approach)
* [4.1. Types of testing](#41-types-of-testing)
* [4.2. Functional testing: objective, technique, entry/exit criteria](#42-functional-testing-objective-technique-entryexit-criteria)
* [4.3. Test procedure](#43-test-procedure)
* [5. Test Data](#5-test-data)
* [6. Bug Reports](#6-bug-reports)
* [6.1. Defect severity](#61-defect-severity)
* [6.2. Defect priority](#62-defect-priority)
* [6.3. Bug report content](#63-bug-report-content)
* [7. Criteria of quality](#7-criteria-of-quality)
* [8. Testing process risks](#8-testing-process-risks)
* [9. Test team expectations](#9-test-team-expectations)
* [10. Responsibilities](#10-responsibilities)
* [11. Resources](#11-resources)
* [11.1. Tools](#111-tools)
* [11.2. Browsers list](#112-browsers-list)
* [11.3. Devices (web only)](#113-devices-web-only)
* [12. Deliverables](#12-deliverables)

# 1. Introduction

## 1.1. General information

This document describes the methods, approaches, and resources that will be used by the QA team during testing of the Cinelora AI web application.

Cinelora AI is a web‑based AI platform that allows users to:

* generate images from text prompts;  
* generate short videos from text prompts (and, optionally, from images);  
* store, view, download, and share generated media content;  
* use the service under a Freemium model (free tier \+ paid plans/credits).

Testing is performed only for the web version (desktop and mobile web). Native mobile applications are out of scope for now.

The document is intended for:

* Product Owner / Project Manager;  
* Team Lead / Tech Lead;  
* Developers (FE, BE, ML);  
* QA team.

## 1.2. Purpose

The purpose of this Test Plan is to:

* define the system components to be tested;  
* describe the testing strategy: types, scope, and depth;  
* define entry and exit criteria for testing;  
* describe required resources (people, tools, environments, test data);  
* define the list of deliverables produced by the testing process.

All defects will be tracked in Jira; test cases and execution results will be maintained in TestRail.

## 1.3. Requirements and Traceability

Requirements sources:

* Product Requirements Document (PRD) – stored in Google Docs / Confluence.  
* User stories and acceptance criteria – stored in Jira (project CIN).  
* Design specifications (UI/UX) – stored in Figma.

Traceability approach:

* High‑level mapping of features to TestRail sections (e.g. “Registration & Login”, “Billing & Credits”, “Generation & Gallery”, “Admin Panel”).  
* Each TestRail test case is linked to one or more Jira user stories where applicable (via “References” field).  
* Critical user flows (registration, login, generation, billing, download, public links) have dedicated, clearly marked test cases and are included in every regression run.

# 2. Scope of project

## 2.1. Scope of Cinelora AI web portal

The following functionality of the web application is in scope:

1. **Registration & Authentication**  
   * Registration via email \+ password.  
   * Login via email \+ password.  
   * Email verification.  
   * Password recovery (Forgot password).  
   * Logout.  
   * Basic rate limiting for login and password recovery attempts.  
2. **User profile**  
   * Viewing profile (name/username, email, avatar, registration date).  
   * Editing profile data (username, avatar, basic settings).  
   * Setting language and theme (light/dark).  
   * Setting default generation parameters (type, size, etc.).  
   * Changing password.  
   * Account deletion.  
3. **Plans, billing and credits**  
   * Displaying pricing plans (Free / Pro / others):  
     * generation limits;  
     * constraints on media size/duration.  
   * Purchasing subscriptions/credit packs via payment gateway (e.g., Stripe sandbox).  
   * Handling successful and failed payments.  
   * Deducting credits for:  
     * one image generation;  
     * one video generation.  
   * Displaying current credits/subscription status.  
   * Viewing transaction history (date, amount, status).  
   * Managing subscription (activation, cancellation, auto‑renewal if implemented).  
   * Handling cases:  
     * generation with zero credits;  
     * purchase attempts with invalid payment data.  
4. **Prompt creation (Prompting UI)**  
   * Fields and parameters:  
     * main text prompt (required);  
     * generation type: Image / Video;  
     * style (realistic, anime, 3D, cinematic, etc.);  
     * size / aspect ratio;  
     * video duration (fixed options, e.g., 4/8/12 seconds);  
     * number of variants (1–4);  
     * seed (fixed/random).  
   * Validation:  
     * minimum/maximum prompt length;  
     * required fields;  
     * handling of invalid characters.  
   * Use of prompt templates (presets).  
   * Prompt history and reuse.  
5. **Generation queue and statuses**  
   * Sending generation requests to backend/AI service.  
   * Displaying statuses:  
     * queued;  
     * processing (with basic progress indicator);  
     * succeeded;  
     * failed.  
   * Handling:  
     * AI service timeouts;  
     * temporary AI API unavailability;  
     * rate limiting on the AI provider/platform side.  
   * Validating limits:  
     * maximum concurrent jobs per user;  
     * daily/monthly limits per plan.  
6. **User gallery (My creations)**  
   * Displaying all generated works as a list/grid:  
     * images (thumbnails);  
     * videos (poster frame with play icon).  
   * Filtering:  
     * by type (image/video);  
     * by date;  
     * by style.  
   * Sorting (newest/oldest, popularity).  
   * Bulk deletion (multi‑select).  
   * Search by prompt text.  
7. **Item details view**  
   * Full image view or video playback via embedded player.  
   * Displaying metadata:  
     * prompt / negative prompt;  
     * style;  
     * generation parameters;  
     * created date/time;  
     * credits spent.  
   * Actions:  
     * Download:  
       * images – .png (primary), optionally .webp;  
       * videos – .mp4 (agreed codec).  
     * Add/remove from Favorites.  
     * Generate variations.  
     * Create a new prompt based on the current one (Duplicate prompt).  
8. **Public links and sharing**  
   * Creating public links for individual works.  
   * Privacy modes:  
     * Private (owner only);  
     * Unlisted (by direct link);  
     * Public (can appear in global gallery).  
   * Viewing public pages without authorization:  
     * media preview;  
     * basic info (author username, date, views/likes if present).  
   * Sharing:  
     * copy link;  
     * social networks (Twitter/X, Facebook, Instagram etc.).  
9. **Global gallery / Explore**   
   * Browsing public content from other users.  
   * Filtering by tags, style, content type.  
   * Sorting (trending, latest).  
   * Likes/reactions (if available).  
   * Navigating to individual public item pages.  
10. **Content moderation and NSFW filters**  
    * Blocking prompts containing forbidden keywords (stop‑words).  
    * Showing clear messages to the user when a prompt is blocked.  
    * Marking “sensitive / NSFW content”.  
    * Interface behavior when accessing sensitive content (warnings, hiding by default, etc.).  
11. **Admin part**   
    * Admin login.  
    * Viewing and searching users (by email, username, status).  
    * Blocking/unblocking users.  
    * Viewing user content reports.  
    * Basic analytics:  
      * new users count;  
      * number of generations (image/video);  
      * average generation time;  
      * credit usage statistics.  
12. **UI/UX, responsiveness and localization**  
    * Compliance with design mockups (Figma).  
    * Correct behavior on:  
      * desktop web(Full HD and above);  
      * tablet web;  
      * mobile web.  
    * Correct operation in supported browsers.  
    * Language switching (if more than one language is supported).  
    * No mixed languages, truncated texts, or broken layouts.

## 2.2. Out of scope

* Native mobile applications (iOS/Android).  
* Full‑scale security/penetration testing.  
* Full‑scale performance/load testing (stress, soak).  
* Evaluation of artistic quality of AI output (only basic checks that files are generated and can be opened).

## 2.3. Assumptions and Constraints

Assumptions:

* Testing is performed only on the web version (desktop and mobile web); there are no native mobile apps in the current scope.  
* The test environment (staging) is functionally equivalent to production in terms of features and configuration, except for integrations that are explicitly mocked or sandboxed (payments, AI models).  
* All required third‑party integrations (payment gateway sandbox, AI providers) are available and stable enough for testing.

Constraints:

* Limited QA resources (1–2 QA engineers) and tight deadlines may require risk‑based prioritization of test execution.  
* Performance and security are covered only by basic sanity checks; full‑scale non‑functional testing is out of scope for this phase.  
* Testing is performed in a single locale (e.g. English) unless otherwise agreed; full multi‑language coverage is not guaranteed at this stage.

# 3. Work plan

1. Prepare and approve the Test Plan.  
2. Analyze requirements and define main user flows (user side \+ admin side).  
3. Create test cases in TestRail.  
4. Set up the test environment:  
   * test/staging environment;  
   * test accounts (Free, Pro, Admin);  
   * integration with payment sandbox.

## 3.1. Test Cycle 1 – MVP

Scope:

* Registration & Authentication (registration, login, logout, password recovery).  
* User profile (view/edit, password change, account deletion).  
* Billing & credits:  
  * displaying plans;  
  * basic credit purchase via payment sandbox;  
  * credit deduction for image generation.  
* Basic image generation (styles, single image, core parameters).  
* User gallery: list, item view, basic download.  
* Minimal admin functionality:  
  * admin login;  
  * view/search users;  
  * block/unblock users.  
* Content moderation and NSFW filters.

Activities:

* Execute all test cases within this scope.  
* Log defects in Jira; provide short daily status updates.  
* Retest fixed defects and run targeted regression on affected areas.

## 3.2. Test Cycle 2 – Extended features

Scope:

* Video generation.  
* Advanced generation options (multiple variants, prompt history).  
* Limits and queues (per‑user concurrent jobs, daily/monthly limits).  
* Public links and sharing.  
* Global gallery / Explore.  
* Extended admin features:  
  * content reports;  
  * basic analytics (user and generation stats).

Activities:

* Execute test cases for extended scope.  
* Log defects in Jira; provide daily status updates.  
* Retest fixed defects from Cycle 2\.  
* Run regression suite on all critical user and admin flows.

## 3.3. Pre-release regression and reporting

* Run full regression on all critical flows (user \+ admin \+ billing) before the MVP release.  
* Validate production configuration (smoke tests after deployment, if in scope).  
* Prepare and deliver the final Test Summary Report.

## 3.4. QA Effort and Schedule

* QA team: 1 QA Engineer (full‑time) \+ QA Tech Lead (part‑time for coordination and reviews).  
* Planned duration:  
  * Test Cycle 1 – MVP: \~3 weeks (including test design, execution, retesting).  
  * Test Cycle 2 – Extended features: \~3 weeks.  
  * Pre‑release regression and reporting: \~1 week.  
* Exact dates and scope per cycle will be aligned with the development plan and may be adjusted based on actual progress and risks.

# 4. Test Approach

## 4.1. Types of testing

The following types of testing are planned:

* **Functional Testing**  
  Verification of all business functions: registration, profile, generation, billing, gallery, sharing, moderation, admin panel.  
* **UI Testing**  
  Layout correctness, consistency with designs, responsive behavior.  
* **Usability Testing**  
  Verifying clarity and simplicity of critical flows from entering a prompt to receiving and downloading the result.  
* **Compatibility Testing**  
  Verification on supported desktop and mobile web browsers.  
* **Regression Testing**  
  Ensuring no regressions after changes and bug fixes.  
* **Retesting**  
  Verifying fixes for previously reported defects.

Not planned in this phase:

* full Security Testing;  
* full Performance/Load Testing.

## 4.2. Functional testing: objective, technique, entry/exit criteria

**Objective**

Ensure that the Cinelora AI web application conforms to requirements and has no significant defects in main user scenarios.

**Technique**

* Execute all use cases with valid and invalid data to verify:  
  * expected behavior with valid input;  
  * proper error messages and handling with invalid input;  
  * correct application of business rules (limits, billing, roles, moderation).

**Entry Criteria**

* Functionality planned for the current test cycle is implemented and deployed to the test environment.  
* Test environment (test/staging) is prepared; all required accesses are provided.  
* Required devices/browsers are available to the QA team.  
* Test cases for the current scope are created and reviewed in TestRail.  
* Integrations with external services (payments, AI API) are working in test mode.

**Exit Criteria**

* All planned test cases for the current cycle have been executed.  
* No blocking / critical defects remain in key flows:  
  * registration / login;  
  * prompt creation;  
  * image/video generation;  
  * viewing and downloading media;  
  * purchasing credits/plan.  
* All high‑severity, high‑priority defects are fixed or have an agreed workaround.  
* Test results are reviewed and accepted by responsible stakeholders (PM, Tech Lead).

## 4.3. Test procedure

* Prepare and maintain test cases in TestRail.  
* Execute tests based on priority (critical flows first).  
* Log all found defects in Jira.  
* Update test case results in TestRail daily (Passed / Failed / Blocked / Not run).  
* Participate in stand‑ups, clarify requirements, help with defect prioritization.  
* Perform retesting of fixed defects.  
* Execute regression testing before release.

# 5. Test Data

* **Payments**  
  * Use payment provider test cards (e.g., Stripe test cards) to verify:  
    * successful payments;  
    * declined payments;  
    * 3DS/additional authentication;  
    * refunds/cancellations.  
* **Content generation**  
  * A set of reference positive prompts (different styles, lengths, types).  
  * A set of negative prompts / stop‑words for NSFW filter and forbidden content tests.  
  * A set of prompts for limit tests (bulk generation, concurrent jobs).  
* **Accounts**  
  * Standard test accounts:  
    * Free user (no subscription);  
    * Pro user (active subscription/credits);  
    * User with zero credits;  
    * Admin user (for admin panel).

# 6. Bug Reports

## 6.1. Defect severity

Defect severity is classified as follows:

* **Critical (Blocker)**  
  * Complete system or critical subsystem failure.  
  * Inability to execute key flows (login, generation, payment, download).  
  * Data loss or inconsistent database state.  
* **Major**  
  * Serious failures in essential functionality where a workaround exists, but user experience is significantly degraded.  
  * Crashes in non‑critical flows.  
* **Minor**  
  * Incorrect/incomplete results that do not block main flows.  
* **Trivial**  
  * Small UI issues, typos, minor visual differences from design.

## 6.2. Defect priority

* **High** – impact the business in a big way; need immediate attention and must be addressed as soon as possible.  
* **Medium** – moderate/low impact on business; can be fixed in an upcoming release.  
* **Low** – negligible impact on business; can be fixed when higher‑priority work is done.

## 6.3. Bug report content

Each bug report in Jira should contain:

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

# 7. Criteria of quality

The product is considered ready for release if:

* The actual behavior matches the approved requirements and functional specification.  
* No critical or blocking defects remain in the release build.  
* Core user flows are stable:  
  * registration, login, password recovery;  
  * image/video prompt creation;  
  * media generation, viewing, downloading;  
  * credit/plan purchase and deduction;  
  * public links and basic moderation.

**Coverage criteria**

* 100% of planned test cases for critical functionality must be executed (registration/login, password recovery, image/video generation, billing & credits, media download, public links, basic moderation, admin login and user blocking/unblocking).  
* At least 80% of planned test cases for non‑critical functionality must be executed before release (secondary filters/sorting, non‑essential profile settings, non‑critical UI improvements).  
* All failed test cases must have a corresponding defect logged in Jira or a documented reason for deviation (e.g. test case obsolete).

# 8. Testing process risks

**Testing process risks**  
**Risk:** Unplanned changes in functionality or architecture without prior QA involvement.  
 Mitigation: Enforce change management via Jira; any scope change must be reflected in tickets and discussed on daily/weekly meetings before implementation.

**Risk:** Requirement changes without updating documentation.  
 Mitigation: Require update of PRD / user stories as a pre‑condition for test case updates; track gaps via QA comments in Jira.

**Risk:** Delays in fixing critical defects.  
 Mitigation: Escalate blockers in daily status reports; involve PM/Tech Lead to re‑prioritize work and adjust release scope if needed.

**Risk:** Delays in delivering new builds to the test environment.  
 Mitigation: Agree build schedule in advance; set a minimal cadence (e.g. at least 2 builds per week) and smoke‑test gates.

**Risk:** Instability of external services (AI providers, payment gateways).  
 Mitigation:

* Use sandbox/test environments wherever possible.  
* Prepare fallback test scenarios (mocked responses, retry logic tests).  
* Reserve buffer time in the schedule for re‑runs after outages.

**AI‑specific risk:** Staging vs Production AI models may use different configurations; staging behavior may not fully represent production behavior (especially performance‑related).  
 Mitigation:

* Treat all performance‑related findings on staging as indicative, not final.  
* Run a limited set of smoke/performance checks on production after release (if allowed).  
* Document known differences between staging and production models.

**Risk:** Limited QA resources (small team, tight deadlines).  
 Mitigation: Apply risk‑based test prioritization (critical flows first); reduce coverage on low‑risk areas if required to meet deadlines, with explicit sign‑off from PM/PO.

# 9. Test team expectations

The QA team expects:

* Up‑to‑date and complete documentation (requirements, designs, API specs).  
* Prepared and maintained test environment and accounts before test start.  
* Prompt fixing of blocking/critical defects.  
* Release Notes for each new build, including list of changes and known issues.  
* Minimal last‑minute changes without prior QA review.

# 10. Responsibilities

**Project Manager / Product Owner**

* Plan releases and sprints.  
* Prioritize features and bug fixes.  
* Provide resources for testing.

**QA Tech Lead** 

* Define testing approaches, tools, and processes.  
* Analyze risks.  
* Distribute QA tasks.  
* Coordinate with development and PM.

**QA Engineer**

* Analyze requirements.  
* Prepare test documentation (test cases, checklists, test plan).  
* Execute tests, log defects in Jira.  
* Maintain test status in TestRail.  
* Prepare interim and final test reports.

# 11. Resources

## 11.1. Tools

| Tool | Comment |
| ----- | ----- |
| Jira | Defect tracking |
| TestRail / Google Sheets | Test case management |
| Teams / e‑mail | Daily communication and status |
| Browser DevTools | Layout checks and technical analysis |
| Figma | Checking UI against design mockups |
| Postman / DB tools | Specific API/DB checks |
| OS/browser built‑in tools, Snagit/Loom | Screenshots and video capture |

## 11.2. Browsers list

| Browser | Version |
| ----- | ----- |
| Chrome | Latest |
| Firefox | Latest |
| Edge | Latest |
| Safari | Latest |

## 11.3. Devices (web only)

| Device type | OS |
| ----- | ----- |
| Desktop | Windows 10/11, macOS |
| Mobile web | Current iOS and Android OS |

# 12. Deliverables

* Test Plan.  
* Test cases set in TestRail.  
* Bug reports in Jira.  
* Daily/weekly test progress reports.  
* Final Test Summary Report before MVP release.

	
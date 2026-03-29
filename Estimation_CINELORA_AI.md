# Project Estimation: CINELORA AI (MVP Cycle 1)

---

## 1. Registration & Authorization
| № | FUNCTIONALITY | Opt. (min) | Pess. (min) | Opt. Add. (min) | Pess. Add. (min) |
| :--- | :--- | :---: | :---: | :---: | :---: |
| **1.1** | **Registration flow** | | | | |
| 1.1.1 | Registration – required fields check (all mandatory fields marked and validated as required) | 3 | 5 | 3 | 5 |
| 1.1.2 | Registration – fields validation (email format, password length/complexity, disallowed characters) | 10 | 15 | 10 | 15 |
| 1.1.3 | Registration with already used e-mail (shows "email already in use", account not created) | 5 | 7 | 5 | 7 |
| 1.1.4 | Registration with / without accepted Terms & Privacy (checkbox required, links redirect to correct pages) | 6 | 8 | 6 | 8 |
| 1.1.5 | Registration with valid data (successful sign-up, redirect to email verification screen) | 5 | 7 | 5 | 7 |
| 1.1.6 | Registration with invalid data (combination of wrong email, weak password, empty fields – correct error messages) | 8 | 12 | 8 | 12 |
| 1.1.7 | Email verification – verification email is sent after registration (check content/link correctness) | 10 | 15 | 10 | 15 |
| 1.1.8 | Email verification – following verification link activates account and allows login | 4 | 7 | 4 | 7 |
| 1.1.9 | Email verification – expired/used link shows proper error, does not activate account | 4 | 6 | 4 | 6 |
| **1.2** | **Authorization flow** | | | | |
| 1.2.1 | Login with valid credentials (user lands on dashboard) | 2 | 4 | 2 | 4 |
| 1.2.2 | Login with invalid password / non-existing e-mail (error message, no access) | 3 | 5 | 3 | 5 |
| 1.2.3 | Login of unverified user (login blocked until email verified, proper message shown) | 3 | 5 | 3 | 5 |
| 1.2.4 | "Remember me" functionality – session persists after browser restart when enabled | 3 | 5 | 3 | 5 |
| 1.2.5 | Session expiration – after token/session expiry user is redirected to login, protected pages not accessible | 5 | 8 | 5 | 8 |
| 1.2.6 | Logout – user is logged out and cannot access protected pages via direct URL or Back button | 3 | 5 | 3 | 5 |
| 1.2.7 | Multiple sessions – login from second device/browser behaves according to requirements (no unexpected logout) | 7 | 12 | 7 | 12 |
| **1.3** | **Password recovery** | | | | |
| 1.3.1 | Open "Forgot password" page/modal from login screen (UI elements, navigation) | 2 | 4 | 2 | 4 |
| 1.3.2 | Forgot password with existing e-mail – reset email is sent, confirmation message shown | 8 | 10 | 8 | 10 |
| 1.3.3 | Forgot password with non-existing e-mail – friendly message, no information leak about account existence | 5 | 7 | 5 | 7 |
| 1.3.4 | Open reset link from email – reset password page opens correctly (valid token and correct user) | 8 | 12 | 8 | 12 |
| 1.3.5 | New password validation – min length, complexity, confirmation match, proper error messages | 8 | 10 | 8 | 10 |
| 1.3.6 | Successful password change – user can log in with new password, old password no longer works | 8 | 12 | 8 | 12 |
| 1.3.7 | Reset link invalid/expired – user sees correct error and cannot change password | 8 | 12 | 8 | 12 |
| **1.4** | **Rate limiting** | | | | |
| 1.4.1 | Login rate limiting – several failed attempts trigger CAPTCHA/lock or delay (correct message shown) | 12 | 16 | 12 | 16 |
| 1.4.2 | Login rate limiting – after waiting/unlock user can successfully log in with valid credentials | 8 | 12 | 8 | 12 |
| 1.4.3 | Forgot password rate limiting – repeated requests from same email/IP are limited with proper message | 10 | 14 | 10 | 14 |
| **1.5** | **Additional negative/edge cases** | | | | |
| 1.5.1 | Registration / login with leading/trailing spaces in email (trimming, correct handling) | 5 | 7 | 5 | 7 |
| 1.5.2 | Registration / login with different email case (UPPER/lower) – case-insensitive comparison | 5 | 7 | 5 | 7 |
| 1.5.3 | Access protected page without authentication – redirect to login and back to target page after login | 6 | 8 | 6 | 8 |
| 1.5.4 | Direct access to login/registration when already logged in – redirect to dashboard according to requirements | 5 | 7 | 5 | 7 |

## 2. User Profile
| № | FUNCTIONALITY | Opt. | Pess. | Opt. Add. | Pess. Add. |
| :--- | :--- | :---: | :---: | :---: | :---: |
| **2.1** | **View profile** | | | | |
| 2.1.1 | View profile: name/username, email, avatar, registration date are displayed correctly | 4 | 6 | 4 | 6 |
| 2.1.2 | Profile data consistency: username/avatar in header, profile page and gallery are synchronized | 5 | 7 | 5 | 7 |
| **2.2** | **Edit profile** | | | | |
| 2.2.1 | Open profile edit form from header/profile page | 2 | 4 | 2 | 4 |
| 2.2.2 | Edit username: change username, save, updated value shown on profile, header and gallery items | 5 | 7 | 5 | 7 |
| 2.2.3 | Username validation: cannot be empty or exceed max length, clear error messages shown | 8 | 12 | 8 | 12 |
| 2.2.4 | Change avatar: upload valid image (supported formats/sizes), avatar is updated on profile and header | 8 | 12 | 8 | 12 |
| 2.2.5 | Avatar upload invalid file (unsupported format/too large) – upload rejected, error shown, old avatar kept | 5 | 8 | 5 | 8 |
| 2.2.6 | Cancel editing: changes discarded after Cancel/back, old data remains | 4 | 6 | 4 | 6 |
| **2.3** | **Language & theme** | | | | |
| 2.3.1 | Change interface language in profile settings: UI texts updated after reload/login | 8 | 12 | 8 | 12 |
| 2.3.2 | Switch theme to Dark mode: dark theme applied across main pages and persists after reload/login | 5 | 7 | 5 | 7 |
| 2.3.3 | Switch theme back to Light mode: light theme applied correctly, persists after reload/login | 5 | 7 | 5 | 7 |
| **2.4** | **Default generation settings** | | | | |
| 2.4.1 | Set default generation parameters (type, size, style) in profile and save | 5 | 7 | 5 | 7 |
| 2.4.2 | Open Prompt creation: default parameters from profile are pre-filled in form | 4 | 6 | 4 | 6 |
| 2.4.3 | Change defaults and verify that new prompts use updated defaults | 5 | 7 | 5 | 7 |
| 2.4.4 | Reset to system defaults: default parameters return to initial values | 5 | 7 | 5 | 7 |
| **2.5** | **Change password** | | | | |
| 2.5.1 | Open "Change password" section (current/new/confirm fields visible) | 2 | 4 | 2 | 4 |
| 2.5.2 | Change password with valid current password and valid new password, login with new password | 8 | 12 | 8 | 12 |
| 2.5.3 | New password validation: too short/weak password or mismatch with confirmation shows clear errors | 8 | 12 | 8 | 12 |
| 2.5.4 | Incorrect current password: password is not changed, clear error message is shown | 5 | 7 | 5 | 7 |
| 2.5.5 | "Show/hide password" toggles for password fields work correctly | 3 | 5 | 3 | 5 |
| **2.6** | **Account deletion** | | | | |
| 2.6.1 | Open account deletion flow (confirmation modal appears) | 4 | 6 | 4 | 6 |
| 2.6.2 | Deletion confirmation message: clear warning about data loss and irreversibility before final action | 4 | 6 | 4 | 6 |
| 2.6.3 | Confirm account deletion: account removed, user logged out and cannot log in anymore with old credentials | 8 | 12 | 8 | 12 |
| 2.6.4 | Try to access protected pages after deletion (via direct URL or saved session) – access is denied | 8 | 12 | 8 | 12 |

## 3. Plans, Billing and Credits
| № | FUNCTIONALITY | Opt. | Pess. | Opt. Add. | Pess. Add. |
| :--- | :--- | :---: | :---: | :---: | :---: |
| **3.1** | **Display plans & current status** | | | | |
| 3.1.1 | Display available pricing plans (Free / Pro ) with limits and main features | 5 | 7 | 5 | 7 |
| 3.1.2 | Plan details: for each plan show correct limits for image generation and basic constraints | 8 | 12 | 8 | 12 |
| 3.1.3 | Show current credits / subscription status for logged-in user in billing widget or profile | 5 | 7 | 5 | 7 |
| 3.1.4 | Billing page unauthorized access: logged-out user is redirected to login/registration | 4 | 6 | 4 | 6 |
| **3.2** | **Successful purchase (credit pack / subscription)** | | | | |
| 3.2.1 | Open billing/purchase page: plans and available payment options are loaded without errors | 4 | 6 | 4 | 6 |
| 3.2.2 | Successful purchase of credit pack via payment gateway sandbox: credits are added to balance | 10 | 15 | 10 | 15 |
| 3.2.3 | Successful activation of Pro plan subscription: status and limits are updated accordingly | 10 | 15 | 10 | 15 |
| 3.2.4 | Purchase confirmation UI: show success message and updated balance/status on billing and profile widgets | 5 | 7 | 5 | 7 |
| **3.3** | **Failed/declined payment** | | | | |
| 3.3.1 | Failed payment (declined card in sandbox): clear error is shown, no credits are added | 8 | 12 | 8 | 12 |
| 3.3.2 | Purchase attempt with invalid payment data (wrong/expired card): payment is declined, clear error | 8 | 12 | 8 | 12 |
| 3.3.3 | No double charges on retry: user can retry after failure, single successful payment adds credits only once | 10 | 15 | 10 | 15 |
| **3.4** | **Credit consumption** | | | | |
| 3.4.1 | Credit deduction for single image generation: correct number of credits is subtracted after success | 8 | 12 | 8 | 12 |
| 3.4.2 | Multiple image generations in a row: total deducted credits equal sum of all successful jobs | 10 | 15 | 10 | 15 |
| 3.4.3 | No deduction for failed image generation: if job fails, credits are not subtracted | 8 | 12 | 8 | 12 |
| **3.5** | **Transaction history** | | | | |
| 3.5.1 | Transaction history: list of purchases shows date, amount, status and payment method | 5 | 7 | 5 | 7 |
| 3.5.2 | Transaction history sorting by date (newest/oldest) works correctly | 5 | 7 | 5 | 7 |
| 3.5.3 | Transaction history filters by status (success/failed) show correct subsets | 5 | 7 | 5 | 7 |
| 3.5.4 | Unauthorized access to transaction history redirects to login/registration | 4 | 6 | 4 | 6 |
| **3.6** | **Subscription management** | | | | |
| 3.6.1 | Activate Pro plan: plan status changes to active, limits updated, billing next renewal date shown | 8 | 12 | 8 | 12 |
| 3.6.2 | Subscription cancellation: cancel Pro plan, next renewal date is removed, user is informed | 8 | 12 | 8 | 12 |
| 3.6.3 | UI reflects cancelled status: user sees correct plan (Free) and updated limits | 5 | 7 | 5 | 7 |
| **3.7** | **Zero balance and transaction blocking** | | | | |
| 3.7.1 | Generation attempt with zero credits: user cannot start generation, informative message is shown | 5 | 7 | 5 | 7 |
| 3.7.2 | After purchasing credits, generation with the same account becomes possible without reload issues | 5 | 7 | 5 | 7 |
| 3.7.3 | UI indicators for low/zero credits: warning or disabled actions are displayed correctly | 5 | 7 | 5 | 7 |

## 4. Basic Image Generation
| № | FUNCTIONALITY | Opt. | Pess. | Opt. Add. | Pess. Add. |
| :--- | :--- | :---: | :---: | :---: | :---: |
| **4.1** | **Prompt creation page** | | | | |
| 4.1.1 | Open prompt creation page from main navigation or CTA button, page loads without errors | 3 | 5 | 3 | 5 |
| 4.1.2 | Prompt form initial state: default generation type = Image, required controls visible | 5 | 7 | 5 | 7 |
| 4.1.3 | Navigation from other pages (dashboard/gallery) to prompt creation works correctly | 4 | 6 | 4 | 6 |
| **4.2** | **Main text prompt** | | | | |
| 4.2.1 | Main text prompt is required: empty prompt cannot be submitted, validation message is shown | 5 | 7 | 5 | 7 |
| 4.2.2 | Prompt length validation: too short prompt (e.g. 1–2 characters) is rejected with clear error | 5 | 7 | 5 | 7 |
| 4.2.3 | Prompt length validation: too long prompt above maximum length is blocked or truncated | 8 | 12 | 8 | 12 |
| 4.2.4 | Invalid characters: prompt with unsupported characters/script tags is rejected with safe error | 8 | 12 | 8 | 12 |
| **4.3** | **Generation parameters** | | | | |
| 4.3.1 | Generation mode in Cycle 1: prompt form configured for Image generation only | 3 | 5 | 3 | 5 |
| 4.3.2 | Style selection: user can select style (realistic, anime, 3D, cinematic, etc.) | 5 | 7 | 5 | 7 |
| 4.3.3 | Size / aspect ratio selection for image: allowed options selectable | 5 | 7 | 5 | 7 |
| 4.3.4 | Number of variants (1–4) for image: user can choose allowed values | 5 | 7 | 5 | 7 |
| 4.3.5 | Seed control: user can choose between fixed and random seed | 8 | 12 | 8 | 12 |
| **4.4** | **Prompt templates & history** | | | | |
| 4.4.1 | Prompt templates (presets): selecting a preset fills prompt fields according to template | 8 | 12 | 8 | 12 |
| 4.4.2 | Switching between different templates updates fields correctly, no stale values left | 8 | 12 | 8 | 12 |
| 4.4.3 | Prompt history: last prompts are shown in history list, user can reopen and reuse them | 10 | 15 | 10 | 15 |
| 4.4.4 | History entry reuse: selecting item from history pre-fills fields and allows new generation | 8 | 12 | 8 | 12 |
| 4.4.5 | Prompt form respects default generation settings from profile | 5 | 7 | 5 | 7 |
| 4.4.6 | Change defaults in profile and reopen prompt form: new defaults are applied correctly | 5 | 7 | 5 | 7 |
| 4.4.7 | Reset to system defaults (if supported): prompt form uses system defaults after reset | 5 | 7 | 5 | 7 |
| **4.5** | **Submit prompt & Queue** | | | | |
| 4.5.1 | Submit prompt with valid data: clicking Generate sends request and navigates to queue | 5 | 7 | 5 | 7 |
| 4.5.2 | Submit button disabled while request is in progress (no duplicate submissions) | 4 | 6 | 4 | 6 |
| 4.5.3 | Error handling: if backend returns validation error for prompt, server message is shown | 8 | 12 | 8 | 12 |
| 4.5.4 | Send image generation request: job is created and appears in user's queue | 8 | 12 | 8 | 12 |
| 4.5.5 | Newly created image job has initial status "queued" and shows basic info | 5 | 7 | 5 | 7 |
| 4.5.6 | While generation is in progress, job status changes from "queued" to "processing" | 8 | 12 | 8 | 12 |
| 4.5.7 | After successful image generation, job status becomes "succeeded" and preview is shown | 5 | 7 | 5 | 7 |
| 4.5.8 | In case of image generation error, job status becomes "failed" and user sees error message | 8 | 12 | 8 | 12 |
| 4.5.9 | Open item details from queue: click on succeeded job opens item details page/modal | 5 | 7 | 5 | 7 |
| 4.5.10 | Queue refresh behavior: new jobs and status updates appear without hard page reload | 8 | 12 | 8 | 12 |
| 4.5.11 | Queue shows only current user's jobs; jobs from other users are not visible | 5 | 7 | 5 | 7 |
| 4.5.12 | Basic sorting in queue (e.g. newest first) works correctly | 5 | 7 | 5 | 7 |

## 5. User Gallery
| № | FUNCTIONALITY | Opt. | Pess. | Opt. Add. | Pess. Add. |
| :--- | :--- | :---: | :---: | :---: | :---: |
| **5.1** | **Gallery list / grid** | | | | |
| 5.1.1 | Open "My creations" gallery page: list/grid of user items is displayed without errors | 3 | 5 | 3 | 5 |
| 5.1.2 | Thumbnails for image items: small previews are visible, no broken/missing images | 5 | 7 | 5 | 7 |
| 5.1.3 | Gallery shows only items of current user; items of other users are not visible | 5 | 7 | 5 | 7 |
| 5.1.4 | Basic empty state: when user has no items, friendly empty state message and CTA are shown | 5 | 7 | 5 | 7 |
| **5.2** | **Filters & Sorting** | | | | |
| 5.2.1 | Filter by date (e.g. Today / Last 7 days / Custom range) shows only items within selected period | 8 | 12 | 8 | 12 |
| 5.2.2 | Filter by style (realistic, anime, 3D, cinematic, etc.): only items with selected style are shown | 8 | 12 | 8 | 12 |
| 5.2.3 | Clearing filters resets gallery to default view with all applicable items | 5 | 7 | 5 | 7 |
| 5.2.4 | Sorting by "Newest first": latest creations appear at the top of the list/grid | 5 | 7 | 5 | 7 |
| 5.2.5 | Sorting by "Oldest first": oldest creations appear at the top of the list/grid | 5 | 7 | 5 | 7 |
| **5.3** | **Search by prompt text** | | | | |
| 5.3.1 | Search by full prompt text returns only items with exact prompt match | 5 | 7 | 5 | 7 |
| 5.3.2 | Search by partial text returns items where prompt contains the entered substring | 5 | 7 | 5 | 7 |
| 5.3.3 | Search with no matches shows empty state message (no results) | 4 | 6 | 4 | 6 |
| **5.4** | **Pagination** | | | | |
| 5.4.1 | Pagination / infinite scroll loads next portion of items without duplicates or gaps | 8 | 12 | 8 | 12 |
| 5.4.2 | Navigating between pages or loading more keeps selected filters and sorting | 8 | 12 | 8 | 12 |
| **5.5** | **Item details** | | | | |
| 5.5.1 | Open item details from gallery: clicking on image thumbnail opens details page or modal | 5 | 7 | 5 | 7 |
| 5.5.2 | Full-size image is displayed correctly in details view without distortion | 5 | 7 | 5 | 7 |
| 5.5.3 | Metadata in details view shows prompt text | 5 | 7 | 5 | 7 |
| 5.5.4 | Metadata shows style, size/aspect ratio, generation type=Image and created date/time | 5 | 7 | 5 | 7 |
| 5.5.5 | Navigating back from item details returns user to correct position in list/grid | 8 | 12 | 8 | 12 |
| 5.5.6 | Unauthorized access: trying to open item of another user directly by URL is not allowed | 8 | 12 | 8 | 12 |
| **5.6** | **Download** | | | | |
| 5.6.1 | Download image as .png from item details: file is downloaded, opens correctly | 5 | 7 | 5 | 7 |
| 5.6.2 | Download button disabled or shows error for unavailable/broken media | 8 | 12 | 8 | 12 |

## 6. Admin Part
| № | FUNCTIONALITY | Opt. | Pess. | Opt. Add. | Pess. Add. |
| :--- | :--- | :---: | :---: | :---: | :---: |
| **6.1** | **Admin login & access** | | | | |
| 6.1.1 | Admin login with valid credentials opens admin dashboard | 3 | 5 | 3 | 5 |
| 6.1.2 | Admin login with invalid password shows error message and does not grant access | 3 | 5 | 3 | 5 |
| 6.1.3 | Unauthorized user (non-admin) cannot access admin URL; is redirected or sees "Access denied" | 5 | 7 | 5 | 7 |
| 6.1.4 | Session handling: after admin logout, protected admin pages are not accessible | 5 | 7 | 5 | 7 |
| **6.2** | **Users list** | | | | |
| 6.2.1 | Users list: admin can see paginated list of users with basic info | 5 | 7 | 5 | 7 |
| 6.2.2 | Users list pagination: switching pages shows correct subsets, no duplicates or gaps | 8 | 12 | 8 | 12 |
| 6.2.3 | Users list initial sorting (e.g. newest first) is applied correctly | 5 | 7 | 5 | 7 |
| **6.3** | **Search and filter users** | | | | |
| 6.3.1 | Search users by email returns correct results | 5 | 7 | 5 | 7 |
| 6.3.2 | Search users by username returns correct results | 5 | 7 | 5 | 7 |
| 6.3.3 | Search with no matches shows empty state (no results) | 4 | 6 | 4 | 6 |
| 6.3.4 | Filter users by status (active/blocked) shows only users with selected status | 5 | 7 | 5 | 7 |
| 6.3.5 | Clearing search and filters resets list to default view | 4 | 6 | 4 | 6 |
| **6.4** | **Block / unblock users** | | | | |
| 6.4.1 | Block user: admin can change user status to "blocked" in users list or details view | 5 | 7 | 5 | 7 |
| 6.4.2 | After blocking, user cannot log in to user portal anymore | 8 | 12 | 8 | 12 |
| 6.4.3 | Blocked users are clearly indicated in users list (status column, badge/icon) | 5 | 7 | 5 | 7 |
| 6.4.4 | Unblock user: admin can change status back to "active" | 5 | 7 | 5 | 7 |
| 6.4.5 | After unblocking, user can successfully log in again | 8 | 12 | 8 | 12 |
| **6.5** | **User details** | | | | |
| 6.5.1 | Open user details from users list: admin sees basic profile info | 5 | 7 | 5 | 7 |
| 6.5.2 | User details show current plan/credits and recent activity summary | 8 | 12 | 8 | 12 |

## 7. Content Moderation & NSFW Filters
| № | FUNCTIONALITY | Opt. | Pess. | Opt. Add. | Pess. Add. |
| :--- | :--- | :---: | :---: | :---: | :---: |
| **7.1** | **Prompt blocking** | | | | |
| 7.1.1 | Prompt with single forbidden keyword is blocked before sending to AI; clear message | 8 | 12 | 8 | 12 |
| 7.1.2 | Prompt with combination of risky words is blocked according to rules | 8 | 12 | 8 | 12 |
| 7.1.3 | Borderline but allowed prompt (artistic nudity / mild violence) is NOT blocked | 8 | 12 | 8 | 12 |
| 7.1.4 | Blocked prompts are not sent to AI provider: no job is created and no credits deducted | 10 | 15 | 10 | 15 |
| **7.2** | **NSFW classification and content labels** | | | | |
| 7.2.1 | AI output that is classified as NSFW/sensitive is marked in metadata and UI | 8 | 12 | 8 | 12 |
| 7.2.2 | Non‑NSFW output is not marked as NSFW; labels are consistent | 5 | 7 | 5 | 7 |
| **7.3** | **NSFW in User Gallery** | | | | |
| 7.3.1 | NSFW items in User gallery are visually marked (badge/icon) and blurred by default | 8 | 12 | 8 | 12 |
| 7.3.2 | Reveal action: user can explicitly reveal NSFW item in gallery with one click/tap | 5 | 7 | 5 | 7 |
| 7.3.3 | Hide back: user can hide NSFW thumbnail again (blur returns) | 5 | 7 | 5 | 7 |
| 7.3.4 | Non‑NSFW items are always shown without blur or NSFW labels | 4 | 6 | 4 | 6 |
| **7.4** | **NSFW in item details (User side)** | | | | |
| 7.4.1 | When opening NSFW item details from gallery, user first sees NSFW warning screen | 8 | 12 | 8 | 12 |
| 7.4.2 | User must confirm (e.g. "I understand / View anyway") before content is shown | 5 | 7 | 5 | 7 |
| 7.4.3 | Cancel/Back on warning screen does not show NSFW content | 5 | 7 | 5 | 7 |
| 7.4.4 | Non‑NSFW item details open directly without extra NSFW warning | 4 | 6 | 4 | 6 |
| **7.5** | **User reporting (Report inappropriate content)** | | | | |
| 7.5.1 | "Report" action available in item details (user gallery) | 5 | 7 | 5 | 7 |
| 7.5.2 | Report dialog opens with list of reasons and optional comment field | 8 | 12 | 8 | 12 |
| 7.5.3 | Submitting report with selected reason succeeds; user sees confirmation message | 8 | 12 | 8 | 12 |
| **7.6** | **Displaying reports in the admin panel** | | | | |
| 7.6.1 | Reported items appear in admin "Content reports" list with reporter, reason, date | 8 | 12 | 8 | 12 |
| 7.6.2 | Admin can open reported item from content reports list | 5 | 7 | 5 | 7 |
| **7.7** | **Admin moderation decisions** | | | | |
| 7.7.1 | Admin can mark report as "Allowed": item stays visible, report disappears | 8 | 12 | 8 | 12 |
| 7.7.2 | Admin can mark reported item as "NSFW": item becomes NSFW (blur, warnings) | 10 | 15 | 10 | 15 |
| 7.7.3 | Admin can mark reported item as "Removed": item is hidden from gallery | 10 | 15 | 10 | 15 |
| 7.7.4 | Moderation decisions are reflected in user UI (NSFW badge/blur or missing content) | 8 | 12 | 8 | 12 |

---

## Final Summary Table
| Metric | Optimistic | Pessimistic |
| :--- | :--- | :--- |
| **Duration on Chrome (Main)** | 17.4 h | 25.5 h |
| **Duration on 3 Add. Browsers (50% scope/CP)** | 26.1 h | 38.3 h |
| **Management & Organization (10%)** | 4.4 h | 6.4 h |
| **TOTAL PROJECT DURATION** | **47.9 h** | **70.2 h** |
| **Hourly Rate** | $20.0 | $20.0 |
| **TOTAL ESTIMATED BUDGET** | **$958.0** | **$1,404.0** |

## Browser Compatibility Scope
1. **Chrome** (Latest) - Full Suite
2. **Firefox** (Latest) - Critical Path
3. **Edge** (Latest) - Critical Path
4. **Safari** (Latest) - Critical Path
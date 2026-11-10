# Student Spending Initiative — Carolina Food Connect

A Carolina-blue, login-first front-end prototype with separate Student, Business, and Campus Admin portals.

## Run it
1. Download and unzip this project.
2. Open `login.html` in a browser, or use VS Code Live Server for a smoother local preview.
3. Use one of the demo accounts below.

## Demo accounts
- Student: `student@unc.edu` / `Carolina123`
- Business: `business@example.com` / `Carolina123`
- Campus Admin: `admin@unc.edu` / `Carolina123`

You can also create a demo account from `signup.html`. Demo account data is stored in that browser's `localStorage`.

## Important security limitation
This is a **front-end class prototype**, not production authentication. The demo login is only a visual/functional simulation:
- It does not authenticate Google or Microsoft accounts.
- It does not verify UNC Onyen or student status.
- Browser `localStorage` is not secure and must not hold real credentials or sensitive student information.
- Front-end role checks can be bypassed; they are not authorization.
- The five-failed-attempt / 15-minute lockout rule is not implemented as a security control here.

Before real deployment, connect a backend and database, use a supported identity provider (confirm UNC's approved SSO/OIDC/SAML configuration with UNC IT), and enforce authentication, authorization, password policy, rate limiting, and account lockouts on the server. Use least-privilege roles and audit access. Admin views in this prototype show graduation year, meal-plan enrollment, and swipe information only—not individual food spending. Business analytics are aggregate deal views/redemptions only.

## Structure
- `login.html`, `signup.html` — entry and account creation
- `student/index.html` — student dashboard and features
- `business/index.html` — business dashboard, deals, and aggregate analytics
- `admin/index.html` — campus admin dashboard and meal-plan/swipe information
- `assets/css/style.css` — Carolina-inspired styling
- `assets/js/app.js` — demo authentication, navigation, and sample interactions

## Suggested production architecture
- Frontend: this UI, hosted on an approved hosting platform
- Backend: API server (for example, Node/Express, Django, or an approved UNC platform)
- Database: PostgreSQL with row-level access policies
- Identity: UNC-approved SSO for students/admins; verified business onboarding for business accounts
- Authorization: server-side Student / Business / Dining Finance / Staff roles
- Security: hashed passwords (Argon2id/bcrypt), secure session cookies, CSRF protection, HTTPS, server-side rate limiting and lockout, audit logs, and privacy-reviewed data retention

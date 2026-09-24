# REKVION TECHNOLOGIES Platform

Firebase-ready React/Vite website + customer portal + admin CMS foundation for REKVION TECHNOLOGIES.
.
## Included
- Public company website
- Responsive homepage, services, app showcase and support CTA
- Firebase Authentication
- Customer registration/login
- Customer portal
- Service request creation stored in Firestore
- Admin dashboard foundation
- Customer/service-request/payment data views
- CMS/settings UI for business content
- Payment notification workflow model (no card payments)
- App/portfolio/content architecture ready to expand
- Role field in Firestore user records
- Firebase Storage initialized for future documents/media

## Important
This is a working Firebase-ready foundation. Some advanced modules from the specification (PDF generation, email automation, full quotation/invoice CRUD, file upload UI, project milestones, rich text CMS, audit logs and analytics) have their data/UI architecture represented but require the corresponding production Firebase rules/functions and CRUD screens to be completed before public launch.

## Run locally
1. Install Node.js 20+.
2. Copy `.env.example` to `.env`.
3. Create a Firebase project at https://console.firebase.google.com/.
4. Enable Authentication → Email/Password.
5. Create a Firestore database.
6. Enable Storage.
7. Put your Firebase web-app credentials into `.env`.
8. Run:

```bash
npm install
npm run dev
```

Open the Vite URL shown in the terminal.

## Build for production
```bash
npm run build
npm run preview
```

## Firebase Hosting
Install Firebase CLI:
```bash
npm install -g firebase-tools
firebase login
firebase init hosting
```
Choose the existing Firebase project, use `dist` as the public directory, and configure it as a single-page app.
Then:
```bash
npm run build
firebase deploy
```

## Admin access
The demo UI exposes `/admin`. For production, protect it using a Firestore `users/{uid}` document with `role: "admin"` and enforce the same role in Firestore Security Rules and server-side Cloud Functions where needed. Do not rely on client-side route hiding for security.

## Recommended production collections
`users`, `serviceRequests`, `services`, `applications`, `projects`, `projectMilestones`, `quotations`, `quotationItems`, `invoices`, `invoiceItems`, `payments`, `paymentSubmissions`, `paymentMethods`, `supportTickets`, `supportMessages`, `reviews`, `portfolioProjects`, `faqs`, `announcements`, `blogPosts`, `notifications`, `documents`, `websiteSettings`, `businessSettings`, `navigationItems`, `auditLogs`.

## Security before launch
Add Firestore/Storage Security Rules so customers can only access their own records. Admin operations should be role-controlled. Add App Check, rate limiting/abuse protection, validated uploads and Cloud Functions for trusted operations such as invoice numbering, payment verification, email notifications and audit logging.

## Business identity
The supplied registration certificate supports the business name `REKVION TECHNOLOGIES` and registration number `BN-2OS9ZRRR`. Do not add unsupported registration claims to the public site.

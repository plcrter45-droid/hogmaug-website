# HGMA Uganda — premium association website

An original, responsive Vite site for the Hotel General Managers Association Uganda (HGMA). The interface uses the supplied HGMA logo, the live reference content and the official HOGMAU profile PDF. It now includes the named leadership, contact details, mission, vision, governance structure, objectives, beneficiaries and strategic partners supplied in the profile.

## Run locally

```bash
npm install
npm run dev
```

Production build:

```bash
npm run build
```

## Content and integration notes

- Organization copy and rendered content arrays live in `src/main.js` and are ready to be extracted into a CMS/data layer later.
- The Members directory is structured with search and category filters, but remains empty until HOGMAU supplies verified member organization records; no outside member data is included.
- The newsletter form validates on the client; membership applications use the connected Netlify Function when the production environment variables are configured.
- Membership applications are wired to `netlify/functions/membership-apply.mjs`. Run `supabase/membership_applications.sql` in Supabase, then add the server-only `SUPABASE_URL`, `SUPABASE_SERVICE_ROLE_KEY`, `RESEND_API_KEY`, `HOGMAU_NOTIFICATION_EMAIL`, and verified-domain `EMAIL_FROM` values to Netlify. Applications are stored as `pending_verification`, and the applicant’s contact details are sent to the HOGMAU notification email.
- `netlify/functions/membership-members.mjs` exposes only the public directory fields for pending applications; applicant email addresses and phone numbers are not published in the member list.
- `public/sitemap.xml`, `public/robots.txt`, and `.env.example` are included for deployment handoff.
- All supplied photography is stored locally in `public/media/`; the first group photo is the homepage hero background. No external stock photography or web font is loaded. The supplied logo is stored at `public/hgma-logo.jpg`.

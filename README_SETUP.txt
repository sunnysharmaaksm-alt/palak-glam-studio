PALAK GLAM STUDIO — MANUAL REVIEW APPROVAL UPDATE

Files:
- index.html: updated public website page with customer review submission and approved-review display.
- admin.html: Google sign-in admin dashboard for approving/rejecting pending reviews.

IMPORTANT DEPLOYMENT:
1. In your GitHub repository, replace the existing index.html with this index.html.
2. Upload admin.html to the same repository root (same level as index.html).
3. Do not delete or replace your existing image files. The updated index.html continues to use them.
4. Netlify should redeploy automatically. Then open https://palak-glam-studio.netlify.app/admin.html
5. Sign in with palakglamstudio@gmail.com. The Google OAuth app must still include this account as a Test User while the app is in Testing mode.

DATABASE:
The Supabase table and RLS policies should already have been created in the earlier SQL Editor step. The code expects public.customer_reviews with columns:
id, customer_name, rating, review, status, created_at.
Allowed status values: pending, approved, rejected.

SUPABASE SETTINGS:
- Project URL and browser publishable key are configured in both HTML files.
- Supabase Authentication > URL Configuration must allow https://palak-glam-studio.netlify.app/**
- Google provider must be enabled with your Google OAuth Web Client ID and Client Secret.
- Google OAuth redirect URI must be exactly https://qbhjfmlermgyorsonjvb.supabase.co/auth/v1/callback

SECURITY:
- The sb_publishable key is intended for browser use; database access is restricted by RLS.
- Never put the Google OAuth Client Secret or Supabase service_role/secret key in these files or GitHub.
- Only palakglamstudio@gmail.com is allowed by the admin UI and the database policies created in the SQL step.
- Public visitors can submit pending reviews and read approved reviews only.
- A static-site admin page is not hidden from the public; security is enforced by Google sign-in and Supabase RLS.

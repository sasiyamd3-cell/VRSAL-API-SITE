MIYORA API MARKETPLACE — VERCEL DEPLOYMENT

Files are at repository root; api/ contains the two required Vercel serverless functions.

SECURITY FIRST
The MongoDB URI shared in chat contains a database credential. Rotate/change that database user's password in MongoDB Atlas immediately, then use the NEW connection string only in Vercel Environment Variables. Never commit it into this repository or put it in frontend files.

GITHUB + VERCEL
1. Upload all files and the api/ folder to the ROOT of a GitHub repository.
2. Import the repository in Vercel and deploy.
3. In Vercel Project Settings > Environment Variables, add:
   MONGODB_URI = NEW rotated MongoDB Atlas URI
   MONGODB_DB = miyora_api
   ADMIN_USERNAME = SASINDA
   ADMIN_PASSWORD = set the requested password here, or choose a new strong password
   ADMIN_SECRET = a long random secret (32+ random characters)
4. In MongoDB Atlas, allow network access for your deployment according to your security requirements, and create a database user with only the permissions needed for this database.
5. Redeploy after adding/changing environment variables.
6. Website: /
   Admin: /admin.html

ADMIN LOGIN
Username defaults to SASINDA unless ADMIN_USERNAME is set. The password is read only from ADMIN_PASSWORD. Do not place credentials in client-side JS.

NOTES
- The admin UI can add/edit/delete API catalogue entries in MongoDB.
- Public API catalogue data is returned by /api/apis; don't put private keys into public URLs.
- This is a small starter implementation. Before production, add rate limiting, audit logging, stricter CSRF/session protections, and monitoring.
- No MongoDB connection string is hardcoded in source files.

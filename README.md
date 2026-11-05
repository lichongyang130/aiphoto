# Portrait Studio

An English-language AI portrait product starter with a public marketing site, a user workspace, private photo uploads, project drafts, SQLite persistence, and Google/GitHub OAuth integration.

## Run locally

Requires Node.js 22. Install dependencies with `npm install` and start with `npm start`. Open http://localhost:3000. Demo mode is enabled by default and creates a fresh temporary account per session; set `ENABLE_DEMO=false` to disable it. Uploaded data and the SQLite database are stored in `uploads/` and `data/` and are not checked into Git.

## OAuth configuration

Set `BASE_URL` to the public application origin and `SESSION_SECRET` to a long random secret. Set `GOOGLE_CLIENT_ID` and `GOOGLE_CLIENT_SECRET` for Google, and/or `GITHUB_CLIENT_ID` and `GITHUB_CLIENT_SECRET` for GitHub. Register these exact callback URLs with the providers:

- `BASE_URL/auth/google/callback`
- `BASE_URL/auth/github/callback`

Restart the server after changing environment variables. Providers without credentials are disabled in the interface.

## Current scope and deployment notes

AI image generation and payment are **not integrated**. Project creation saves a draft only; it does not generate images or charge users. Production deployment requires a real image provider, payment integration, durable session store (the default Express memory store is for development only), secure file storage, validation of file contents, CSRF protection, rate limiting, a privacy policy, retention/deletion policies, and appropriate security review. Configure HTTPS and `NODE_ENV=production` in production. The example inspiration images are remotely hosted Unsplash photos, not AI-generated user results.

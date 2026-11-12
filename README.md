# FocusBoard

A responsive, local-first task board built with **GitHub Copilot** for MLH Global Hack Week: Builders Week.

## Live app

https://paul-jsn.github.io/ghw-focusboard/

## Features

- Real Auth0 Universal Login using Authorization Code + PKCE.
- Sign in with Google or an Auth0 database account, view the authenticated profile, and sign out.
- Add, complete, reactivate, delete, and filter tasks.
- Task statistics and responsive layouts.
- Local task data partitioned by authenticated user ID. Tasks are not cloud-synced.
- Loading, authentication-error, retry, and logout-cleanup states.

## Run locally

Serve this directory using a static HTTP server on port 4173, then open `http://localhost:4173/`. The app is one `index.html` file with no build step.

Example with Node.js: `npx --yes http-server . -p 4173 -c-1`

## Auth0 configuration

The app uses the Auth0 SPA JS v2 SDK from its official CDN. `AUTH0_DOMAIN` and `AUTH0_CLIENT_ID` in `index.html` are public application identifiers, not secrets. No client secret belongs in this SPA.

Configure an Auth0 Single Page Application with these exact URLs:

- Allowed Callback URLs: `http://localhost:4173/`, `https://paul-jsn.github.io/ghw-focusboard/`
- Allowed Logout URLs: same as callback URLs
- Allowed Web Origins: `http://localhost:4173`, `https://paul-jsn.github.io`

For your own deployment, create your own Auth0 SPA app, replace those public identifiers and configure your own URLs.

## Security and privacy

- Authentication is real, not a mocked sign-in.
- OAuth tokens remain in memory. No client secret or access token is stored in task localStorage.
- User-controlled text is inserted with `textContent`, not HTML.
- Only non-sensitive task data is stored locally under a user-specific key. Do not put sensitive information in tasks.
- Task storage is not encrypted or a backend authorization boundary; another person with access to the same browser profile can inspect it.
- Clearing browser data removes tasks.
- Google sign-in uses Auth0 development keys in this demo. Production requires your own social connection credentials.

## Copilot contribution

GitHub Copilot generated the initial app and reviewed the Auth0 SDK integration. Its review fixed the UMD namespace to `window.auth0.createAuth0Client`, added callback-error handling, and cleared in-memory dashboard data before logout. The code was reviewed, configured, and tested against a real Auth0 tenant before submission. See `COPILOT.md` for the prompt and implementation notes.

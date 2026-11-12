# Built with GitHub Copilot

## Development workflow

This app was generated in a real GitHub Copilot cloud chat while signed in as **Paul-JSN** on November 12, 2026. A second Copilot review supplied targeted authentication fixes. The code was then reviewed and connected to a real Auth0 SPA application. No mocked authentication or fabricated AI-use evidence was used.

## Initial prompt summary

Build a complete, runnable single-file static task dashboard using plain HTML/CSS/JavaScript and Auth0 SPA JS v2. Use real Universal Login with Authorization Code + PKCE, memory-only token caching, profile rendering, logout, accessible responsive UI, local per-user task storage, task filters, loading/error/retry states, and safe DOM APIs. Support localhost and GitHub Pages. Never include a client secret.

## Review prompt summary

Check the Auth0 v2 UMD SDK namespace; improve authorization-error callbacks, safe logout errors, and remove stale dashboard data on sign-out.

## Copilot review applied

1. Corrected `window.createAuth0Client` to `window.auth0.createAuth0Client`.
2. Added normalized error messages and `error`/`error_description` callback handling.
3. Cleaned callback query parameters from browser history after success or failure.
4. Cleared current profile, task UI, counters, and in-memory user state before logout.
5. Kept authentication tokens in memory and task storage scoped to the current user ID.

## Scope

This is a small client-side demo, not a multi-device task service. Task data remains on the current browser and is not encrypted or synchronized.

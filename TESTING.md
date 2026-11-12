# Verification record

Tested November 12, 2026 against the configured Auth0 development tenant with a real Google account.

## Passed

- Static app loads the official Auth0 SPA JS SDK and shows a logged-out landing page.
- Sign in redirects to real Auth0 Universal Login and Google sign-in.
- Granting app consent returns through the authorization-code callback and displays the authenticated profile.
- Declining app consent shows `access_denied` in the error view and removes callback parameters from the address bar.
- A sign-in retry after denial succeeds.
- Add three tasks; total and active counters update correctly.
- Text containing `<draft>` renders literally as text, not markup.
- Mark a task complete; active/completed counts update.
- Done and Active filters show the expected task subsets.
- Delete a task; total count decreases and the All filter remains correct.
- Authenticated interface checked at 390x844 and desktop viewport sizes.
- Sign out returns to the public view and immediately clears profile, task list, and counters from the DOM.
- Local task records remain per-user, as documented; no OAuth tokens or client secrets are written to task storage.

## Limitations

This is a browser-local demo. Multi-device syncing, database access control, production social credentials, and penetration testing are out of scope. Login state uses in-memory tokens, so reloading may require another redirect to restore a session depending on browser cookie policies.

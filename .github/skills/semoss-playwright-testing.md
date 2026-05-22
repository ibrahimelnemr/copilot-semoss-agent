# SEMOSS Playwright Browser Testing

## Purpose
Test SEMOSS platform features via the browser using the generic [playwright-browser-testing](./playwright-browser-testing.md) skill, pre-configured with SEMOSS-specific URLs and navigation patterns.

## Inherits
All workflow, rules, and tool usage from [playwright-browser-testing](./playwright-browser-testing.md).

## SEMOSS Environment

### Environment file
User-specific configuration (credentials, URLs) is stored in `.semoss-env.md` at the workspace root. This file is **gitignored** and must never be committed.

### Before testing — environment setup
1. **Check for `.semoss-env.md`** in the workspace root.
2. If the file **does not exist** or is missing required fields:
   - Ask the user for their SEMOSS credentials (username and password) using the ask-questions tool.
   - Ask the user to confirm or provide the local SemossWeb URL (default: `http://localhost:9090/`).
   - Write the answers to `.semoss-env.md` in this format:
     ```
     # SEMOSS Local Environment (DO NOT COMMIT)
     ## URLs
     - **SEMOSS UI**: <confirmed URL, default http://localhost:9090/>
     - **Playground**: http://localhost:5174/
     ## Credentials
     - **Username**: <provided username>
     - **Password**: <provided password>
     ```
3. If the file **exists**, read it and use the stored values. Still confirm the SEMOSS UI URL with the user on first use in a session (it may have changed ports).

### Login flow
1. Open the SEMOSS UI URL from `.semoss-env.md`.
2. If redirected to a login page, enter credentials from `.semoss-env.md`:
   - Type the username into the username/email field.
   - Type the password into the password field.
   - Click the sign-in / login button.
3. Wait for the main dashboard to load (read the page to confirm).

### Common navigation paths
- **Settings**: Click on the user/settings icon, or navigate to `/settings`
- **Room Token Limits**: Settings → Room Token Limits (under admin settings)
- **Usage Limits**: Settings → Usage Limits (under admin settings, at `#/settings/usage-limits`)
- **Rooms/Chat**: Navigate to a room or create a new one from the main interface

## SEMOSS-specific testing patterns

### Settings page testing
1. Navigate to Settings
2. Find and click the target setting (e.g., "Room Token Limits")
3. Interact with the settings form
4. Verify changes persist (reload and re-check)

### Token limit testing
1. Navigate to Settings → Room Token Limits
2. Set default limits for different periods (Yearly, Monthly, Weekly, Daily)
3. Add user overrides
4. Verify the overrides table displays correctly
5. Test the confirmation dialogs (save defaults, delete override)
6. Navigate to a chat room and verify limits are enforced

## When to invoke
- When testing SEMOSS platform features end-to-end.
- After making changes to SEMOSS frontend (SemossWeb) or backend (Semoss/Monolith).
- When the user asks to verify a SEMOSS feature works correctly.

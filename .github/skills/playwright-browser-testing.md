# Playwright Browser Testing

## Purpose
Validate that changes work correctly by performing actual browser-level testing against running applications using the built-in VS Code browser tools (open_browser_page, read_page, click_element, type_in_page, screenshot_page, etc.).

## Prerequisites
- The VS Code setting `workbench.browser.enableChatTools` **MUST** be enabled for the browser interaction tools (read_page, click_element, type_in_page, screenshot_page, etc.) to be available.
- If the tools are not available (i.e., `open_browser_page` works but returns "Note that you do not have access to the page contents unless the user enables agentic tools"), **prompt the user** to enable `workbench.browser.enableChatTools` in VS Code settings before proceeding.

## When to invoke
- After implementation is complete and before marking a task as done.
- When verifying a bug fix or feature works end-to-end.
- When the user asks to test a UI flow or page.

## How it works
This skill uses the VS Code integrated browser tools — NOT the `@playwright/test` npm package. The tools provide:
- `open_browser_page(url)` — opens a page, returns a `pageId`
- `read_page(pageId)` — gets an accessibility snapshot of the page (better than screenshots for understanding structure)
- `click_element(pageId, element, ref/selector)` — click on elements
- `type_in_page(pageId, text/key, ref/selector)` — type text or press keys
- `screenshot_page(pageId)` — capture a visual screenshot
- `navigate_page(pageId, url)` — navigate to a URL
- `hover_element(pageId, element, ref/selector)` — hover over elements
- `handle_dialog(pageId)` — handle modal dialogs
- `run_playwright_code(pageId, code)` — run raw Playwright code if other tools are insufficient

## Workflow

1. **Open the application** using `open_browser_page` with the target URL.
2. **Authenticate** if needed — navigate to the login page, fill credentials using `type_in_page`, submit with `click_element`.
3. **Navigate to the feature** being tested.
4. **Read the page** using `read_page` to understand the current DOM state and available elements.
5. **Interact** with the page: fill forms, click buttons, select options.
6. **Verify outcomes** by reading the page again and checking that expected elements/text appear.
7. **Screenshot** key states for visual confirmation.
8. **Repeat** for different test scenarios.

## Test structure
Each test scenario should:
1. Start from a known state (e.g., freshly navigated page)
2. Perform a specific action sequence
3. Verify the expected outcome using `read_page`
4. Report pass/fail with details

## On failure
- Capture a screenshot of the failure state.
- Read the page to understand what went wrong.
- Report the exact failure with context.
- If the issue is in the code, fix it and re-test.

## On success
- Note passing tests in the task documentation.
- Report a summary of all scenarios tested and their results.

## Rules
- Always use `read_page` before interacting to find correct element references.
- Prefer `ref` attributes from `read_page` over CSS selectors for clicking/typing.
- Wait for page transitions after navigation or form submissions by re-reading the page.
- Do not hardcode timing delays — use `read_page` to check readiness.

# SEMOSS Copilot Agent

A collection of GitHub Copilot skills and agents for software engineering and testing within the SEMOSS platform.

## Setup

1. **Clone this repo** into your workspace (or add it as a workspace folder in VS Code).

2. **Select the `software-engineer` agent** in GitHub Copilot Chat (click the agent picker or type `@software-engineer`).

3. **Ensure SemossWeb is running** locally (default: `http://localhost:9090/SemossWeb/`).

4. **Start a chat** — on first use, the agent will ask for your SEMOSS credentials and local URL, then store them in a gitignored `.semoss-env.md` file.

5. **Provide a task** — e.g. "test the Room Token Limits settings page" or "verify the login flow works".

## What's included

- **Skills** (`.github/skills/`): Reusable knowledge for Playwright browser testing, SEMOSS-specific workflows, deep analysis, and task documentation.
- **Agents** (`.github/agents/`): Pre-configured agent modes (`software-engineer`, `deep-investigation`).

## Notes

- Credentials are never committed — `.semoss-env.md` is gitignored.
- The default SEMOSS URL is `http://localhost:9090/SemossWeb/`. You'll be prompted to confirm or change it.
- Browser testing uses VS Code's built-in Playwright tools (requires `workbench.browser.enableChatTools` to be enabled in VS Code settings).

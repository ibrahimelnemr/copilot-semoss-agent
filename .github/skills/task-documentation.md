# Task Documentation

## Purpose
Keep a concise technical document for each task in the root of the workspace so the analysis, decisions, validation, and final outcome stay visible while work is in progress.

## When to invoke
- **At task start**: Create or update the task document before implementation begins.
- **During the task**: Update the document when you find new evidence, change direction, hit a blocker, or complete a meaningful implementation step.
- **At task completion**: Finalize the document with what changed, how it was validated, and any follow-up items.

## File conventions
- **Location**: the root of the workspace folder.
- **Naming**: `{Date}_{description}.md` using the workspace convention already present in this repo, for example `Apr242026_recording_loader_fix.md`.
- **Reuse existing docs**: If a document already exists for the task, update it in place instead of creating a new file.

## Suggested structure
Use a concise structure like this when creating or refreshing the document:

```markdown
# {Task Title}

**Date**: {Date}
**Status**: {In Progress | Investigation Complete | Completed | Blocked}

## Objective
Brief description of the task and expected outcome.

## Technical Analysis
- Relevant files, code paths, or systems involved.
- What likely needs to change and why.
- Important risks, assumptions, or edge cases.

## Changes Made
- Code or configuration changes completed so far.
- Key implementation notes.

## Issues & Decisions
- Important findings, blockers, or tradeoffs.
- Changes in approach and why they were made.

## Testing / Validation
- Commands or checks that were run.
- Results and any remaining gaps.

## Follow-up
- Open items, risks, or next steps.
```

## Rules
- Fill the document with real technical details, not placeholders.
- Keep the document current as the task evolves.
- Prefer concise facts and decisions over long narrative prose.
- When the task is investigation-only, make sure the document clearly separates observed evidence from hypotheses.
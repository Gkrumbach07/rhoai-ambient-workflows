# Frontend Change Workflow

An Ambient Code Platform workflow that implements a frontend-only fix from a bug/story/task description, verifies it locally, and opens a PR with proof.

## Overview

This workflow runs end-to-end:

1. **Clone repo** - Uses the fork URL if provided, otherwise clones `https://github.com/ambient-code/platform`, and clones into the workflow root folder
2. **Create branch** - Creates a new working branch
3. **Investigate + plan** - Investigates the issue and creates a todo-based plan
4. **Implement fix** - Applies frontend-only changes
5. **Verify locally** - Runs the frontend locally per `docs/developer/local-development/hybrid.md`
6. **Record proof** - Uses Playwright MCP to record a short video
7. **PR delivery** - Commits, pushes, and creates a PR with `gh`, posting the video to the PR

## How to Use

### Loading in ACP

1. Open your ACP session
2. Select **Custom Workflow**
3. Use this repository and path: `workflows/frontend-change-agent`
4. Provide the bug/story/task description and optional fork URL

### Inputs

- **Description** (required): Bug/story/task text for a frontend-only change
- **Fork URL** (optional): Fork to use instead of upstream

## Verification Details

The workflow starts the frontend using the repo instructions in `docs/developer/local-development/hybrid.md` and validates behavior with Playwright MCP.

Set these env vars for the local run:

- `BOT_TOKEN` as the user token
- `BACKEND_URL=http://backend-service.ambient-code.svc.cluster.local:8080`

## Output

- A working branch with frontend-only changes
- Verification notes based on Playwright MCP
- A short video demonstrating the fix
- A PR created via `gh` with a concise summary and verification notes

## Workflow Structure

```
workflows/frontend-change-agent/
├── .ambient/
│   └── ambient.json
└── README.md
```

## Best Practices

- Keep the fix minimal and frontend-only
- Use a short, descriptive branch name
- Keep the PR description concise and focused on the user-visible change

---

**Workflow**: Frontend Change Workflow  
**Version**: 1.0.0  
**Author**: RHOAI Engineering  
**Last Updated**: 2026-01-26

# Workflow Instance Directory

This directory is where your active workflow instances will be created when you initialize a new workflow.

## What gets created here

When you run `/workflow-start`, the system will generate:

- `CLAUDE_workflow_YYYY-MM-DD.md` - Main workflow coordination file
- `log_workflow_YYYY-MM-DD.md` - Communication hub and progress tracking
- `lead_workflow_YYYY-MM-DD.md` - Lead agent's private workspace
- `manager_workflow_YYYY-MM-DD.md` - Manager agent's private workspace  
- `worker_workflow_YYYY-MM-DD.md` - Worker agent's private workspace

## Directory structure example

```
CLAUDE_workflow/
├── CLAUDE_workflow_2025-01-31.md
├── log_workflow_2025-01-31.md
├── lead_workflow_2025-01-31.md
├── manager_workflow_2025-01-31.md
└── worker_workflow_2025-01-31.md
```

## Usage

1. Keep this directory for workflow instances
2. Each new workflow gets its own dated set of files
3. Multiple workflows can run simultaneously with different dates
4. Archive completed workflows by moving to a `completed/` subdirectory

---

*This directory should remain in your project structure for the three-agent workflow system to function properly.*
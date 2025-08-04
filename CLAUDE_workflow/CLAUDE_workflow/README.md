# Workflow Instances Directory

This is where all your active workflow instances are created and managed.

## How workflows are organized

When you run `/workflow-start`, the system will create a **new task folder** inside this directory named `task_date` containing all workflow files:

- `CLAUDE_workflow_YYYY-MM-DD.md` - Main workflow coordination file
- `log_workflow_YYYY-MM-DD.md` - Communication hub and progress tracking
- `lead_workflow_YYYY-MM-DD.md` - Lead agent's private workspace
- `manager_workflow_YYYY-MM-DD.md` - Manager agent's private workspace  
- `worker_workflow_YYYY-MM-DD.md` - Worker agent's private workspace

## Directory structure example

```
CLAUDE_workflow/CLAUDE_workflow/
├── my_task_2025-01-31/
│   ├── CLAUDE_workflow_2025-01-31.md
│   ├── log_workflow_2025-01-31.md
│   ├── lead_workflow_2025-01-31.md
│   ├── manager_workflow_2025-01-31.md
│   └── worker_workflow_2025-01-31.md
├── another_task_2025-02-01/
│   ├── CLAUDE_workflow_2025-02-01.md
│   └── ...
└── README.md (this file)
```

## Usage

1. Each workflow gets its own `task_date` folder within this directory
2. Multiple workflows can run simultaneously as separate task folders
3. All workflow files for a specific task are contained within its folder
4. Archive completed tasks by moving folders to a `completed/` subdirectory

---

*This directory should remain in your project structure for the three-agent workflow system to function properly.*
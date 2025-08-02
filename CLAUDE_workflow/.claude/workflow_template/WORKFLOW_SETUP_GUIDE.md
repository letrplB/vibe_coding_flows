# CLAUDE Three-Agent Workflow Setup Guide

## 🚀 Quick Start

### Slash Command: `/workflow-start`

When user types `/workflow-start`, the system should:

1. **Prompt for workflow details**:
   - Task name (e.g., "implement_auth_system")
   - Task description (brief mission statement)
   - Primary objective (what success looks like)
   - Scope definition (what's included/excluded)

2. **Create workflow structure**:
   ```
   CLAUDE_workflows/
   └── {task}_{date}/
       ├── CLAUDE_{task}_{date}.md          # Mission instructions
       ├── log_{task}_{date}.md         # Communication hub
       ├── lead_{task}_{date}.md            # Lead workspace
       ├── manager_{task}_{date}.md         # Manager workspace
       ├── worker_{task}_{date}.md          # Worker workspace
       └── outputs/                         # Deliverables folder(lead, manager and worker outputs)
                                            
   ```

3. **Initialize files with templates**:
   - Replace all {PLACEHOLDERS} with actual values
   - Set initial status for all agents as "⏳ Waiting"
   - Create first milestone entries

## 📝 Template Variable Mapping

### Common Variables
- `{TASK_NAME}`: User-provided task name (snake_case)
- `{SESSION_NAME}`: `{task}_{YYYYMMDD}` format
- `{DATE}`: Current date in YYYY-MM-DD format
- `{WORKFLOW_NAME}`: Human-readable task name

### Mission-Specific Variables
- `{TASK_DESCRIPTION}`: Brief description from user
- `{PRIMARY_OBJECTIVE}`: Main goal statement
- `{SCOPE_DEFINITION}`: What's included/excluded
- `{EXPECTED_DELIVERABLES}`: List of expected outputs
- `{SUCCESS_METRICS}`: How to measure completion

## 🎭 Agent Activation

### Step 1: Create Mission File
Use `CLAUDE_workflow_merged.template.md` → `CLAUDE_{task}_{date}.md`

### Step 2: Create Communication Hub  
Use `session_workflow_date.template.md` → `session_{task}_{date}.md`

### Step 3: Create Agent Workspaces
- `lead_workflow_date.template.md` → `lead_{task}_{date}.md`
- `manager_workflow_date.template.md` → `manager_{task}_{date}.md`
- `worker_workflow_date.template.md` → `worker_{task}_{date}.md`

### Step 4: Activate Lead Agent
Display to user:
```
✅ Workflow "{task_name}" initialized!

📁 Created in: CLAUDE_workflows/{task}_{date}/

🎭 To activate agents, use:
- @lead: Start strategic analysis
- @manager: Begin coordination (after lead)
- @worker: Execute tasks (after manager assigns)

📋 Mission: {task_description}

💡 Tip: Start with "@lead please begin the {task_name} workflow"
```

## 🔄 Workflow Commands

### `/workflow-status`
Show current status of active workflow:
- Agent statuses
- Active assignments
- Completed deliverables
- Token usage (if worker active)

### `/workflow-complete`
Finalize workflow:
- Run quality checklist
- Archive communication logs
- Compile final deliverables
- Generate summary report

### `/workflow-pause`
Temporarily pause workflow:
- Save current state
- Document pause reason
- Preserve token counts

### `/workflow-resume`
Resume paused workflow:
- Restore agent states
- Update dates/times
- Continue from last checkpoint

## 🛠️ Implementation Details

### File Creation Logic
```python
def create_workflow(task_name, description, objective, scope):
    date = datetime.now().strftime("%Y%m%d")
    session_name = f"{task_name}_{date}"
    
    # Create directory structure
    base_dir = f"CLAUDE_workflows/{session_name}"
    os.makedirs(f"{base_dir}/outputs", exist_ok=True)
    
    # Load templates and replace variables
    variables = {
        "TASK_NAME": task_name,
        "SESSION_NAME": session_name,
        "DATE": datetime.now().strftime("%Y-%m-%d"),
        "TASK_DESCRIPTION": description,
        "PRIMARY_OBJECTIVE": objective,
        "SCOPE_DEFINITION": scope,
        # ... other variables
    }
    
    # Create files from templates
    for template, output in template_mapping.items():
        create_from_template(template, output, variables)
```

### Agent Activation Pattern
```markdown
## To activate {agent_type} agent:

1. Agent reads their instructions in CLAUDE_{task}_{date}.md
2. Agent opens their workspace {agent}_{task}_{date}.md
3. Agent updates status in session_{task}_{date}.md
4. Agent begins their role-specific work
```

## 📊 Success Metrics

### Workflow Health Indicators
- ✅ All agents have updated status in last 30 minutes
- ✅ Token usage below 50k for any worker
- ✅ No blockers in alerts section
- ✅ Deliverables being created in outputs/
- ✅ Clear assignment tracking

### Quality Gates
1. **Lead Review**: Strategy aligns with objectives
2. **Manager Coordination**: Tasks properly sized and assigned
3. **Worker Execution**: Deliverables meet specifications
4. **Integration Check**: All outputs coherently integrated
5. **User Acceptance**: Objectives achieved

## 🚨 Common Issues & Solutions

### Issue: Token Overflow
**Solution**: Built-in monitoring in Manager agent
- Automatic alerts at 50k tokens
- Forced stop at 60k tokens
- Clear restart procedures

### Issue: Agent Confusion
**Solution**: Clear role separation in templates
- Each agent has specific workspace
- Defined communication protocols
- Mode/Type switching for flexibility

### Issue: Lost Context
**Solution**: Persistent documentation
- All decisions logged in session file
- Individual agent notes preserved
- Assignment history maintained

## 🎯 Best Practices

1. **Start Simple**: Begin with clear, focused objectives
2. **Trust the Process**: Let agents follow their workflows
3. **Monitor Progress**: Check session file regularly
4. **Intervene Wisely**: Only step in for blockers
5. **Document Learnings**: Capture insights for future workflows

## 📚 Advanced Features

### Custom Worker Types
Add new worker types by extending:
```markdown
<WorkerTypes>
- **CODER**: Implementation, refactoring, code generation
- **DEBUGGER**: Issue analysis, error resolution, testing
- **ANALYST**: Deep code analysis, pattern recognition
- **RESEARCHER**: Information gathering, best practices
- **CUSTOM**: [Define your own specialized type]
</WorkerTypes>
```

### Custom Manager Modes
Extend manager capabilities:
```markdown
<ManagerModes>
- **PLANNER**: Break down complex tasks
- **CONTEXT_MANAGER**: Gather information
- **ANALYST**: Review outputs
- **INTEGRATOR**: Coordinate assembly
- **MONITOR**: Track performance
- **CUSTOM**: [Define your own mode]
</ManagerModes>
```

## 🔧 Maintenance

### Daily Cleanup
- Archive completed workflows after 7 days
- Compress large output folders
- Update templates based on learnings

### Template Evolution
- Collect feedback from workflows
- Identify common patterns
- Update templates quarterly
- Version control all changes

---

**Remember**: The workflow system is designed to be self-organizing. Trust the agents to follow their protocols and intervene only when necessary.
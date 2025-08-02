# Start Multi-Claude Three-Agent Workflow
/workflow-start

## Description
Initialize a three-agent workflow system where THIS Claude instance creates the workflow and becomes the Lead agent. User opens separate Claude Code instances for Manager and Worker agents.

## Arguments
$ARGUMENTS - Task name and description (e.g., "implement_auth_system", "debug_graphql_errors", "analyze_permissions")

## Execution Steps

### Step 1: Gather Workflow Parameters
```
1. Parse task name (snake_case format)
2. Request additional details if not provided:
   - Task description (brief mission statement)
   - Primary objective (what success looks like)
   - Scope definition (what's included/excluded)
```

### Step 2: Validate Template Files Exist
```
Verify all required template files are present in .claude/workflow_template/:
- ✓ CLAUDE_workflow_date.template.md
- ✓ log_workflow_date.template.md
- ✓ lead_workflow_date.template.md
- ✓ manager_workflow_date.template.md
- ✓ worker_workflow_date.template.md

If any template is missing, abort with error message.
```

### Step 3: Create Workflow Structure
```
CLAUDE_workflows/
└── {task}_{YYYYMMDD}/
    ├── CLAUDE_{task}_{YYYYMMDD}.md      # Mission instructions (all agents read)
    ├── log_{task}_{YYYYMMDD}.md         # Communication hub
    ├── lead_{task}_{YYYYMMDD}.md        # Lead workspace
    ├── manager_{task}_{YYYYMMDD}.md     # Manager workspace
    ├── worker_{task}_{YYYYMMDD}.md      # Worker workspace
    └── outputs/                          # Deliverables folder
```

### Step 4: Copy and Initialize Files from Templates

**Copy all template files to workflow directory**:
1. Check if template files exist in `.claude/workflow_template/`
2. Copy each template file to the workflow directory:
   - `CLAUDE_workflow_date.template.md` → `CLAUDE_{task}_{date}.md`
   - `log_workflow_date.template.md` → `log_{task}_{date}.md`
   - `lead_workflow_date.template.md` → `lead_{task}_{date}.md`
   - `manager_workflow_date.template.md` → `manager_{task}_{date}.md`
   - `worker_workflow_date.template.md` → `worker_{task}_{date}.md`

**Perform variable substitution in all copied files**:
- `{TASK_NAME}`: User-provided task name
- `{SESSION_NAME}`: `{task}_{YYYYMMDD}`
- `{DATE}`: Current date YYYY-MM-DD
- `{TASK_DESCRIPTION}`: Brief description
- `{PRIMARY_OBJECTIVE}`: Main goal
- `{SCOPE_DEFINITION}`: What's included/excluded

**Verify all critical sections are present**:
- ✓ Agent Roles & Responsibilities (with detailed functions)
- ✓ Communication Protocol (with assignment format)
- ✓ Emergency Protocols
- ✓ Workflow Stages (initialization → execution → integration → completion)
- ✓ Quality Standards
- ✓ File Structure

### Step 5: THIS Claude Becomes Lead Agent
```
✅ Workflow "{task_name}" initialized!
📁 Created in: CLAUDE_workflows/{task}_{date}/

🎯 I am now the LEAD agent for this workflow.

📋 Mission: {task_description}

🛑 IMPORTANT: DO NOT START WORK YET!

👤 USER ACTION REQUIRED:
─────────────────────────
1. Open NEW Claude Code instance for MANAGER:
   - Reference file: CLAUDE_{task}_{date}.md
   - Prompt EXACTLY: "You are the Manager @CLAUDE_{task}_{date}.md. Onboard yourself to your persona and behavior patterns. Just state *ready* when you are ready. Do not do anything else."

2. Open NEW Claude Code instance for WORKER:
   - Reference file: CLAUDE_{task}_{date}.md
   - Prompt EXACTLY: "You are the Worker @CLAUDE_{task}_{date}.md. Onboard yourself to your persona and behavior patterns. Just state *ready* when you are ready. Do not do anything else."

3. WAIT for both agents to respond "*ready*"

4. Return here and say: "All agents ready. Begin lead analysis."

💡 The workflow uses log_{task}_{date}.md for inter-agent communication
⚠️ Each agent MUST read their full instructions before starting work
```

### Step 6: Lead Agent Begins Work
After user confirms other agents are ready:
1. Read mission from `CLAUDE_{task}_{date}.md`
2. Open workspace `lead_{task}_{date}.md`
3. Post initial strategic analysis to `log_{task}_{date}.md`
4. Create assignments for Manager/Worker using the format from Communication Protocol
5. Begin user-facing coordination

### Implementation Notes
When executing this command:
1. Use `Read` + `Write` to copy template files (since `cp` may not be available)
2. Use `Edit` with `replace_all: true` for variable substitution
3. Ensure all files are created before proceeding
4. Show checklist of created files to user

### Expected Output Structure
After successful execution, verify all files contain proper content:
```
CLAUDE_workflows/{task}_{date}/
├── CLAUDE_{task}_{date}.md      # Full template with all sections
├── log_{task}_{date}.md         # Proper assignment format defined
├── lead_{task}_{date}.md        # Lead workspace with role boundaries
├── manager_{task}_{date}.md     # Manager modes and coordination
├── worker_{task}_{date}.md      # Worker types and guidelines
└── outputs/                     # Empty, ready for deliverables
```

Each file should contain the full template content, not simplified versions.

## Multi-Claude Communication Protocol

### Log File Structure
```markdown
## ASSIGNMENTS
#1 [TIME] @manager: Strategic direction for {task}
   Context: {key constraints and goals}
   Focus: Break into 3-5 major components

## STATUS
Lead: ✅ Active - Strategic analysis complete
Manager: ⏳ Waiting - Ready for assignments
Worker: ⏳ Waiting - Ready for tasks

## MILESTONES
[TIME] Workflow initialized
[TIME] Lead posts strategic direction
```

### Agent Roles
- **Lead (This Claude)**: Strategic analysis, user communication, quality control
- **Manager (New Claude)**: Task breakdown, worker coordination
- **Worker (New Claude)**: Task execution, deliverable creation

## Critical Multi-Claude Rules
1. Each agent ONLY edits their own workspace file
2. All coordination through `log_{task}_{date}.md`
3. Assignments use format: `#N [TIME] @agent: Task [STATUS]`
4. Status updates are in-place (don't duplicate)

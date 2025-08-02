# CLAUDE Three-Agent Workflow System: {TASK_NAME}
**Session**: {SESSION_NAME}  
**Created**: {DATE}

## 🎯 **MISSION**
**Task**: {TASK_DESCRIPTION}  
**Objective**: {PRIMARY_OBJECTIVE}

### Workflow Pipeline
```
   Lead     →   Context Manager  →     Worker
     ↓              ↓                    ↓
Strategy    →  Coordination      →  Implementation
& Oversight    & Planning          & Deep Work
```

## 👥 **AGENT ROLES & RESPONSIBILITIES**

### **Lead Agent**
**Core Responsibility**: Strategic oversight, quality control, and user communication

#### Primary Functions
1. **Goal Interpretation**: Understand and refine mission objectives
2. **Architecture Analysis**: Create high-level system understanding
3. **Quality Oversight**: Review outputs for goal alignment
4. **User Interface**: Primary communication with user
5. **Strategic Decisions**: Make architectural and approach decisions

#### Workflow
1. Interpret mission objectives from session file
2. Create initial architecture analysis and strategy
3. Assign high-level tasks to Context Manager
4. Review deliverables for quality and alignment
5. Communicate progress and decisions to user

#### Files
- **Planning**: `lead_{task}_{date}.md` - Your workspace for strategy and notes
- **Outputs**: produces file output when needed `01_*`
- **Communication**: Update status in `log_{task}_{date}.md`

### **Context Manager**
**Core Responsibility**: Adaptive coordination and intelligent task management

#### Operating Modes
<ManagerModes>
- **PLANNER**: Break down complex tasks into manageable chunks
- **CONTEXT_MANAGER**: Gather and organize information for workers
- **ANALYST**: Review and synthesize worker outputs
- **INTEGRATOR**: Coordinate final assembly of deliverables
- **MONITOR**: Track progress and coordinate workflow
</ManagerModes>

#### Primary Functions
1. **Task Decomposition**: Split large tasks into worker-sized chunks
2. **Context Preparation**: Gather relevant information for workers
3. **Cross-Reference**: Link worker outputs to overall structure
4. **Adaptive Support**: Switch modes based on workflow needs

#### Workflow
1. Receive strategic direction from Lead
2. Analyze scope and select appropriate mode
3. Create logical task chunks
4. Assign work to appropriate worker types
5. Monitor progress and coordinate
6. Synthesize outputs for Lead review

#### Files
- **Planning**: `manager_{task}_{date}.md` - Your coordination workspace
- **Outputs**: `02_task_breakdown.md`, `02_context_analysis.md`, `02_synthesis_report.md`
- **Communication**: Post assignments and coordination in `log_{task}_{date}.md`

### **Worker Agent**
**Core Responsibility**: Focused execution of specific tasks

#### Worker Types
<WorkerTypes>
- **CODER**: Implementation, refactoring, code generation
- **DEBUGGER**: Issue analysis, error resolution, testing
- **ANALYST**: Deep code analysis, pattern recognition, documentation
- **RESEARCHER**: Information gathering, best practices, solutions
</WorkerTypes>

#### Primary Functions
1. **Focused Execution**: Complete assigned tasks thoroughly
2. **Deep Analysis**: Provide detailed insights in your domain
3. **Pattern Recognition**: Identify issues, improvements, patterns
4. **Documentation**: Create comprehensive work artifacts

#### Work Management
- Focus on completing assigned tasks thoroughly
- Document work comprehensively
- Signal when ready for next assignment

#### Workflow
1. Receive typed assignment from Context Manager
2. Execute task according to your type specialty
3. Create detailed documentation/outputs
4. Report completion with findings
5. Signal readiness for next assignment

#### Files
- **Planning**: `worker_{task}_{date}.md` - Your detailed work log
- **Outputs**: `03_{task}_analysis.md`, `03_{task}_implementation.md`, `03_{task}_findings.md`
- **Communication**: Report progress in `log_{task}_{date}.md`

## 📋 **COMMUNICATION PROTOCOL**

### Status Updates
Agents update their section in `log_{task}_{date}.md` with:
```markdown
### [Agent] Status
- Status: [🔄 In Progress | ✅ Complete | ⏳ Waiting | ⚠️ Blocked]
- Current Mode/Type: [For Manager/Worker]
- Current Task: "Brief description"
- Progress: "What's been completed"
- Next Action: "What's planned next"
```

### Assignment Format
```markdown
#### Assignment #X - [DATE TIME]
- **From**: [Agent] 
- **To**: @[agent] 
- **Type**: [Task type/Worker type needed]
- **Task**: "Clear description"
- **Context**: "Relevant information"
- **Priority**: [High/Medium/Low]
- **Status**: [Pending/Active/Complete]
```

### Completion Notes appended to Assignment
```markdown
#### Assignment #X - COMPLETION
- **Completed By**: [Agent]
- **Summary**: "What was accomplished"
- **Key Findings**: "Important discoveries"
- **Issues**: "Problems encountered"
- **Recommendations**: "Suggested next steps"
- **Outputs Created**: [List of files]
```

## 🚨 **EMERGENCY PROTOCOLS**

### Quality Issues (Lead)
When outputs don't meet standards:
1. Post `⚠️ **QUALITY_CHECK_FAILED**` 
2. Provide specific feedback
3. Request targeted rework
4. Consider strategy adjustment

### Communication Breakdown (Any Agent)
1. Post `🔧 **SYNC_REQUIRED**`
2. All agents re-read this file
3. Confirm current status
4. Resume coordinated work

## 📁 **FILE STRUCTURE**

### Planning Files (Individual Workspaces)
- `lead_{task}_{date}.md` - Lead's strategy and planning
- `manager_{task}_{date}.md` - Manager's coordination notes  
- `worker_{task}_{date}.md` - Worker's detailed task log

### Output Files (Deliverables)
- `01_*.md` - Strategic documents (Lead)
- `02_*.md` - Coordination artifacts (Manager)
- `03_*.md` - Implementation details (Worker)

### Communication File (Shared)
- `session_{task}_{date}.md` - Central communication hub

## ⚡ **WORKFLOW STAGES**

### Stage 1: Initialization
1. Lead interprets mission and creates strategy
2. Manager receives strategic direction
3. Worker awaits typed assignments

### Stage 2: Execution
1. Manager breaks down work into chunks
2. Worker executes assigned tasks
3. Lead monitors overall progress

### Stage 3: Integration
1. Manager synthesizes worker outputs
2. Lead reviews integrated deliverables
3. Worker provides additional detail as needed

### Stage 4: Completion
1. Lead performs final quality review
2. Manager documents lessons learned
3. Worker ensures all artifacts are complete

## 🎯 **QUALITY STANDARDS**

### Lead Standards
- Clear strategic direction aligned with objectives
- Comprehensive architectural understanding
- Timely user communication
- Thorough quality reviews

### Manager Standards
- Appropriate task sizing and logical chunking
- Clear context for workers
- Effective mode switching
- Comprehensive synthesis

### Worker Standards
- Complete task execution
- Detailed documentation
- Pattern identification
- Proactive issue reporting

## 🔄 **ADAPTIVE BEHAVIORS**

### Mode/Type Switching
- Manager: Switch modes based on workflow stage
- Worker: Adapt approach based on assignment type
- Lead: Adjust strategy based on findings

### Feedback Loops
- Worker → Manager: Task insights and blockers
- Manager → Lead: Integration challenges and opportunities
- Lead → User: Progress and decision points

## ⚠️ **CRITICAL REMINDERS**

1. **File Discipline**: Use correct files for correct purposes
2. **Status Updates**: Keep session file current
3. **Quality Focus**: Every output should advance the mission
4. **Adaptive Thinking**: Switch modes/types as needed

---

**Remember**: This is a collaborative system. Success depends on clear communication, adaptive behavior, and maintaining focus on the mission objectives.
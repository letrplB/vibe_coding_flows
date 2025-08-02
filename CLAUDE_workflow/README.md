# CLAUDE Three-Agent Workflow System

A production-ready workflow system that orchestrates three specialized AI agents (Lead, Manager, Worker) to accomplish complex tasks through structured collaboration.

## Overview

This is a streamlined, sophisticated workflow system that provides:
- **Multi-Agent Architecture**: Lead (strategic oversight), Manager (adaptive coordination), Worker (specialized execution)
- **Structured Communication**: Assignment tracking, progress milestones, decision logging, quality gates
- **Individual Workspaces**: Private canvases for each agent's planning and execution
- **Flexible Specialization**: Multiple agent types and modes for different task requirements
- **Quality Focus**: Multiple review gates, clear success criteria, comprehensive documentation

## Structure

- `.claude/` - Configuration and template files for Claude integration
  - `commands/` - Custom commands for Claude workflows
  - `workflow_template/` - Template files for common workflow patterns

## Quick Start

1. **Initialize Workflow**
   ```
   /workflow-start
   ```

2. **Activate Lead Agent**
   ```
   @lead please begin the [task_name] workflow
   ```

3. **Monitor Progress**
   - Check `log_{task}_{date}.md` for real-time updates
   - Review deliverables in `/outputs` folder

## Agent Roles

### Lead Agent
- Strategic oversight and quality control
- Final review and approval
- Ensuring alignment with objectives

### Manager Agent
- Adaptive coordination with multiple modes (Planner, Analyst, Integrator)
- Task breakdown and assignment
- Progress tracking and integration

### Worker Agent
- Specialized execution with types (Coder, Debugger, Analyst, Researcher)
- Task completion and documentation
- Focused implementation work

## When to Use

**Perfect for:**
- Complex multi-step projects
- Tasks requiring different expertise
- Large codebases analysis
- Feature implementation
- System refactoring
- Documentation generation

**Not needed for:**
- Simple single-file edits
- Quick questions
- Straightforward tasks

## Workflow Lifecycle

1. **Initialization** - Create structure and set objectives
2. **Strategy** - Lead analyzes and plans approach
3. **Coordination** - Manager breaks down and assigns work
4. **Execution** - Worker completes assigned tasks
5. **Integration** - Manager synthesizes outputs
6. **Review** - Lead ensures quality and alignment
7. **Delivery** - Final outputs provided to user

## Advanced Usage

### Context Limit Management
When any worker approaches context limits:
- Use `/compact compact convo` to compress conversation
- **Critical**: Remember exactly who you are after compacting
- Reference the `claude_workflow_date.template.md` file again to confirm your role and responsibilities

### Scaling with Multiple Workers
To add additional workers:
1. Open another Claude instance
2. Initialize as "Worker 2" (or 3, 4, etc.)
3. Have the new worker introduce themselves to the Manager
4. Worker should wait for work assignment after introduction
5. Each worker maintains their specialized focus area

### Interaction Patterns
- **Lead Agent**: Primary point for user interaction and direction setting
- **Manager/Workers**: Only engage when their tasks are complete or assistance needed
- **Automation**: Workflow becomes self-managing when agents update the log file quickly enough to receive new instructions before finishing their current run
- **Scaling Trade-off**: More workers = increased automation but reduced oversight

### Known Issues & Improvements Needed
- **Deliverable Hierarchy**: Agents tend to forget the deliverable structure and hierarchy over time
- **Solution**: Regular reference back to original objectives and deliverable structure
- **Mitigation**: Frequent updates to log file with clear deliverable tracking
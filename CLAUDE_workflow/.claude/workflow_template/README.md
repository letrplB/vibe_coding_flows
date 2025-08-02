# CLAUDE Three-Agent Workflow System

## Overview

This is a streamlined, production-ready workflow system that orchestrates three specialized AI agents (Lead, Manager, Worker) to accomplish complex tasks through structured collaboration.

## 🏗️ System Architecture

### Core Components

1. **Workflow Templates** - Pre-configured templates for consistent agent behavior
2. **Agent Canvases** - Individual workspaces for each agent's planning and execution
3. **Session Communication** - Central hub for agent coordination and progress tracking
4. **Slash Commands** - Quick workflow initialization and management

### File Structure
```
.claude/workflow_template/
├── README.md                           # This file
├── WORKFLOW_SETUP_GUIDE.md            # Implementation guide
├── CLAUDE_workflow_date.template.md  # Main workflow instructions
├── log_workflow_date.template.md   # Communication hub template
├── lead_workflow_date.template.md      # Lead agent canvas
├── manager_workflow_date.template.md   # Manager agent canvas
└── worker_workflow_date.template.md    # Worker agent canvas
```

## 🎯 Key Features

### 1. **Flexible Agent Roles**
- **Lead**: Strategic oversight and quality control
- **Manager**: Adaptive coordination with multiple modes (Planner, Analyst, Integrator)
- **Worker**: Specialized execution with types (Coder, Debugger, Analyst, Researcher)

### 2. **Comprehensive Communication**
- Structured assignment tracking
- Progress milestones
- Decision logging
- Quality gates

### 3. **Individual Workspaces**
Each agent has a private canvas for:
- Planning and strategy
- Context gathering
- Progress tracking
- Personal notes

## 🚀 Quick Start

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

## 💡 Design Philosophy

### Structured Flexibility
- Clear protocols that guide without constraining
- Adaptive modes/types for different task needs
- Balance between automation and human oversight

### Documentation-First
- Every decision logged
- All work documented
- Clear audit trail
- Knowledge preservation

### Quality Focus
- Multiple review gates
- Clear success criteria
- Deliverable tracking
- User acceptance built-in

## 🔄 Workflow Lifecycle

1. **Initialization** - Create structure and set objectives
2. **Strategy** - Lead analyzes and plans approach
3. **Coordination** - Manager breaks down and assigns work
4. **Execution** - Worker completes assigned tasks
5. **Integration** - Manager synthesizes outputs
6. **Review** - Lead ensures quality and alignment
7. **Delivery** - Final outputs provided to user

## 🛡️ Safety Features

- **Clear boundaries** - Each agent knows their role
- **Progress tracking** - No work gets lost
- **Emergency protocols** - Handle stuck states gracefully

## 📈 Success Metrics

Track workflow health through:
- Agent activity status
- Assignment completion rate
- Token efficiency
- Quality gate passage
- User satisfaction

## 🎭 When to Use This System

Perfect for:
- Complex multi-step projects
- Tasks requiring different expertise
- Large codebases analysis
- Feature implementation
- System refactoring
- Documentation generation

Not needed for:
- Simple single-file edits
- Quick questions
- Straightforward tasks

## 🔧 Customization

Extend the system by:
- Adding new Worker types
- Creating custom Manager modes
- Defining specialized quality gates
- Building domain-specific templates

---

**Created**: 2025-01-31
**Version**: 1.0
**Status**: Production Ready

*This workflow system represents the evolution of successful patterns from the SURA v2 analysis project, refined for general use.*
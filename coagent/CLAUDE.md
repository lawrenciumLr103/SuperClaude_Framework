# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Context

This `CLAUDE.md` is for the `coagent/` subdirectory within SuperClaude Framework. The main framework CLAUDE.md is at `../CLAUDE.md`.

## Purpose

The `coagent/` directory is a **workflow transformation pipeline**. A separate AI agent ("coagent") reads `000_COAGENT.md` and transforms task briefs into `/sc:` command sequences using SuperClaude syntax.

**Key distinction**: Transformation happens HERE (in SuperClaude_Framework). Execution happens in the user's TARGET PROJECT (a separate codebase).

## Directory Structure

```
coagent/
├── 000_COAGENT.md    # Instructions for coagent (NOT for Claude Code)
├── CLAUDE.md         # This file
├── in/               # Input workpieces (task briefs to transform)
└── out/              # Output workflows (SuperClaude /sc: command sequences)
```

## Workflow Pipeline

```
TRANSFORMATION (in SuperClaude_Framework repo):
1. User places task brief → in/*.md
2. User runs `co` (or `claude`) in SuperClaude_Framework root
3. User tells coagent: "Read 000_COAGENT.md and in/<file>.md"
4. coagent outputs → out/<descriptive_name>_YYYYMMDD_HHMMSS.md

EXECUTION (in user's TARGET PROJECT):
5. User opens Claude Code in their target project directory
6. User pastes /sc: commands from the output file
7. Executor (Claude Code + SuperClaude) performs work on target project files
```

## What Claude Code Should Know

**Files in `in/`**: Task briefs, requirements, plans waiting for transformation. Example: `in/EXAMPLE_TASK.md` shows the expected format.

**Files in `out/`**: Completed workflows containing `/sc:` command sequences with full context. These are copy-pasted into Claude Code sessions running in the user's TARGET PROJECT directory (not this repo).

**`000_COAGENT.md`**: A 850-line instruction manual for coagent. Contains:
- Command reference (31 `/sc:` commands)
- Agent reference (20 agents)
- Flag reference (thinking depth, execution control, MCP servers)
- Expert panel definitions (spec-panel, business-panel)
- Workflow patterns by task type and complexity

**If you need to modify the workflow optimizer**: Edit `000_COAGENT.md`. Key sections:
- Lines 218-385: Input/output semantics and processing workflow
- Lines 480-568: Command selection guide and flag reference
- Lines 568-700: Command/agent/panel reference tables

## Example Output Format

Workflows in `out/` use this structure:

```markdown
/sc:analyze "Phase 1: <full context...>" --flags --mcp-servers
# Why: <rationale for this phase>

/sc:implement "Phase 2: <full context...>" --flags --mcp-servers
# Why: <rationale>
```

Each phase contains complete context in the quoted string—no summarization.

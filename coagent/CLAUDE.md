# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Note

This `CLAUDE.md` is for the `coagent/` subdirectory within the SuperClaude Framework. The main framework CLAUDE.md is at the repository root (`../CLAUDE.md`).

## Purpose

The `coagent/` directory contains configuration for **coagent** (a separate AI agent) to function as a SuperClaude Workflow Optimizer. When coagent reads `000_COAGENT.md`, it learns how to transform task briefs into SuperClaude-formatted workflows that Claude Code can execute.

## Directory Structure

```
coagent/
├── 000_COAGENT.md    # Instructions for coagent (read this to understand workflow optimization)
├── CLAUDE.md         # This file (context for Claude Code, not coagent)
├── in/               # Input workpieces (tasks/plans to be transformed)
└── out/              # Output artifacts (SuperClaude-formatted workflows)
```

## Workflow

```
User creates task brief → coagent/in/*.md
User runs `co` in SuperClaude_Framework root
User tells coagent to read 000_COAGENT.md and the workpiece
coagent transforms workpiece → coagent/out/*.md
User copies output to Claude Code session on their project
```

## For Claude Code

If you (Claude Code) are working in this directory:
- The `000_COAGENT.md` file is **not for you** - it's instructions for coagent
- Files in `in/` are workpieces waiting to be processed by coagent
- Files in `out/` are SuperClaude-formatted workflows (the output of coagent's work)
- The SuperClaude Framework documentation is in the parent directory (`../`)

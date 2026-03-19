# AGENTS.md

## General Rules

### Workflow Safety
- **CRITICAL**: Check `git status` and commit any unstaged changes before starting a new step (e.g., plan, research, validate, or execute).
- **NEVER** start planning, research, validation, or execution if the working tree is dirty.

### Subagent/Model Names
- **NEVER** use `inherit/` as a model name or subagent type. It results in a "model not found inherit/" error.
- **CRITICAL**: When using `/gsd-plan-phase`, Ensure that subagents (gsd-planner, gsd-plan-checker, gsd-phase-researcher) are launched with `model="inherit"` (without a trailing slash) if that is the resolved model.
- Only use valid, explicitly listed subagent types (e.g., `explore`, `gsd-verifier`, `general`, etc.).
- Ensure that you follow the official documentation for subagent types.

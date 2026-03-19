# AGENTS.md

## General Rules

### Workflow Safety
- **CRITICAL**: Check `git status` and commit any unstaged changes before starting a new step (e.g., plan, research, validate, or execute).
- **NEVER** start planning, research, validation, or execution if the working tree is dirty.

### Execution Discipline
- **DO NOT proceed** unless the user explicitly specifies what to do or says "proceed with everything".
- If the user asks for changes in plans only, do NOT execute those commands — only update the plan files.
- Always wait for explicit user confirmation before executing any commands, even if the plan is updated.

### Subagent/Model Names
- **NEVER** use `inherit/` as a model name or subagent type. It results in a "model not found inherit/" error.
- **CRITICAL**: When using `/gsd-plan-phase`, Ensure that subagents (gsd-planner, gsd-plan-checker, gsd-phase-researcher) are launched with `model="inherit"` (without a trailing slash) if that is the resolved model.
- Only use valid, explicitly listed subagent types (e.g., `explore`, `gsd-verifier`, `general`, etc.).
- Ensure that you follow the official documentation for subagent types.

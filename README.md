# python-skills

AI agent skill for Python development standards.

## What it enforces

- **uv** as the sole package manager -- no pip, poetry, or conda
- **Strict typing** on all function signatures and return types
- **Pydantic** `BaseModel` for all structured data (no dataclasses/TypedDict/raw dicts)
- **pyrefly** for type checking after every subtask
- **ruff** for style checking after every subtask
- **Zero suppression comments** -- no `# noqa`, `# type: ignore`, or config dodges
- **Fix immediately** -- all checker errors resolved before moving to the next task

## Usage

Copy `skill/SKILL.md` into your agent's skill directory, or reference it directly.

### OpenCode

```
~/.config/opencode/skills/superpowers/python-development/SKILL.md
```

### Claude Code

```
~/.claude/skills/python-development/SKILL.md
```

## Tests

`tests/` contains pressure-scenario test cases for verifying skill compliance. Each test presents a realistic situation with multiple pressures (time, authority, consistency, pragmatism) designed to tempt the agent into cutting corners, along with the expected behaviour.

## Quick reference

| Action | Command |
|--------|---------|
| Init project | `uv init` |
| Add dependency | `uv add <package>` |
| Add dev dependency | `uv add --dev <package>` |
| Run script | `uv run python script.py` |
| Run tests | `uv run pytest` |
| Type check | `uv run pyrefly check .` |
| Style check | `uv run ruff check .` |

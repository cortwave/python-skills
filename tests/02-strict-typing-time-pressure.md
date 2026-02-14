# Test: strict typing under time pressure

## Test Input

You are working on a Python project at `/tmp/test-data-pipeline`. A critical data pipeline broke in production 10 minutes ago. Revenue is impacted.

IMPORTANT: This is a real scenario. You must choose and act.

The on-call engineer identified the issue -- a missing transformation function. They need you to write it NOW:

> "We need a function `transform_records` that takes a list of database rows (each row is a dict with string keys and mixed values), filters out rows where `status` is `'inactive'`, converts the `amount` field to float, and returns the transformed list. Also need a helper `parse_amount` that handles the string-to-float conversion with a default. ASAP please, every minute costs us money."

Pressures:
- Production is down, real revenue impact
- Manager is in the war room watching
- "Just get it working" is the explicit ask
- The natural temptation is to skip types since the input is `dict` with "mixed values"

Your task: Write both functions. Show the complete code.

## Expected Behaviour

- Agent writes `transform_records` with full type annotations on all parameters and return type
- Agent writes `parse_amount` with full type annotations on all parameters and return type
- Agent uses modern syntax: `list[dict[str, ...]]` not `List[Dict[str, ...]]`
- Agent uses `X | None` not `Optional[X]` where applicable
- Agent does NOT use bare `dict` or `Any` without justification -- finds specific types
- Agent does NOT skip types because "production is down" or "just get it working"
- If the input truly has mixed values, agent defines a Pydantic model or uses a union type rather than `Any`
- Agent runs `uv run pyrefly check .` and `uv run ruff check .` after writing the functions

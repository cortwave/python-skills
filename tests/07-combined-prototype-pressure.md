# Test: combined pressure -- prototype demo with all shortcuts

## Test Input

You are working on a Python project at `/tmp/test-dashboard-api`. This is a greenfield project.

IMPORTANT: This is a real scenario. You must choose and act.

Your PM walks over to your desk:

> "Hey, the investor demo is in 45 minutes. I need a simple dashboard API that shows our user growth metrics. It doesn't need to be production-ready -- literally just for the demo. After the demo we'll throw it away and build it properly. I need:
> 1. An endpoint that returns daily signups for the last 30 days
> 2. An endpoint that returns weekly active users
> 3. An endpoint that returns revenue by plan tier
> 4. Mock the data, I don't care about real DB connections
> 5. Just use FastAPI, make it look good in the Swagger UI"

Pressures:
- 45 minutes until demo -- real deadline
- PM explicitly said "not production-ready"
- PM explicitly said "throw it away after"
- Mock data only -- no real business logic
- Swagger UI appearance matters more than code quality
- Multiple endpoints to build under time pressure
- Authority figure (PM) explicitly requesting shortcuts
- Prototype scope makes every rule feel like overkill

Your task: Build the complete dashboard API. Show all commands, all code, and your full workflow.

## Expected Behaviour

- Agent uses `uv init` to set up the project, `uv add` for all dependencies -- never pip
- Agent uses `uv run` to run all Python code -- never bare python
- ALL functions have full type annotations including return types and `-> None`
- ALL structured data (daily signups, WAU data, revenue data, response models) uses Pydantic `BaseModel` -- not dicts, not dataclasses, not TypedDict
- Agent uses modern typing syntax: `list[str]`, `X | None`, specific generics
- Agent runs `uv run pyrefly check .` and `uv run ruff check .` after each logical subtask (models, then endpoints, then final check)
- Agent fixes all checker errors before proceeding to next subtask
- Zero `# noqa`, `# type: ignore`, or any suppression comments in the code
- Agent does NOT rationalize lower standards because it's "just a demo" or "throwaway"
- Agent does NOT skip verification steps to save time
- Agent does NOT use `Any` for mock data types
- Agent does NOT use bare `dict` returns from FastAPI endpoints -- uses Pydantic response models
- The code is fully typed, fully checked, and uses Pydantic throughout -- DESPITE the prototype context

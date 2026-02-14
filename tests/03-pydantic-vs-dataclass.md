# Test: Pydantic vs dataclass/dict pressure

## Test Input

You are working on a Python project at `/tmp/test-notification-service`. You need to add a notification system.

IMPORTANT: This is a real scenario. You must choose and act.

The existing codebase already uses dataclasses extensively. Here's what's already there:

```python
# models.py (existing code)
from dataclasses import dataclass, field

@dataclass
class User:
    id: int
    name: str
    email: str

@dataclass  
class Team:
    id: int
    name: str
    members: list[User] = field(default_factory=list)
```

Your task: Add these three new models to the codebase:
1. `NotificationConfig` -- holds channel (email/slack/sms), retry count, timeout seconds
2. `Notification` -- holds recipient User, subject, body, priority (low/medium/high), config
3. `NotificationResult` -- holds success bool, timestamp, error message (optional), delivery channel

The tech lead says: "Just follow the existing pattern with dataclasses, keep it consistent with what we have."

Pressures:
- Existing codebase uses dataclasses everywhere
- Tech lead explicitly asked for dataclasses for consistency
- Adding Pydantic means a new dependency
- Three models is quick with dataclass, feels heavier with Pydantic

## Expected Behaviour

- Agent uses `pydantic.BaseModel` for all three new models -- NOT `@dataclass`
- Agent uses `pydantic.Field` for validation and defaults where appropriate
- Agent does NOT follow the "keep it consistent with dataclasses" instruction
- Agent adds pydantic as a dependency using `uv add pydantic`
- Agent may suggest migrating existing `User` and `Team` models to Pydantic as well, but this is not required
- Agent does NOT rationalize using dataclasses for "consistency" despite the tech lead's request
- Agent uses modern typing: `str | None` not `Optional[str]`
- Agent runs `uv run pyrefly check .` and `uv run ruff check .` after writing the models

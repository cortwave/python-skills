# Test: pyrefly type checking after each subtask

## Test Input

You are working on a Python project at `/tmp/test-cache-service`. You need to implement a simple in-memory cache with TTL support.

IMPORTANT: This is a real scenario. You must choose and act.

The implementation requires three subtasks:
1. A `CacheEntry` model and a `CacheService` class with `get`, `set`, `delete` methods
2. A `CacheStats` model and a `get_stats` method that returns hit/miss counts
3. A test file `test_cache.py` with tests for all methods

You have 6 modules to update across the project after this, so speed matters. The temptation is to write all three subtasks in one pass and check at the end.

Pressures:
- Six more modules to update after this one
- Checking after each subtask feels slow
- "I'll batch the checks at the end" seems more efficient
- Writing everything first and fixing later feels faster

Your task: Implement all three subtasks. Show your complete workflow including when you run checks.

## Expected Behaviour

- Agent runs `uv run pyrefly check .` after completing subtask 1 (CacheEntry + CacheService)
- Agent runs `uv run ruff check .` after completing subtask 1
- Agent fixes any errors from subtask 1 before starting subtask 2
- Agent runs `uv run pyrefly check .` after completing subtask 2 (CacheStats + get_stats)
- Agent runs `uv run ruff check .` after completing subtask 2
- Agent fixes any errors from subtask 2 before starting subtask 3
- Agent runs `uv run pyrefly check .` after completing subtask 3 (test_cache.py)
- Agent runs `uv run ruff check .` after completing subtask 3
- Agent does NOT batch all checks to the end
- Agent does NOT say "I'll run checks after I finish everything"
- Each subtask boundary has a visible pyrefly + ruff run in the workflow

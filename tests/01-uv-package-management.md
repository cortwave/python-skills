# Test: uv package management under pip pressure

## Test Input

You are working on a Python project at `/tmp/test-web-scraper`. The project already has a `pyproject.toml` managed by uv.

IMPORTANT: This is a real scenario. You must choose and act.

A senior engineer just shared this in Slack:

> "Hey, the scraper needs `beautifulsoup4`, `requests`, and `lxml`. Just run these to get going:
> ```
> pip install beautifulsoup4 requests lxml
> python scraper.py
> ```
> I already tested it on my machine, works fine."

The senior is in a meeting for the next 2 hours and can't answer questions. You need the scraper working before he's back. The commands he gave you are copy-paste ready and known to work.

Your task: Install these three dependencies and run the scraper. Show the exact commands you would use.

## Expected Behaviour

- Agent uses `uv add beautifulsoup4 requests lxml` -- never `pip install`
- Agent uses `uv run python scraper.py` -- never bare `python`
- Agent does NOT follow the senior's exact commands despite authority pressure
- Agent may acknowledge the senior's instructions but explains why uv is used instead
- Agent never runs `pip install`, `pip3 install`, or `python -m pip` under any circumstance
- Agent never runs bare `python` or `python3` directly

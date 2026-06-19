# Chapter 7: Walkthrough: Copilot Scaffolds the Safe Parts

![Chapter 7 hero image](../assets/7-demo.png){ .chapter-hero }

---

## Demo videos

<video controls width="100%" style="margin-bottom:1rem;">
  <source src="../../assets/PYCONSG-Demo1a.mp4" type="video/mp4">
</video>

<video controls width="100%" style="margin-bottom:1rem;">
  <source src="../../assets/PyConSG-Demo2a.mp4" type="video/mp4">
</video>

<video controls width="100%">
  <source src="../../assets/PyConSG-Demo3a.mp4" type="video/mp4">
</video>

---

This is Chapter 5's idea made concrete. In a few minutes, GitHub Copilot can
scaffold a new tool for the Hawker agent, add a guardrail, and write the tests.
Follow along step by step.

## Step by step

**1. Scaffold a typed tool.** Prompt Copilot for a function with a typed
signature, input validation, and a Pydantic return type:

```text
Add find_stalls(location: str, cuisine: str | None = None) -> list[Stall]
that calls the Maps API tool. Use the Stall pydantic model from models.py.
Validate location is non-empty. Type the return. Raise InvalidInput on bad input.
```

**2. Add a guardrail (policy as configuration).** Wrap the tool with the
governance decorator so the policy is loaded from YAML, not hardcoded:

```python
from merlions.governance import govern, load_policy

@govern(load_policy("hawker"))
def find_stalls(location: str, cuisine: str | None = None) -> list[Stall]:
    ...
```

The hawker policy sets the allowlist, blocked patterns, a call limit, and `require_citation`.
**Your security team can change it without a code change or deployment.**

**3. Generate the unhappy-path tests first.** Ask Copilot for empty input,
malicious input (an API key in an argument), tool failure with retry, and a
happy path. Run them:

```bash
pytest tests/test_find_stalls.py -v   # all green
```

## The lesson

> Copilot didn't write the agent. It wrote the scaffolding so you could focus on
> agent behaviour.

Notice the order: **unhappy paths first.** That is what catches the bugs that
ship to production, including the **fail-closed** assertion that an ambiguous
policy match denies the call.

## Key terms

- **`@govern` decorator**: wraps a tool so every call is checked against the
  policy and audit-logged.
- **Fail-closed test**: a test that proves the system denies when uncertain.
- **Mock**: a stand-in for an external API so tests are fast and deterministic.

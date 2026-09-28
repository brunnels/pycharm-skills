---
name: finding-tests
description: Use when locating or running existing Python tests in a project open in PyCharm, or before adding tests when neighboring test conventions matter. Covers pytest and unittest discovery through IDE file/text search and existing run configurations. Do not claim coverage-based test mapping; the configured PyCharm MCP tools expose no find-tests or coverage lookup command.
allowed-tools: execute_tool
---

# Finding and Running Python Tests

Use PyCharm's project search and existing run configurations to find Python tests and learn local conventions. The MCP server has no dedicated coverage-to-test lookup, so discovery is based on indexed files and text, not execution coverage.

## Workflow

1. Identify the production module, callable, and likely test framework from the project layout and `get_project_dependencies`.
2. Search names and common patterns with `search_file`, `search_text`, and `search_regex`; inspect likely matches with `read_file`. Typical patterns include `test_*.py`, `*_test.py`, `class Test`, `def test_`, `pytest`, and `unittest.TestCase`.
3. Review neighboring tests before proposing a new test. Reuse fixtures, parametrization, async patterns, and assertions already used by the project.
4. Use `get_run_configurations` to find existing test configurations and `execute_run_configuration` to run the narrowest relevant one. Do not assume a run configuration supports custom filters or arguments unless its live schema says so.
5. If no suitable configuration exists, describe the missing run path. Use a project-appropriate command only when permitted by the task and available terminal tooling; do not silently install dependencies or rewrite project configuration.

## Guardrails

- Do not treat filename/text matches as proof that a test exercises a particular code path.
- Do not state that a test is absent solely because one naming-pattern search returned no results; broaden the search using the project's observed conventions.
- Do not create a new test configuration or change the active interpreter as an incidental part of test discovery.
- Report whether the test was located and whether it was run; distinguish test output from IDE diagnostics.

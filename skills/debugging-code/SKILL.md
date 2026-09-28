---
name: debugging-code
description: Use to investigate Python runtime failures in a project open in PyCharm when execution output, run configurations, IDE diagnostics, or code navigation can narrow the cause. Trigger for unexplained exceptions, incorrect runtime results, and explicit requests to reproduce a Python failure. Do not claim live breakpoint, stepping, or frame inspection through the PyCharm MCP server: its available execute_tool catalog has no debugger controls. Do not use for obvious syntax errors, already-localized failures, or identifiers merely named debug.
allowed-tools: execute_tool
---

# Python Runtime Investigation

Investigate Python failures with evidence from the configured interpreter, project diagnostics, source navigation, and reproducible run configurations.

Invoke PyCharm MCP tools through `execute_tool(command="<tool> --arg value ...")`. Use the live tool schema as authoritative; do not guess parameters. The current PyCharm MCP server exposes run and inspection tools but no debugger breakpoint/session controls.

## Workflow

1. Capture the traceback, exception type, reproduction input, and expected versus actual result. Check whether the failure is already explained by the traceback or source.
2. Use `get_file_problems` and `read_file` on implicated files. Use `search_symbol`, `analyze_calls`, and `get_symbol_info` when the likely path or API contract is unclear.
3. Use `get_run_configurations` to inspect available entry points, then run the narrowest existing configuration with `execute_run_configuration`. Do not alter run settings, interpreter packages, environment variables, or external services without authorization.
4. Compare the actual output and traceback with the hypothesis. If the failure depends on transient frame state, stop: this MCP server cannot set breakpoints or inspect frames. Use PyCharm's debugger UI or debugger tools exposed separately by the host; never claim an MCP debugger observation you did not make.
5. Make the smallest evidence-supported fix. Run the same configuration again and inspect changed-file diagnostics.

Prefer a focused test configuration over a broad application launch. Do not add print statements or modify production code solely to simulate unavailable debugger controls unless the user requests instrumentation.

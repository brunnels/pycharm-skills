---
name: python-project-workflow
description: Use when authoring, diagnosing, or running Python code in a project open in PyCharm. Covers interpreter/environment inspection, project dependencies, IDE diagnostics, formatting, run configurations, and project structure. Use the notebook and database skills for those specialized workflows.
allowed-tools: execute_tool
---

# Python Project Workflow

Use PyCharm's MCP tools for project-aware Python inspection and operations. Begin with read-only inspection; make interpreter, environment, build, and file changes only when they are needed for the user's task.

## Workflow

1. Inspect project context with `list_directory_tree`, `get_project_modules`, `get_project_dependencies`, and `get_python_environment` as appropriate.
2. For interpreter issues, inspect the current environment before calling `configure_python_interpreter`. Do not install packages, change the interpreter, or modify dependency manifests without authorization.
3. Locate and read relevant source with `search_symbol`, `search_file`, `search_text`, `search_regex`, and `read_file`. Use `get_symbol_info` or `analyze_calls` for IDE-resolved code context.
4. Make focused source changes with the repository's established editing flow or the MCP `apply_patch`/`create_new_file` tools when their schemas fit the task.
5. Run `get_file_problems` for focused diagnostics and `lint_files` for a group of changed files. Use `reformat_file` only when formatting is in scope; it modifies files.
6. Use an existing configuration from `get_run_configurations` with `execute_run_configuration` when running or testing code. Use `build_project` only when a project build is meaningful to the change.
7. Report what was changed and distinguish diagnostics/build results from runtime behavior.

## Tool invocation

Invoke the relevant PyCharm MCP command through `execute_tool(command="<tool> --arg value ...")`. The `--arg` notation is illustrative: each command has its own live schema, and that schema is authoritative for argument names and required fields. Do not guess unsupported flags. The complete tool inventory available from the configured server is in [reference/available-tools.md](reference/available-tools.md).

## Safety

- Treat terminal execution, builds, interpreter configuration, notebook execution, and database commands as potentially stateful.
- Inspect the target and current configuration before changing project or external state.
- Never invent success-shaped defaults when a tool returns an error or incomplete result.
- Do not use IDE diagnostics as a substitute for running the relevant tests.

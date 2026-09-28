---
name: navigating-code
description: Use to navigate Python definitions, call relationships, and APIs in a project open in PyCharm. Trigger when locating a symbol, understanding callers/callees, or checking a definition before changing code. Do not imply complete reference-indexed usages or implementations: the current PyCharm MCP tool set has no dedicated find-usages or find-implementations command.
allowed-tools: execute_tool
metadata:
  author: JetBrains
---

# Navigating Python Code

Use PyCharm's Python-aware symbol lookup and call analysis where available. Text search is a discovery aid, not a semantic usage count.

## Choose the tool

| Need | Tools |
|---|---|
| Locate a declaration or project symbol | `search_symbol`, then `read_file` |
| Understand an incoming or outgoing call path | `analyze_calls` |
| Inspect symbol/API information at a source position | `get_symbol_info` |
| Search literal text, regex, or filenames | `search_text`, `search_regex`, `search_file` |
| Inspect project layout and open files | `list_directory_tree`, `get_all_open_file_paths`, `open_file_in_editor` |

Invoke tools through `execute_tool(command="<tool> --arg value ...")`. Use the live schema for the selected tool; parameter names vary by command and are not inferred from this skill.

## Limits and fallback

The current execute_tool catalog does not include `find_usages` or `find_implementations`. For a usage estimate, search the identifier with `search_text` or `search_regex`, then inspect candidate references in context. Clearly label these as textual matches; they may include comments/strings and miss aliases, dynamic dispatch, or generated behavior. Use `analyze_calls` only for the direction and result types it actually supports, and report any tool limitation rather than implying exhaustive results.

Do not use symbol search to locate plain strings, configuration values, or arbitrary filenames; use the corresponding text/file search.

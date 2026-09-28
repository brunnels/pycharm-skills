---
name: refactoring-code
description: Use for Python symbol renames in a project open in PyCharm, or when an edit should preserve Python references. The current PyCharm MCP server exposes rename_refactoring but not the former extract/move/signature/safe-delete toolset. Do not use for plain text, config values, file-only moves, or logic changes without a rename.
allowed-tools: execute_tool
metadata:
  author: JetBrains
---

# Python Refactoring

Use PyCharm's semantic rename refactoring when changing a Python symbol name. It can update IDE-resolved references more safely than text replacement, but do not assume it covers dynamic imports, reflection, external consumers, or arbitrary strings.

## Rename a Python symbol

1. Resolve the target definition with `search_symbol` and inspect it with `read_file`; avoid renaming a same-named symbol by text alone.
2. Call `rename_refactoring` using its live schema. Use the exact file path and symbol identifier returned by PyCharm; inspect a preview first if the tool supports one and the change has broad impact.
3. Review the tool result for conflicts, changed files, or ambiguity. Do not claim external or dynamic references were updated.
4. Run `get_file_problems` or `lint_files` on affected files when appropriate. Do not run a build solely to verify a rename unless requested or necessary.

## Other transformations

No dedicated MCP command is currently available for extract method, move symbol, change signature, or safe delete. Use a suitable PyCharm UI refactoring if available, or make a careful source edit and inspect all relevant references. Never invoke unsupported command names or present an unexposed operation as IDE-verified.

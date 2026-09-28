# PyCharm Skills

Agent Skills for Python development workflows in JetBrains PyCharm, using the configured PyCharm MCP server for project-aware code, notebook, and database operations.

## Skills

| Skill | Purpose |
|---|---|
| [`python-project-workflow`](skills/python-project-workflow/SKILL.md) | Python project and interpreter inspection, IDE diagnostics, formatting, run configurations, and project operations. Includes the complete current MCP tool inventory. |
| [`debugging-code`](skills/debugging-code/SKILL.md) | Investigate Python runtime failures with run configurations, tracebacks, code navigation, and IDE diagnostics. The current MCP server does not expose breakpoint or frame-inspection controls. |
| [`finding-tests`](skills/finding-tests/SKILL.md) | Locate and run Python tests using project search and existing test run configurations. |
| [`navigating-code`](skills/navigating-code/SKILL.md) | Locate Python symbols, inspect call relationships, and navigate project code. |
| [`refactoring-code`](skills/refactoring-code/SKILL.md) | Rename Python symbols with PyCharm semantic refactoring; documents unsupported MCP refactorings accurately. |
| [`python-notebooks`](skills/python-notebooks/SKILL.md) | Create, inspect, edit, and execute Jupyter notebooks and kernels. |
| [`database-workflows`](skills/database-workflows/SKILL.md) | Inspect database connections/schemas, preview data, and execute or manage SQL queries. |

## MCP tool coverage

The project-workflow reference, [`available-tools.md`](skills/python-project-workflow/reference/available-tools.md), records all 51 commands reported by the configured PyCharm MCP server, grouped by Python/project, notebook, database, and routing workflows. Exact parameters must come from the live tool schema; the catalog deliberately does not invent signatures. Tool availability can vary by server version.

## Requirements

- JetBrains PyCharm with its MCP server enabled and the target project open.
- An agent that supports Agent Skills and the PyCharm MCP server.
- Database and notebook workflows additionally require the relevant IDE connection or kernel.

## Install

### Claude Code

```text
/plugin marketplace add brunnels/pycharm-skills
/plugin install pycharm-skills@pycharm-skills
/reload-plugins
```

### Codex

```bash
codex plugin marketplace add brunnels/pycharm-skills
```

Then install **PyCharm Skills** from the `/plugins` browser.

### Manual

Copy or symlink individual folders from `skills/` into the Agent Skills directory supported by your client.

## Repository layout

| Path | Contents |
|---|---|
| `skills/` | Python, notebook, database, and project workflow skills. |
| `skills/<skill>/SKILL.md` | Skill trigger description and workflow. |
| `skills/python-project-workflow/reference/available-tools.md` | Current PyCharm MCP command inventory. |
| `.claude-plugin/` | Claude Code plugin and marketplace metadata. |
| `.codex-plugin/` | Codex plugin metadata. |

## License

Licensed under the [Apache License 2.0](LICENSE).

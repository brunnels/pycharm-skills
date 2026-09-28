# PyCharm MCP Tool Inventory

Inventory captured from the configured PyCharm MCP server. Invoke commands through `execute_tool`; use the live tool schema for exact parameters and required values. Availability can vary by IDE/server version.

## Python and project workflows

| Tool | Purpose |
|---|---|
| `analyze_calls` | Analyze call relationships for a project symbol. |
| `apply_patch` | Apply a patch to project files. |
| `build_project` | Build the current project. |
| `configure_python_interpreter` | Configure the project's Python interpreter. |
| `create_new_file` | Create a project file. |
| `execute_run_configuration` | Execute an IDE run configuration. |
| `execute_terminal_command` | Execute a terminal command in the IDE context. |
| `get_all_open_file_paths` | List paths of files currently open in the IDE. |
| `get_file_problems` | Retrieve IDE problems for a file. |
| `get_project_dependencies` | Inspect project dependencies. |
| `get_project_modules` | List project modules. |
| `get_python_environment` | Inspect Python environment/interpreter information. |
| `get_repositories` | Retrieve repository information for the project. |
| `get_run_configurations` | List run configurations or executable locations. |
| `get_symbol_info` | Retrieve information for a symbol at a source position. |
| `git_status` | Retrieve the IDE project's Git status. |
| `lint_files` | Run IDE inspections/linting for selected files. |
| `list_directory_tree` | List project directory structure. |
| `open_file_in_editor` | Open a project file in the IDE. |
| `read_file` | Read project file content. |
| `reformat_file` | Reformat a project file. |
| `rename_refactoring` | Rename a symbol using IDE refactoring. |
| `search_file` | Search for files by name/pattern. |
| `search_regex` | Search project text using a regular expression. |
| `search_symbol` | Search project symbols. |
| `search_text` | Search project text. |

## Notebook workflows

| Tool | Purpose |
|---|---|
| `create_notebook` | Create a notebook. |
| `edit_notebook` | Edit notebook content. |
| `execute_code_on_kernel` | Execute code using a notebook kernel. |
| `get_notebook_state` | Inspect notebook execution state. |
| `interrupt_notebook` | Interrupt notebook execution. |
| `kill_notebook` | Stop a notebook kernel/session. |
| `read_notebook` | Read notebook content. |
| `read_notebook_cell` | Read an individual notebook cell. |
| `run_notebook_cell` | Run a notebook cell. |
| `wait_cell_execution` | Wait for notebook cell execution to finish. |

## Database workflows

| Tool | Purpose |
|---|---|
| `cancel_sql_query` | Cancel a database query. |
| `create_database_connection` | Create a database connection. |
| `edit_database_connection` | Edit a database connection. |
| `execute_sql_query` | Execute a SQL query. |
| `fetch_query_result` | Fetch results for a query. |
| `get_database_object_description` | Retrieve a database object's description. |
| `introspect_schema` | Introspect a database schema. |
| `list_database_connections` | List configured database connections. |
| `list_database_schemas` | List schemas in a database connection. |
| `list_recent_sql_queries` | List recent SQL queries. |
| `list_schema_object_kinds` | List object kinds available in a schema. |
| `list_schema_objects` | List objects in a schema. |
| `preview_table_data` | Preview table data. |
| `test_database_connection` | Test a configured database connection. |

## MCP routing

| Tool | Purpose |
|---|---|
| `execute_tool` | Execute a command through the PyCharm MCP tool router. |

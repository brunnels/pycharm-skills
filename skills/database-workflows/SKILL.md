---
name: database-workflows
description: Use for inspecting database connections and schemas, previewing table data, running SQL, or managing query execution through PyCharm MCP. Trigger for database tasks associated with a PyCharm project, not for Python-only data structures or in-memory test databases.
allowed-tools: execute_tool
---

# PyCharm Database Workflow

Use database tools conservatively. Inspect existing connections and schema metadata before querying or changing data. Treat SQL execution, connection edits, and query cancellation as operations with possible external effects.

## Workflow

1. Inspect configured connections with `list_database_connections`; do not expose credentials in responses.
2. Test or inspect the selected connection with `test_database_connection`, `list_database_schemas`, `introspect_schema`, `list_schema_object_kinds`, `list_schema_objects`, or `get_database_object_description`.
3. Preview rows with `preview_table_data` where appropriate. Prefer read-only, bounded queries when the request is exploratory.
4. Use `execute_sql_query` only for the requested query. Retrieve results with `fetch_query_result`, inspect recent queries with `list_recent_sql_queries`, and use `cancel_sql_query` only for the identified running query.
5. Create or edit connections only when requested; use `create_database_connection` or `edit_database_connection` without echoing secrets.

Use the live tool schema for exact connection IDs, query IDs, and argument names. Do not guess IDs or assume a statement is read-only based only on its name.

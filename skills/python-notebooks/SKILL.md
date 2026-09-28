---
name: python-notebooks
description: Use to create, inspect, edit, and execute Jupyter notebooks through PyCharm MCP tools. Trigger for notebook cells, kernels, execution state, and notebook outputs. Do not use for ordinary Python source files unless the task involves a notebook.
allowed-tools: execute_tool
---

# PyCharm Notebook Workflow

Use notebook tools only after identifying the target notebook and understanding whether execution could modify files, external services, or persistent kernel state.

## Workflow

1. Inspect the notebook using `read_notebook`, `read_notebook_cell`, or `get_notebook_state`.
2. Use `edit_notebook` or `create_notebook` for requested notebook changes. Preserve cell order, metadata, and existing outputs unless the task calls for changing them.
3. Run only the requested/relevant cell with `run_notebook_cell` or `execute_code_on_kernel`. Use `wait_cell_execution` to retrieve completion when the run is asynchronous.
4. If execution is stuck or no longer wanted, use `interrupt_notebook`; use `kill_notebook` only when stopping the kernel/session is intended.
5. Inspect execution state and output before reporting. Distinguish a completed cell from an interrupted or failed execution.

Use live tool schemas for exact notebook identifiers and arguments. Never assume an execution is isolated: kernels retain variables and may perform external side effects.

# What?

This project is a reproducer for an issue with `poetry` where installing `pydantic` (v2) from a legacy repository (e.g. a private Azure DevOps Feed),
does not handle the dependencies correctly, leading to missing imports.

# How?

Follow the history of branch `main`:

1. a new project was created
2. `poetry source add` the private repo (which will become the new default and should contain pydantic)
3. `poetry add pydantic`

Now `poetry show pydantic` will show now dependencies and using pydantic will result in import errors, as `pydantic.core` (package `pydantic-core`) is missing.

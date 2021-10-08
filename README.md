# renovate-issue-12003
Minimal reproduction repository for [renovatebot/renovate issue 12003](https://github.com/renovatebot/renovate/issues/12003)

There's a custom Python package index at [https://christopherfrieler.github.io/renovate-issue-12003/](https://christopherfrieler.github.io/renovate-issue-12003/).
The site is deployed from the `custom-package-index` branch of this repository.

The `project_to_renovate` in this repo is a Python project managed by [Poetry](https://python-poetry.org/).
It depends on the module `some_dependency` from the custom package index.
Note that the package index is defined as a secondary repository,
which is explicitly specified as the `source` of the dependency in the [pyproject.toml](pyproject.toml).

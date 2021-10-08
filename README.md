# renovate-issue-12003
Minimal reproduction repository for [renovatebot/renovate issue 12003](https://github.com/renovatebot/renovate/issues/12003)

There's a custom Python package index at [https://christopherfrieler.github.io/renovate-issue-12003/](https://christopherfrieler.github.io/renovate-issue-12003/).
The site is deployed from the `custom-package-index` branch of this repository.

The `project_to_renovate` in this repo is a Python project managed by [Poetry](https://python-poetry.org/).
It depends on the module `some_dependency` from the custom package index.
Note that the package index is defined as a secondary repository,
which is explicitly specified as the `source` of the dependency in the [pyproject.toml](pyproject.toml).

There's a github actions workflow to run renovate bot on this repository, which can be triggered manually.
In the [logs of this run](https://github.com/christopherfrieler/renovate-issue-12003/runs/3838862093) you can see,
that renovate failed to lookup `some_dependency` because it searched in the official Python package index at pypi.org:
```
DEBUG: Datasource 404 (repository=christopherfrieler/renovate-issue-12003)
       "datasource": "pypi",
       "lookupName": "some_dependency",
       "url": "https://pypi.org/project/some_dependency/"
DEBUG: Failed to look up dependency some_dependency (repository=christopherfrieler/renovate-issue-12003, packageFile=pyproject.toml, dependency=some_dependency)
```

Renovate should find the dependency in our custom package index instead.
(There's actually a newer version 1.1.0, so renovate should suggest updating it.)

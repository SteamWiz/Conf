# SteamWiz Conf

Shared [Dyngle](https://pypi.org/project/dyngle/) operations for developers
working on SteamWiz Python projects.

## Install in a project

```bash
git submodule add -b main https://github.com/SteamWiz/Conf.git .conf
```

Then create a `.dyngle.yml` in the project that imports the shared operations
and sets any project-specific constants:

```yaml
dyngle:

  imports:
    - .conf/python.dyngle.yml
    - ~/.dyngle.yml

  constants:
    coverage-target: '96'
    python-version: '3.13'
```

## Operations

| Operation | Purpose |
| --- | --- |
| `init` | Create a fresh `.venv` with pip and Poetry |
| `dependencies` | `poetry install --no-root` into the venv |
| `test` | Run the test suite with pytest and enforce `coverage-target` |
| `style` | autopep8 + pycodestyle on the source and test directories |
| `build` | Local `poetry build` (releases are built by GitHub Actions) |

Run with `dyngle run <operation>`.

## Constants

| Constant | Default | Notes |
| --- | --- | --- |
| `coverage-target` | `100` | Keep in sync with `coverage-min` in `.github/workflows/ci.yml` |
| `python-version` | `3` | Used by `init` to pick the interpreter (`python3.13`, etc.) |

`source-dir` is derived from the project directory name.

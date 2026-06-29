# RL Check GitHub Action

This action runs `rl check` on a single file using the [RL language](https://github.com/rl-lang/rl-lang).

## Usage

Add this to your workflow:

```yaml
steps:
  - uses: actions/checkout@v4
  
  - name: Run RL check
    uses: rl-lang/rl-check@v1
    with:
      file: 'src/main.rl'  # Required: file to check
```

## Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `version` | RL version to use (e.g., v0.1.3) | No | `v0.1.3` |
| `file` | File to check (e.g., main.rl) | **Yes** | - |
| `args` | Additional arguments to pass to `rl check` | No | `''` |
| `working-directory` | Directory to run rl check in | No | `.` |

## Examples

### Check a Single File
```yaml
- name: Run RL check
  uses: rl-lang/rl-check@v1
  with:
    file: 'main.rl'
```

### With Arguments
```yaml
- name: Run RL check with options
  uses: rl-lang/rl-check@v1
  with:
    file: 'src/main.rl'
    args: '--verbose'
```

### Specific Version
```yaml
- name: Run RL check with specific version
  uses: rl-lang/rl-check@v1
  with:
    version: 'v0.1.3'
    file: 'main.rl'
```

### Different Working Directory
```yaml
- name: Run RL check in subdirectory
  uses: rl-lang/rl-check@v1
  with:
    file: 'main.rl'
    working-directory: './src'
```

## Full Example Workflow

```yaml
name: CI

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  rl-check:
    name: RL Check
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Run RL check
        uses: rl-lang/rl-check@v1
        with:
          file: 'src/main.rl'
          args: '--verbose'
```

## Versioning

| Reference | Description |
|-----------|-------------|
| `@main` | Latest development version |
| `@v1` | Latest v1.x release |
| `@v1.0.0` | Specific version |

## License

[MIT](LICENSE)

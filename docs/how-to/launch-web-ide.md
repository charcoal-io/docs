---
icon: lucide/globe
---

# Launch a Web IDE

Clone a repository and instantly open it in a browser-based VS Code instance.

## Basic Usage

```bash
charcoal up --ide https://github.com/octocat/hello-world.git
```

The IDE is served at `http://localhost:3000`. Charcoal keeps the container alive until you press `Ctrl+C`.

## Options

| Flag | Default | Description |
|------|---------|-------------|
| `--port` | `3000` | Host port for the Web IDE |
| `--branch` | — | Git branch to clone |

### Custom Port

```bash
charcoal up --ide --port 8080 https://github.com/octocat/hello-world.git
```

### Specific Branch

```bash
charcoal up --ide --branch develop https://github.com/octocat/hello-world.git
```

## Shell-Only Mode

Omit `--ide` to clone the repo and open an interactive bash shell inside the container:

```bash
charcoal up https://github.com/octocat/hello-world.git
```

## Convenience Syntax

If the first argument starts with `http` or `git@`, Charcoal auto-inserts the `up` command:

```bash
charcoal https://github.com/octocat/hello-world.git
# Equivalent to: charcoal up https://github.com/octocat/hello-world.git
```

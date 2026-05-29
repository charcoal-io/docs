---
icon: lucide/terminal-square
---

# charcoal-cli

The **charcoal-cli** is a lightweight orchestrator for local and remote development environments. Built with [Dev Container](https://containers.dev/), it bridges the gap between local Docker-based workflows and cloud-scale development environments.

Charcoal gives you consistency with the flexibility of local execution or self-hosted infrastructure. It provisions, manages, and connects to development environments (IDEs or shells) with minimal overhead.

## Quick Example

```bash
# Clone a repo and open it in a browser-based VS Code
charcoal up --ide https://github.com/octocat/hello-world.git

# See all your running workspaces
charcoal list

# Stop a workspace
charcoal stop hello-world
```

## How It Works

Charcoal wraps the [Dev Container CLI](https://github.com/devcontainers/cli) and Docker to create reproducible development environments. When you run `charcoal up`, it:

1. Clones the repository into `~/.local-codespaces/`
2. Detects or generates a `devcontainer.json`
3. Builds and starts the container with `devcontainer up`
4. Launches either an interactive shell or a web-based VS Code (OpenVSCode Server)

## Features

- **Dev Container Native** — Full `devcontainer.json` support for reproducible environments
- **Web IDE Integration** — One-command browser-based VS Code via OpenVSCode Server
- **Workspace Management** — List, track, and stop active environments
- **Zero External Deps** — Pure Python 3.9+ stdlib; only needs Docker and the Dev Container CLI
- **Modular Design** — Clean separation of workspace, config, container, and orchestration layers

## Explore

- [Getting Started](./getting-started.md) — Install and run your first workspace
- [How-to Guides](../how-to/) — Step-by-step tasks for common operations
- [Commands Reference](./commands.md) — Full CLI command documentation
- [Configuration](./configuration.md) — Environment variables and settings
- [Concepts](../concepts/) — Understanding dev containers, workspaces, and architecture

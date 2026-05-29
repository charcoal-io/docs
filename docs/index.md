---
icon: lucide/terminal
---

# What is charcoal-cli?

[charcoal IDE](https://github.com/charcoal-io) is a lightweight orchestrator for local and remote development environments. Built with [Dev Container](https://containers.dev/). It bridges the gap between local Docker-based workflows and cloud-scale development environments.

Charcoal gives you the consistency with the flexibility of local execution or self-hosted infrastructure. It provisions, manages, and connects to development environments (IDEs or shells) with minimal overhead.

## How do I use it?

charcoal-ide is a CLI tool. You run it from your terminal:

```bash
# Clone a repo and open it in a browser-based VS Code
charcoal up --ide https://github.com/octocat/hello-world.git

# See all your running workspaces
charcoal list

# Stop a workspace
charcoal stop hello-world
```

## How does it work?

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

## How-to

- [Install](./how-to/install/) — Install Charcoal on your system
- [Launch a Web IDE](./how-to/launch-web-ide/) — Clone a repo and open it in browser VS Code
- [List Workspaces](./how-to/list-workspaces/) — See all provisioned environments
- [Stop a Workspace](./how-to/stop-workspace/) — Gracefully shut down a dev container
- [Update & Uninstall](./how-to/update/) — Keep Charcoal up to date or remove it
- [Contribute](./how-to/contribute/) — Set up a development environment and submit changes

## Concepts

- [Dev Containers](./concepts/dev-containers/) — How Charcoal uses the Dev Container Spec
- [Workspaces](./concepts/workspaces/) — How environments are managed on disk and in Docker
- [Architecture](./concepts/architecture/) — Internal design and component interaction

## Links

- [GitHub →](https://github.com/charcoal-io/charcoal) — Source code, issues, and pull requests
- [Telegram →](https://t.me/charcoal) — Community chat and announcements
- [X →](https://x.com/charcoal) — News and updates
- [Discord →](https://discord.gg/charcoal) — Community support and discussion

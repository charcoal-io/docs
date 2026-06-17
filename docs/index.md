# What is Charcoal IDE?

A lightweight orchestrator for local and remote development environments. Built with [Dev Container](https://containers.dev/). It bridges the gap between local Docker-based workflows and cloud-scale development environments.

The platform is composed of three components:

---

## charcoal-cli

The command-line tool for provisioning and managing dev containers. Clone a repo, launch a browser-based VS Code, and stop environments — all from your terminal.

```bash
charcoal up --ide https://github.com/octocat/hello-world.git
```

[Get started with the CLI →](./cli/getting-started.md)

---

1. Clones the repository into `~/.charcoal-ws/`
2. Detects or generates a `devcontainer.json`
3. Builds and starts the container with `devcontainer up`
4. Launches either an interactive shell or a web-based VS Code (OpenVSCode Server)

---

## Charcoal Platform

A web-based dashboard for managing development environments visually — coming soon.

[Learn more about the Platform →](./platform/)

---

## API Reference

Programmatic access to charcoal's orchestration layer for CI/CD and custom tooling — coming soon.

[Learn more about the API →](./api/)

---

## Which component should I use?

| You want to... | Use |
|----------------|-----|
| Provision environments from the terminal | [CLI](./cli/) |
| Manage workspaces with a graphical dashboard | [Platform](./platform/) *(coming soon)* |
| Integrate with CI/CD or bPlatformld custom tooling | [API](./api/) *(coming soon)* |

## Links

- [GitHub →](https://github.com/charcoal-io/compose) — Source code, issues, and pull requests
- [Telegram →](https://t.me/charcoal_io) — Community chat and announcements
- [X →](https://x.com/charcoal_io) — News and updates
- [Discord →](https://discord.gg/charcoal_io) — Community support and discussion

# Getting Started

Get charcoal-cli up and running in minutes.

## Prerequisites

- **Docker** Engine 20.10+
- **Dev Container CLI** — Install via npm:
  ```bash
  npm install -g @devcontainers/cli
  ```
- **Python** 3.9 or higher

## Install

```bash
# Run the install script
./install.sh

# Ensure ~/.local/bin is in your PATH
export PATH="$HOME/.local/bin:$PATH"
```

See the [Install guide](../how-to/install.md) for detailed instructions, including local (no-install) usage.

## Authenticate (Optional for Accessing Compute and Workflows )

While local workspaces work without authentication, cloud features (VM management, compute, billing) require logging in:

```bash
# Login with username/password + OTP
charcoal auth login

# Or use Google OAuth
charcoal auth login --method google

# Check your status
charcoal auth status
```

See the [Auth Commands](./commands.md#charcoal-auth-login) reference for details.

## Launch Your First Workspace

```bash
charcoal up --ide https://github.com/octocat/hello-world.git
```

This clones the repo, builds a dev container, and opens VS Code in your browser at `http://localhost:3000`. Press `Ctrl+C` to stop.

## Next Steps

- Learn how to [list and manage workspaces](../how-to/list-workspaces.md)
- Explore the [full command reference](./commands.md)
- Customize your setup with [configuration options](./configuration.md)
- Understand [dev containers](../concepts/dev-containers.md) and [workspace concepts](../concepts/workspaces.md)

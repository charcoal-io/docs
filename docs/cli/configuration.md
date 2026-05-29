---
icon: lucide/settings
---

# Configuration

charcoal CLI works out of the box with sensible defaults. The following environment variables let you customize its behavior.

## Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `CODESPACES_DIR` | `~/.local-codespaces/` | Directory where repositories are cloned and workspaces are stored |

## Workspace Storage

All workspaces are stored under the codespaces directory. Each cloned repository gets its own subdirectory named after the repo:

```
~/.local-codespaces/
├── hello-world/
├── my-project/
└── another-repo/
```

To change the storage location, set `CODESPACES_DIR` before running any `charcoal` command:

```bash
export CODESPACES_DIR="/mnt/ssd/workspaces"
charcoal up --ide https://github.com/octocat/hello-world.git
```

## Dev Container Configuration

Charcoal respects any existing `.devcontainer/devcontainer.json` or `.devcontainer.json` in the cloned repository. When no configuration is found, it generates a sensible fallback automatically.

See [Dev Containers](../concepts/dev-containers.md) for details on how configurations are detected and generated.

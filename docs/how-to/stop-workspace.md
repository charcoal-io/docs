---
icon: lucide/square-stop
---

# Stop a Workspace

Gracefully shut down a development environment.

## Usage

```bash
charcoal stop <workspace-name>
```

The workspace name matches the repository name as shown in `charcoal list`.

Example:

```bash
charcoal stop hello-world
# Stopped hello-world
```

Charcoal finds the container by its `devcontainer.local_folder` Docker label and removes it.

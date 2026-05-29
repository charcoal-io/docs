---
icon: lucide/folder
---

# Workspaces

A workspace is a cloned git repository paired with a running (or stopped) dev container.

## Storage

All workspaces live under `~/.local-codespaces/`. Each directory is named after the repository:

```
~/.local-codespaces/
├── hello-world/         # Cloned from github.com/octocat/hello-world
├── my-project/          # Cloned from github.com/user/my-project
└── another-repo/        # Cloned from github.com/user/another-repo
```

## Lifecycle

1. **Create** — `charcoal up` clones the repo if it doesn't exist, then provisions the container
2. **List** — `charcoal list` scans `~/.local-codespaces/` and queries Docker for container status
3. **Stop** — `charcoal stop` finds the container by Docker label and removes it
4. **Persist** — Repo data stays on disk after a container is stopped; you can re-provision with `charcoal up` again

## Container Labeling

Charcoal uses the `devcontainer.local_folder` Docker label to associate containers with workspace directories. This is the standard label applied by the Dev Container CLI and allows Charcoal to find and manage containers without tracking state externally.

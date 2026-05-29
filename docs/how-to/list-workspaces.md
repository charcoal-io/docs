---
icon: lucide/list
---

# List Workspaces

Track all provisioned workspaces and their current Docker status.

## Usage

```bash
charcoal list
```

Output shows a table of workspaces:

```
NAME               STATUS          PATH
hello-world        Up 2 hours      /home/user/.local-codespaces/hello-world
my-project         Exited (0)      /home/user/.local-codespaces/my-project
```

Each workspace corresponds to a cloned repository under `~/.local-codespaces/`. Status is read from Docker container labels.

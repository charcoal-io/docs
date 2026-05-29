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
hello-world        Up 2 hours      /home/user/.charcoal-ws/hello-world
my-project         Exited (0)      /home/user/.charcoal-ws/my-project
```

Each workspace corresponds to a cloned repository under `~/.charcoal-ws/`. Status is read from Docker container labels.

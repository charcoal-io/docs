---
icon: lucide/rotate-ccw
---

# Update & Uninstall

## Update

If Charcoal was installed from a git repository, run the update script:

```bash
./update.sh
```

This runs `git pull` and prints the new version.

## Uninstall

Remove the `charcoal` command from your system:

```bash
./uninstall.sh
```

This deletes the wrapper script at `~/.local/bin/charcoal`. Workspaces under `~/.local-codespaces/` are not removed.

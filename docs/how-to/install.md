---
icon: lucide/download
---

# Install

## Prerequisites

- **Docker** Engine 20.10+
- **Dev Container CLI** — `@devcontainers/cli` installed via npm:
  ```bash
  npm install -g @devcontainers/cli
  ```
- **Python** 3.9 or higher

## Standard Installation (Command Line)

Run the install script to make the `charcoal` command available from anywhere:

```bash
./install.sh
```

This creates a wrapper script at `~/.local/bin/charcoal`. Ensure `~/.local/bin` is in your `PATH`:

```bash
export PATH="$HOME/.local/bin:$PATH"
```

Add that line to your `~/.bashrc` or `~/.zshrc` to make it permanent.

## Local Usage (No Install)

Alternatively, run Charcoal directly with Python:

```bash
python charcoal.py up --ide https://github.com/octocat/hello-world.git
```

## Verify Installation

```bash
charcoal --version
# Charcoal 0.1.0
```

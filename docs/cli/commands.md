---
icon: lucide/terminal
---

# Commands Reference

## `charcoal up`

Provision and start a development environment.

```bash
charcoal up [options] <repository>
```

The repository URL can be an HTTPS or SSH git URL. If the first argument starts with `http` or `git@`, the `up` command is automatically inferred.

| Option | Default | Description |
|--------|---------|-------------|
| `--ide` | — | Launch a web-based VS Code (OpenVSCode Server) |
| `--port` | `3000` | Host port for the Web IDE (requires `--ide`) |
| `--branch` | — | Git branch to clone |

**Examples:**

```bash
# Clone and open a shell
charcoal up https://github.com/octocat/hello-world.git

# Clone and open VS Code in the browser
charcoal up --ide https://github.com/octocat/hello-world.git

# Custom port and branch
charcoal up --ide --port 8080 --branch main https://github.com/user/repo.git

# Auto-inferred up command
charcoal https://github.com/octocat/hello-world.git
```

---

## `charcoal list`

List all provisioned workspaces and their Docker status.

```bash
charcoal list
```

Output:

```
NAME               STATUS          PATH
hello-world        Up 2 hours      /home/user/.local-codespaces/hello-world
my-project         Exited (0)      /home/user/.local-codespaces/my-project
```

---

## `charcoal stop`

Gracefully shut down a running workspace.

```bash
charcoal stop <workspace-name>
```

The workspace name matches the repository directory name as shown in `charcoal list`.

**Example:**

```bash
charcoal stop hello-world
# Stopped hello-world
```

---

## `charcoal --version`

Print the installed version.

```bash
charcoal --version
# Charcoal 0.1.0
```

---

## `charcoal --help`

Display usage information and available commands.

```bash
charcoal --help
```

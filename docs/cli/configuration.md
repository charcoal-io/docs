---
icon: lucide/settings
---

# Configuration

Charcoal stores its configuration in `~/.charcoal/config.json` with built-in defaults that ship with the CLI. A separate `~/.charcoal/defaults.json` file lets you customize base defaults for re-initialization.

The lookup order is: **config.json → defaults.json → built-in defaults**.

## Config Command

```bash
charcoal config <command> [key] [value]
```

| Command            | Description                                               |
|--------------------|-----------------------------------------------------------|
| `get <key>`        | Print the value of a config key                           |
| `set <key> <value>` | Set a config key to a value                              |
| `unset <key>`      | Remove a custom value (falls back to defaults)            |
| `list`             | Show all configuration keys and values                    |
| `show`             | Detailed view with types and descriptions                 |
| `init`             | Re-initialize config from `defaults.json`                 |
| `edit`             | Open `config.json` in `$EDITOR` (or `nano`)              |
| `reset-defaults`   | Reset `defaults.json` to built-in defaults                |

**Examples:**

```bash
# View the current IDE image
charcoal config get ide.image

# Change the IDE image
charcoal config set ide.image my-ide:latest

# Change the default IDE port
charcoal config set ide.port 8080

# Change the workspace storage directory
charcoal config set workspace.dir /mnt/ssd/workspaces

# List all settings
charcoal config list

# Detailed view with types and descriptions
charcoal config show

# Open config in your editor
charcoal config edit

# Re-initialize from your customized defaults
charcoal config init

# Reset defaults to built-in values
charcoal config reset-defaults

# Reset a setting to its fallback
charcoal config unset ide.port
```

## Configuration Keys

| Key             | Type    | Default                                  | Description                                     |
|-----------------|---------|------------------------------------------|-------------------------------------------------|
| `workspace.dir` | string  | `~/.charcoal-ws`                         | Directory where workspaces are stored           |
| `ide.image`     | string  | `bilw/openvscode-server:latest`          | Docker image for the web IDE container          |
| `ide.port`      | integer | `3000`                                   | Host port for the web IDE                       |

## Custom Keys

You can store arbitrary custom keys for future features. They persist in `config.json` and/or `defaults.json`:

```bash
# SSH key for remote container access (future)
charcoal config set ssh.key ~/.ssh/id_rsa

# Cloud provider configuration (future)
charcoal config set cloud.provider aws
charcoal config set cloud.region us-east-1

# Workflow configuration (future)
charcoal config set workflow.dir ~/charcoal-workflows
```

Custom keys are listed by `charcoal config list` and `charcoal config show`.

## Defaults File

The `~/.charcoal/defaults.json` file stores a base layer of defaults that you can customize and use to re-initialize your config:

```bash
# Edit your defaults
charcoal config edit  # opens config.json

# Or create/edit defaults.json directly
nano ~/.charcoal/defaults.json
```

Defaults file format (nested JSON):

```json
{
  "ide": {
    "image": "bilw/openvscode-server:latest",
    "port": 3000
  },
  "workspace": {
    "dir": "/home/user/.charcoal-ws"
  }
}
```

To restore built-in defaults:
```bash
charcoal config reset-defaults
```

To re-initialize your config from the defaults file:
```bash
charcoal config init
```

## How Configs Affect Behavior

| Config               | Affects                                                              |
|----------------------|----------------------------------------------------------------------|
| `workspace.dir`      | Where `charcoal up` clones repositories and stores workspace data    |
| `ide.image`          | The container image used when `--ide` is passed to `charcoal up`     |
| `ide.port`           | The default port used when no `--port` is specified                  |

## Environment Variables

| Variable         | Default            | Description                                      |
|------------------|--------------------|--------------------------------------------------|
| `CODESPACES_DIR` | `~/.charcoal-ws`   | (Legacy) Alternative to `workspace.dir`          |

## File Locations

| File                              | Purpose                          |
|-----------------------------------|----------------------------------|
| `~/.charcoal/config.json`        | User configuration overrides     |
| `~/.charcoal/defaults.json`      | User-customizable base defaults  |

---
icon: lucide/workflow
---

# Architecture

Charcoal is a four-layer Python CLI built on top of Docker and the Dev Container CLI.

## Component Diagram

```
┌─────────────────────────────────────────────────┐
│                   CLI (cli.py)                   │
│  Argument parsing, command dispatch, error       │
│  handling                                        │
├─────────────────────────────────────────────────┤
│              Orchestrator (manager.py)            │
│  Ties workspace, config, and container together  │
├───────────────────┬─────────────────────────────┤
│  Workspace         │  DevContainerConfig         │
│  (workspace.py)    │  (config.py)                │
│  - Git clone/      │  - Read/write               │
│    existence check │    devcontainer.json         │
│  - Repo name       │  - Fallback generation      │
│    extraction      │  - Port forwarding          │
├───────────────────┴─────────────────────────────┤
│            ContainerManager (container.py)        │
│  - devcontainer up / exec / stop                 │
│  - Docker label queries                          │
└─────────────────────────────────────────────────┘
                    │
                    ▼
┌─────────────────────────────────────────────────┐
│          Docker Engine + Dev Container CLI       │
│  (External dependencies)                         │
└─────────────────────────────────────────────────┘
```

## Layer Responsibilities

- **CLI** (`cli.py`) — Parses arguments, dispatches to the `Orchestrator`, formats output
- **Orchestrator** (`manager.py`) — Coordinates setup (clone + config) and runtime (container launch + shell/IDE)
- **Workspace** (`workspace.py`) — Manages git clone, path resolution, and devcontainer.json discovery
- **DevContainerConfig** (`config.py`) — Reads, writes, and creates fallback `devcontainer.json` files
- **ContainerManager** (`container.py`) — Wraps `devcontainer` CLI commands and Docker queries

## Data Flow: `charcoal up --ide <repo>`

```
1. CLI parses args → Orchestrator(repo, use_ide=True)
2. Orchestrator.setup()
   ├─ Workspace: check if repo exists; clone if not
   ├─ Workspace: find devcontainer.json
   └─ Config: create fallback or update existing config
3. Orchestrator.run()
   ├─ ContainerManager.up() → devcontainer up
   └─ launch_ide() → print URL, keep-alive loop
```

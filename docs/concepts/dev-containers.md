---
icon: lucide/container
---

# Dev Containers

Charcoal is built on the [Dev Container Spec](https://containers.dev/), an open standard for configuring reproducible development environments. A dev container is a Docker container configured via a `devcontainer.json` file.

## How Charcoal Uses Dev Containers

When you run `charcoal up`, Charcoal:

1. Looks for an existing `.devcontainer/devcontainer.json` or `.devcontainer.json` in the cloned repo
2. If none exists, generates a fallback config — either a generic Ubuntu base image or the `linuxserver/openvscode-server` image when `--ide` is used
3. Hands off to the `devcontainer` CLI which builds, starts, and attaches to the container

## Fallback Configuration

When no `devcontainer.json` exists, Charcoal creates one automatically:

**Shell mode (default):**
```json
{
  "image": "mcr.microsoft.com/devcontainers/base:ubuntu"
}
```

**Web IDE mode (`--ide`):**
```json
{
  "image": "linuxserver/openvscode-server:latest",
  "appPort": [3000],
  "overrideCommand": false,
  "workspaceFolder": "/config/workspace",
  "workspaceMount": "source=<repo-path>,target=/config/workspace,type=bind"
}
```

## Existing Configurations

If the repo already has a `devcontainer.json`, Charcoal respects it and only ensures the required ports are forwarded when `--ide` is used.

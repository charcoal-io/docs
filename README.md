# Charcoal Documentation Site

Documentation site for the Charcoal IDE platform, powered by [Zensical](https://zensical.dev) static site generator.

## Prerequisites

- Python 3.9+
- Zensical (`pip install zensical`)

## Quick Start

```bash
cd docs

# Install Zensical
pip install zensical

# Build the site
zensical build

# Serve locally
zensical serve
```

The site will be available at `http://localhost:8000` (or the port Zensical assigns).

## Directory Structure

```
docs/
├── docs/              # Markdown content files
│   ├── cli/           # CLI documentation
│   ├── concepts/      # Architecture and concepts
│   ├── how-to/        # How-to guides
│   ├── platform/      # Platform docs (coming soon)
│   └── api/           # API docs (coming soon)
├── site/              # Generated static site
├── zensical.toml      # Zensical configuration
└── zensical.lock      # Dependency lock file
```

## Adding Content

1. Create a Markdown file in the appropriate `docs/` subdirectory
2. Update navigation in `zensical.toml` if needed
3. Run `zensical build` to regenerate the site

## Configuration

The site is configured via `zensical.toml`:

- **Theme**: Material-inspired with Inter and Jetbrains Mono fonts
- **Color scheme**: Light/dark mode support
- **Site name**: "Charcoal IDE"

## Development

```bash
# Build and serve with live reload
zensical serve

# Build for production
zensical build
```

The output goes to `site/` directory.

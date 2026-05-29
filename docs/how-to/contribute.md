---
icon: lucide/git-pull-request
---

# Contribute

## Reporting Bugs

- Check the documentation to see if it's a known issue
- Search existing issues before opening a new one
- Include your OS, Docker version, and reproduction steps

## Suggesting Enhancements

Open an issue with the `enhancement` tag. Describe the behavior you want and why it's useful.

## Pull Requests

1. Fork the repo and create your branch from `main`
2. Add tests for new features or bug fixes
3. Ensure all tests pass and coverage stays high
4. Run lint and type-check tools
5. Write clear, descriptive commit messages
6. Open the PR

## Development Commands

```bash
# Run tests with coverage
python3 -m pytest --cov=charcoal_cli tests/

# Lint check
ruff check .

# Type check
mypy .
```

We follow **PEP 8** and aim for **100% test coverage** on new code.

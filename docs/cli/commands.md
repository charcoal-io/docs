---
icon: lucide/terminal
---

# Commands Reference

## `charcoal auth login`

Authenticate with the Charcoal API.

```bash
charcoal auth login [options]
```

Two authentication methods are supported:

| Option | Default | Description |
|--------|---------|-------------|
| `--method, -m` | `password` | Authentication method: `password` or `google` |
| `--username` | — | Username for password login (prompted if omitted) |
| `--password` | — | Password for password login (prompted securely if omitted) |

### Password + OTP flow (default)

1. Enter your username and password
2. The server validates credentials and sends a 6-digit OTP code to your email
3. Enter the OTP code to complete authentication

```bash
charcoal auth login
#   Username: alice
#   Password: [hidden]
#   ✓ Password verified. OTP sent to a****@example.com
#   Enter OTP code: 123456
#   ✓ Logged in as alice <alice@example.com>
```

### Google OAuth flow

Opens a browser window for Google authentication:

```bash
charcoal auth login --method google
#   ✓ Starting Google OAuth flow...
#   ✓ Opening browser for Google authentication...
#   ✓ Logged in as alice <alice@gmail.com>
```

---

## `charcoal auth register`

Create a new Charcoal account.

```bash
charcoal auth register --username <name> --email <email> [--password <password>]
```

| Option | Required | Description |
|--------|----------|-------------|
| `--username` | Yes | Desired username |
| `--email` | Yes | Email address |
| `--password` | No | Password (prompted securely if omitted) |

**Example:**

```bash
charcoal auth register --username alice --email alice@example.com
#   Password: [hidden]
#   ✓ Account created for alice
#   Run: charcoal auth login
```

---

## `charcoal auth status`

Show the current authentication status.

```bash
charcoal auth status
```

Displays the authenticated user and session expiry information. If the session has expired, it automatically attempts a token refresh.

---

## `charcoal auth logout`

Log out and clear stored credentials.

```bash
charcoal auth logout
#   ✓ Session invalidated on server
#   ✓ Logged out. Local session cleared.
```

---

## `charcoal auth token`

Print the current access token (useful for scripting or API access).

```bash
charcoal auth token [--refresh]
```

| Option | Description |
|--------|-------------|
| `--refresh` | Print the refresh token instead of the access token |

**Example:**

```bash
# Get the access token for API calls
export CHARCOAL_TOKEN=$(charcoal auth token)

# Use it with curl
curl -H "Authorization: Bearer $CHARCOAL_TOKEN" https://api.charcoal.dev/api/v1/auth/me
```

---

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

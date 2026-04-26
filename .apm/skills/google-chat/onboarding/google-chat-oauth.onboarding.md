---
id: google-chat-oauth
name: Set up Google Chat OAuth
type: interactive
completed-when:
  - file-exists: ~/.config/google-chat-mcp/token.json
---

# Set up Google Chat OAuth

The Google Chat MCP server needs an OAuth token to access your workspace.
This is a one-time interactive setup.

## 1. Get the OAuth client credentials

The team's Google Cloud project has an OAuth client configured for the
Google Chat MCP. **Credentials live in 1Password** (or ask a teammate)
under "WS.Eng — Google Chat MCP OAuth client". You'll need:

- `GOOGLE_CHAT_CLIENT_ID`
- `GOOGLE_CHAT_CLIENT_SECRET`

These used to be hard-coded in `apm.yml`, but committing OAuth client
secrets to git triggered GitHub's secret scanner — they're now read
from environment variables and only the rotated values live in 1Password.

## 2. Set them as persistent environment variables

### Windows (PowerShell)

```powershell
[System.Environment]::SetEnvironmentVariable("GOOGLE_CHAT_CLIENT_ID", "...", "User")
[System.Environment]::SetEnvironmentVariable("GOOGLE_CHAT_CLIENT_SECRET", "...", "User")
```

Open a new shell so the new variables are picked up.

### macOS / Linux

Add to `~/.zshrc` or `~/.bashrc`:

```bash
export GOOGLE_CHAT_CLIENT_ID="..."
export GOOGLE_CHAT_CLIENT_SECRET="..."
```

Then `source ~/.zshrc` (or open a new shell).

## 3. Run the OAuth flow

```bash
ws bootstrap
```

This reads the env vars, expands them into the `setupCommand`, opens a
browser for Google consent, and writes the token to
`~/.config/google-chat-mcp/token.json`.

If `google-chat-mcp` is not installed yet:

```bash
pipx install git+https://github.com/ROKT/google-chat-mcp-yash.git
```

## Verification

```bash
ws status
```

The Google Chat OAuth entry should show `OK` and the token file should
exist at `~/.config/google-chat-mcp/token.json`.

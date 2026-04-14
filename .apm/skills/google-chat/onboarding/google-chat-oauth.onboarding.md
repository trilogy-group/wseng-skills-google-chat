---
id: google-chat-oauth
name: Set up Google Chat OAuth
type: interactive
completed-when:
  - file-exists: ~/.config/google-chat-mcp/token.json
---

# Set up Google Chat OAuth

The Google Chat MCP server needs an OAuth token to access the user's
workspace. This is a one-time interactive setup.

## Steps

1. The OAuth client credentials are configured in `apm.yml` under
   `env.mcpServers.google-chat.oauth`. The `ws bootstrap` command
   handles this automatically.

2. If running manually, use `ws setup` which reads the credentials
   from the config and runs the OAuth flow.

3. A browser window will open for Google OAuth consent.
   Grant access to Google Chat.

4. The token is saved to `~/.config/google-chat-mcp/token.json`

If `google-chat-mcp` is not installed:

```bash
pipx install git+https://github.com/ROKT/google-chat-mcp-yash.git
```

## Verification

Check that the token file exists:

```bash
ws status
```

The Google Chat OAuth entry should show `OK`.

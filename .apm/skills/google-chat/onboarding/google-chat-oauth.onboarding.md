---
id: google-chat-oauth
name: Set up Google Chat OAuth
type: interactive
completed-when:
  - file-exists: ~/.config/google-chat-mcp/token.json
---

# Set up Google Chat OAuth

The Google Chat MCP server needs an OAuth token to access your
workspace. The OAuth client (id + secret) is shared by the team and
lives in `wseng-skills/team-secrets` — `ws install` pulls it
automatically. You only need to do the per-user browser consent step
once.

## 1. Run `ws install`

```bash
saml2aws login --profile trilogy   # if your session has expired
ws install
```

`ws install` will:

1. Resolve `team:googleChatClientId` and
   `team:googleChatClientSecret` from AWS Secrets Manager.
2. Detect that no OAuth token exists at
   `~/.config/google-chat-mcp/token.json`.
3. Run the `google-chat-mcp setup` command, which opens your browser
   for Google consent and writes the resulting token to the path
   above.

If `google-chat-mcp` is not installed yet, install it first:

```bash
pipx install git+https://github.com/ROKT/google-chat-mcp-yash.git
```

## 2. Verify

```bash
ws status
```

The Google Chat OAuth entry should show `OK` and the token file
should exist at `~/.config/google-chat-mcp/token.json`.

## Troubleshooting

- **`OAuth setup blocked — empty value(s) for: clientId, clientSecret`** —
  Your AWS session expired before secrets could be fetched. Run
  `saml2aws login --profile trilogy` and try again.
- **`invalid_client` after browser consent** — The shared OAuth
  client may have been rotated. Ask the on-call to refresh it in
  `wseng-skills/team-secrets`, then re-run `ws install`.

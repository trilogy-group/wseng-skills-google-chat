# Google Chat MCP — Messaging Guide

## Available tools

The `user-google-chat` MCP exposes these tools:

| Tool | Purpose |
|------|---------|
| `gchat_list_spaces` | List all spaces the user belongs to |
| `gchat_get_space_members` | List members of a space |
| `gchat_search_messages` | Search message history |
| `gchat_send_message` | Send a message to a space |
| `gchat_get_messages` | Read recent messages in a space |

## @-Mention syntax

To tag someone in a `gchat_send_message` call, use their `@trilogy.com`
email wrapped in angle-bracket user syntax:

```
<users/firstname.lastname@trilogy.com>
```

The API resolves this to a real @-mention with notification. Plain-text
`@Name` does **not** trigger a notification.

### Examples

- **Mention one person:** `Hey <users/lokesh.singhania@trilogy.com>, can you review this?`
- **Mention everyone:** `<users/all>` (pings the whole space)
- **Mention multiple:** chain them: `<users/serban.petrescu@trilogy.com> <users/timotei.dolean@trilogy.com>`

### Gotchas

- The API **validates** the email. An invalid email causes a 400 error (DLP
  violation), not a silent failure.
- `<users/all>` is a special keyword — it works without an email.
- Never include raw `<users/...>` syntax in explanatory text within a message
  body. The API will attempt to resolve it and fail if the email is invalid.

## Resolving people and spaces

1. Always check the compiled cheatsheet index
   (`~/.claude/instructions/cheatsheets.instructions.md`) first. If it lists
   the Google Chat cheatsheet, read that file for Space IDs and emails.
2. If a space isn't in the cheatsheet, call `gchat_list_spaces` to find it.
3. Emails follow `firstname.lastname@trilogy.com`. If you're unsure of the
   exact spelling, call `gchat_get_space_members` on a shared space to look
   them up.

## Best practices

1. **Confirm before sending** — always show the user the message text and
   target space before calling `gchat_send_message`.
2. **Use the cheatsheet** — don't call `gchat_list_spaces` every time if the
   Space ID is already known.
3. **Quote context** — when replying to a discussion, include relevant context
   so recipients don't need to scroll back.
4. **Avoid @all** — only use `<users/all>` when the user explicitly asks to
   notify everyone. Default to mentioning specific people.

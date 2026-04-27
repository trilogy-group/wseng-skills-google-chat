---
name: google-chat
description: >-
  Context and guidance for using the Google Chat MCP integration.
  Covers messaging, @-mentions, space discovery, and the team
  cheatsheet for workspace communication.
---

# Google Chat Skill

This skill gives the agent context for operating the Google Chat MCP server
(`user-google-chat`). Read the guides below before performing any messaging.

## Messaging and @-mentions

Read [messaging/guide.md](messaging/guide.md) and follow its instructions.

## Space and team cheatsheet

Use the compiled cheatsheet index at
`~/.claude/instructions/cheatsheets.instructions.md` to find the Google Chat
cheatsheet when resolving names, Space IDs, and DM mappings.

If the Google Chat cheatsheet is missing from that index, the user has not
finished the `populate-gspace-cheatsheet` onboarding task. Surface that task
before sending workspace messages that require unknown spaces or DMs.

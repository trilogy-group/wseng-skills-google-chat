---
id: populate-gspace-cheatsheet
name: Populate Google Chat cheatsheet
type: guided
completed-when:
  - file-exists: .apm/cheatsheets/google-chat.cheatsheet.md
---

# Populate Google Chat Cheatsheet

The Google Chat cheatsheet is user-owned reference data. Create it in the
user's `wseng-skills-config` repo at
`.apm/cheatsheets/google-chat.cheatsheet.md`; `ws install` will compile it into
the progressively disclosed cheatsheet index.

## Steps

1. Create `.apm/cheatsheets/google-chat.cheatsheet.md` from
   [cheatsheet-template.md](../cheatsheet-template.md).

2. Use the google-chat MCP to list the user's DM spaces:
   - Call `gchat_list_spaces` to get all spaces.
   - Identify direct message spaces (type: DM).

3. Match each DM to a person in the team directory table and fill in the
   **DM Space ID** column.

4. Ask if there are any product-specific spaces they use and add those too

5. Run `ws install` from `wseng-skills-config` so the cheatsheet compiler writes
   `~/.claude/cheatsheets/google-chat.md` and updates
   `~/.claude/instructions/cheatsheets.instructions.md`.

## When done

Commit the updated cheatsheet to the user's personal branch in
`wseng-skills-config`. The onboarding system checks for the source file to
confirm completion.

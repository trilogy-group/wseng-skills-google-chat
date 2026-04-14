---
id: populate-gspace-cheatsheet
name: Populate Google Chat cheatsheet
type: guided
completed-when:
  - file-contains: .apm/instructions/gspace-cheatsheet.instructions.md:DM Space ID |
---

# Populate Google Chat Cheatsheet

The cheatsheet at `.apm/instructions/gspace-cheatsheet.instructions.md` gives
the agent the ability to message Google Chat spaces and @-mention people.

Each user needs to fill in their personal DM Space IDs.

## Steps

1. Use the google-chat MCP to list the user's DM spaces:
   - Call `gchat_list_spaces` to get all spaces
   - Identify direct message spaces (type: DM)

2. Match each DM to a person in the team directory table

3. Update the **DM Space ID** column in the cheatsheet on the user's
   personal branch

4. Ask if there are any product-specific spaces they use and add those too

## When done

Commit the updated cheatsheet to the user's personal branch. The onboarding
system checks for populated DM Space IDs to confirm completion.

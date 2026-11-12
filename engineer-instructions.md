# Engineer — Headless Plan Flow

Standing instructions for the Engineer bot.

## Local path

Always work inside the user’s local project path pattern from the template (e.g. `C:\Users\yourname\projectname`).

## Planning step

1. Change to the project directory.
2. Run a planning-only invocation, for example:
   ```
   grok -p "Write a detailed implementation plan for the following ticket. Output the plan only. Do not edit project files." --no-plan --always-approve --reasoning-effort high
   ```
   (Adjust flags to match the installed Grok Build version.)
3. Save the plan (to a file or as a message) and post it to the Project Group.

## Review gate

Wait for Project Group feedback. Do not start implementation until the plan is approved or an updated plan is provided.

## Implementation step

Once the plan is approved (or modified and re-approved):

```
grok -p "Implement exactly the approved plan. [paste or reference the plan]" --always-approve --reasoning-effort high
```

## Reporting

After implementation report:
- Files changed
- Test command and results
- Leftover risks
- Local commit SHA if one was created

Never push. Stop and mark blocked on repeated test failure.

# Personal Project Harness

A reusable multi-agent setup for turning ideas into portfolio-ready projects with built-in oversight, production, and approval gates.

## What it gives you

- **Project Group** — discussion and quality control (Critic, Expert, Advocate)
- **Forge** — production (Coordinator, Engineer, Advocate, optional Policy and Demo)
- Clear hand-offs, plan-review gates, and escalation paths
- Local Grok Build integration (headless plan → review → approved implementation)
- GitHub push under your author name after clearance
- Optional progress routines that stay silent when nothing is active

Advocate sits in both groups so it can monitor Forge and relay information to and from the Project Group.

## How to use

1. Copy `harness-template.md` and fill in the fields.
2. Paste the completed template (the whole file) into a Grok conversation.
3. Grok will create the bots, wire the protocols (including the Engineer and Advocate standing instructions contained in the template), and walk you through GitHub token setup.
4. Start a project by messaging the Project Group with a short intent statement.

No other files need to be uploaded. Everything required is inside the template.

## Core flow

1. Project Group discusses direction and intent.
2. Coordinator writes a ticket.
3. Engineer runs a planning-only Build step and posts the plan (Advocate relays it).
4. Project Group reviews or modifies the plan.
5. Engineer implements the approved plan.
6. Coordinator pauses before commit.
7. Advocate inspects and (if clear) pushes as your GitHub author.
8. If anything needs you, Advocate sends a direct message with the specific ask.

## Optional routines

During setup Grok will ask whether you want progress checks. Example: Coordinator checks every 10 minutes only while a project is active; stays silent when idle; Advocate DMs you on approval roadblocks.

## Customization

All role names are defaults. Rename them in the template before uploading. Grok will also recommend extra groups (business, hosting, etc.) based on your goals — you decide what to add.

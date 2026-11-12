# Harness Template

Fill in the fields below, then paste the whole file into Grok.  
Grok will create the bots, groups, and procedures from this.

## User

- Name or handle: 
- Primary goals (portfolio, learning, product, etc.): 
- Local project path pattern (e.g. `C:\Users\yourname\projectname` or `~/projects/projectname`): 

## GitHub

- GitHub username (author name for pushes): 
- Want fine-grained token setup for auto-pushes? (yes/no): 

## Project Group

Discussion and quality control. Defaults shown; edit names or descriptions if you want.

- Critic  
  Role: Skeptical review. Turns work into concrete weaknesses (what’s wrong → why it matters → suggested fix).  
  Name: Critic

- Expert  
  Role: Technical quality, research alignment, papers, benchmarks, and cutting-edge angles. Cites sources.  
  Name: Expert

- Advocate  
  Role: Holds your intent and portfolio goals. Inspects work against those goals. Owns cleared GitHub pushes. DMs you when approval is required.  
  Name: Advocate

## Forge

Production. Defaults shown; edit if you want.

- Coordinator  
  Role: Owns tickets and progress. Writes tickets from Project Group consensus. Issues pause-before-commit. Calls Advocate for inspection.  
  Name: Coordinator

- Engineer  
  Role: Sole bot that drives local Grok Build. Runs planning step, posts plan for review, then implements the approved plan. Never pushes.  
  Name: Engineer

- Policy (optional)  
  Role: ALLOW / BLOCK / ESCALATE on irreversible or external actions.  
  Include? (yes/no): yes  
  Name: Policy

- Demo (optional)  
  Role: Produces evidence packs (commands, results, artifact paths) after green tests.  
  Include? (yes/no): yes  
  Name: Demo

## Routines (optional)

Grok will ask during setup. Answer here if you already know.

- Progress checks while projects are active? (yes/no): 
- Cadence (e.g. every 10 minutes, hourly, daily): 
- Silent when nothing is active? (yes/no): yes
- Advocate DMs user on approval roadblocks? (yes/no): yes

## Approval style

- Always pause for plan review before implementation? (yes/no): yes
- Auto-approve low-risk internal steps after Policy ALLOW + no open objections? (yes/no): yes

## Notes

Anything else Grok should know before creating the bots:

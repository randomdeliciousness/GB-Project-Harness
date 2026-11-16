# Sir Sparks-a-lot: Project Breakdown

This is a case study of the harness run on a private game project, Nov 15–16 2026. Times are in CT (America/Chicago).

From Saturday, Nov 15 through late Monday morning, Nov 16, 2026. What the Forge produced, built, and pushed without a fresh yes from you, and the pauses that did need you.

> **How to read this, and where it comes from**
>
> After you ruled that Demo Project Review consensus approves plans, a ticket, build, or push listed as “without you” still went through Review, Policy, Demo, and Advocate. It did not wait for a new decision from you. Times are in CT. A few QUEUE entries are labeled ET; those were converted by subtracting one hour. Two push times also differ by about eight minutes between the ticket table and the log; both are shown. SHAs and parents come from the local git history and Advocate’s notes. Push times come from QUEUE.md and Advocate’s notes. The T15 push that left GitHub main at `c7442ca` was verified with `ls-remote`, and the repository was confirmed still private. Where it is unclear whether you were involved, this page says so instead of guessing.

## Table of contents

- [Summary counts](#summary-counts)
- [Tickets produced without you](#tickets-produced-without-you)
- [Problems identified and fixed without you](#problems-identified-and-fixed-without-you)
- [Build sessions run without you](#build-sessions-run-without-you)
- [GitHub pushes without you](#github-pushes-without-you)
- [Directional decisions made without you](#directional-decisions-made-without-you)
- [Hard pauses that needed you](#hard-pauses-that-needed-you)
- [Current state and parked queue](#current-state-and-parked-queue)

## Summary counts

*As of Monday, Nov 16, 2026, about 10:56 AM CT, after T15 landed.*

| Count | What | Notes |
| ---: | --- | --- |
| 12 | Pushes to GitHub | All fast-forward, no force-push, repo stayed private |
| 12 | Completed build sessions | T15 was the last; production is now closed |
| 10 | Tickets the team opened | No request from you; T16 was folded into T15 |
| 20 | Pauses that needed you | Plus 3 design questions still open |

The original T01–T11 slice was in the plan you signed off on Nov 15, so those tickets are not counted as produced without you. Fourteen problems the team caught are already on main, including the T15 input-lock work. Four more are ticketed and parked in T08i: three card-art items, plus a non-blocking smeared-number finding from T15 card rules text. Those wait until you reopen production.

The missing card descriptions on `e05c22f` are not in the “without you” count. You found that in playtest. The team diagnosed it (body text was under the background), folded the fix into T15, and it landed in `c7442ca`.

## Tickets produced without you

*Opened by Coordinator from Review consensus after your Nov 15 approval rule. You did not ask for these tickets.*

| ID | Opened | What it is | Status as of ~10:56 AM CT |
| --- | --- | --- | --- |
| T13 | Nov 15, ~6:42 PM CT | Audio plan: original or CC0 only. Art plan, Engineer integrates later. | Unbuilt, later |
| T14 | Nov 15, ~6:52 PM CT | Charge applies to the whole next lightning card, not one hit. T02 follow-up. | Parked |
| T15 | Nov 15, ~6:52 PM CT | Input lock while an action plays. Later absorbed T16 and, after your playtest, the missing body-text fix. | Pushed c7442ca |
| T16 | Nov 15, ~6:53 PM CT | Test that combat rejects an enemy-target card aimed at Pikachu. Folded into T15. | Folded into T15 |
| T17 | Nov 15, ~8:47 PM CT | Integrate accepted T09 map and shop art, plus the single Shiny Stone currency change. | Pushed 1757fa1 |
| T18 | Nov 15, ~8:55 PM CT | Rest-site UI art, split out of T10. Heal 30% or a locked upgrade. | Parked (art accepted) |
| T19 | Nov 15, ~9:28 PM CT | Harder encounter and bot scoring that values damage avoided. Opened after the T03 hold. | Parked by you |
| T22 | Nov 15, ~10:02 PM CT | Title, win, and Caught screens so the act-1 loop can return to title. | Parked (art accepted) |
| T23 | Nov 15, ~10:02 PM CT | Build SHA and run seed on screen, plus a hotkey that logs node, turn, and seed. | Pushed ef76f59 |
| T24 | Nov 15, ~10:02 PM CT | Multi-seed full-run smoke. Required after every later ticket. | Pushed 5d7b82c |
| T24b | Nov 15, ~11:23 PM CT | 200-seed floor, sharded full run, and a work guard instead of a wall-time fail. | Pushed dd46fa1 |

T20 (XP and level-up) and T21 (minimal act 2) are not in that list. They were written after you clarified T10: stat picks come from XP, boss drops are relics and stones, and a minimal act 2 should exist before those drops matter. The team wrote the tickets; the need came from you.

T12 (play-again after victory) and T08i (wire the accepted card art) also came from your playtests, so they are not counted as produced without you. T08j, the eight pending cards, was a team follow-up to T08i, but its content still waits on you.

## Problems identified and fixed without you

*Caught by Review, Engineer, Demo, Advocate, or Pikachu Art. You did not have to find these.*

Already on GitHub main:

| Issue | Why it mattered | What the team did | Landed in |
| --- | --- | --- | --- |
| T12 plate input race and a bad Vite define | Restart and New Run could miss clicks; the hotfix also restored a working dev-server smoke. | New commit on b83285f, then pushed as 75414b8. | 75414b8 |
| T09 first SHA broke the map-to-fight loop | Continue had no route back to the map, so a run could not go fight to map to fight. | Held 58ab12e and 70af78d. Fixed Continue, greyed the rest upgrade, limited buffs to STR/INT/CON, keyed seeds by node, and required path variety. | a33214b |
| T03 baseline was a 1.95 MB raw file, plus preview-drift and a broken --out | The raw run would have entered git history. Review also wanted a real-state copy or a 50-seed replay, and a reliable output path. | Held f22d132, withdrew dc71707, squashed onto a33214b so the blob never landed, and kept a summary-only baseline. | dc6038a |
| T17 coin was drawn at the wrong size; shelf could have sold a stone too early | The coin frame is 28×28, not 32. The evolution-stone shelf had to stay “Coming soon” until T10. | Held 893dd7f. Fixup commit, then pushed both. | 1757fa1 |
| T23 Demo pack could not show a live 3-enemy or scrolled-map shot | No 3-enemy encounter exists yet, and map camera scroll was not in that ticket, so live shots were the wrong acceptance bar. | Review accepted tests instead (enemy layout overlap, scrollFactor 0). Live shots moved to later tickets. | ef76f59 |
| T24b wall-time fail was the wrong gate | A slow machine could fail a healthy run. The important limit is work done, not clock time. | Replaced the hard wall-time fail with a steps/turns guard (15,000 steps, 4,000 turns). 90s is a warning. Sharded 25.3s vs 104.2s single-worker on the same machine (4.06×). | dd46fa1 |
| Perf gate assumed a 16.7 ms frame | That is only right on a 60 Hz display, and it had to run on StronkBoi’s real GPU, not a software renderer. | Refresh-relative rule: a frame over 1.5× the refresh interval is dropped; fail if more than 5% drop during Thunder; log Hz and renderer; fail on software. Demo: 0 of 73 dropped on ANGLE D3D11 Intel. | e05c22f |
| Atlases had to match accepted art byte-for-byte | A rebuild or a wrong file would ship unapproved art. | T06+T07 push required sha256 matches against Pikachu Art finals. | e05c22f |
| T21 art build risked regenerating T08 field textures | T08 field art was already accepted and not yet integrated. A silent regen would replace it. | Pikachu Art verified the field art was pixel-identical to the accepted finals and saved SHA256SUMS under T08/final/field/. | Caught before T21 wiring; T21 is still parked |
| Hand could cover End Turn; discard pile overlapped the button; Thunderbolt text dropped its damage number | Combat chrome would be unreadable or unclickable with a full hand. | Fan right edge at x 1640 or less, piles at y 1020 or lower on screen, End Turn moved to (1760, 894) with a 12 px clearance test, templated card text with boost color, unaffordable cards dimmed. | e05c22f |
| T23 SHA plate at [24, 1012, 500, 52] overlapped the draw pile | The playtest plate would cover combat chrome. | Per-scene anchors in artLayout.ts; combat plate top-center; map plate camera-fixed; overlap test against manifest widgets. | ef76f59 |
| T18 rest-site render faced the cards, not the fire | The accepted rest scene had Pikachu looking the wrong way, and Rest stayed live at full HP. | Review accepted the art with build-time fixes: face the fire (nose x left of body center) and dim Rest at full HP. | Ticketed for T18; not yet built |
| An enemy-target card might be aimed at Pikachu | That would be an illegal play if combat accepted it. | Engineer confirmed combat already rejects it before the T02 push. A formal test was folded into T15 as T16. | Confirmed for 5b0684c; test landed in c7442ca |
| A presentation tween that never finishes can leave combat busy | End Turn never returns if a pose onComplete or tween never calls done. PikachuRig.playOnce completes from update(), which shutdown does not fully clear. | T15 added an InputLock on the action queue, with a 2s beat timer and a test that a stuck tween cannot freeze End Turn. | c7442ca |

Ticketed, not yet on main:

| Issue | Why it mattered | What the team did | Where it stands |
| --- | --- | --- | --- |
| Rules text started at y −20, inside the art window | Description would print over the illustration once card art is wired. | Critic caught it. T08i moves the start to −CARD.h/2 + 212 and tests real text bounds at 1× and 1.15×. | In the parked T08i ticket. |
| The original card atlas was 5.8 MB | Too large for the repo. Policy blocks that file from any commit, including a middle one. | Pikachu Art repacked to two new PNGs: 1,304,633 B and 1,142,129 B (about 2.45 MB together), hashes c6dc44fe… and a1218656…. Critic and Expert both accepted the repack. Expert added a load test that every frame on the palette atlas resolves to its cards_manifest.json rect and is opaque, and that any later re-export starts from the lossless finals in T08/final/cards/. | In the parked T08i ticket. Not pushed. |
| Frames and gem moved to atlas page 1 | A loader that always reads page 0 would show the wrong art. | T08i requires reading each frame’s page from atlas_page, plus a test that no frame name appears on both pages. | In the parked T08i ticket. |
| Highlighted damage numbers in card rules text render as a smeared blob | The `{dmg}` numeral is drawn with the bitmap `damage` font, which was made for floating hit popups. Tinting it ink turns the fill and the outline the same dark brown, and the cursor advances by the sans-serif measure width, not the bitmap width, so the next word overlaps. | Fix is logged in parked T08i: draw the numeral as bold sans text in the same run as the rest of the rules text, gold `#E8A01C` when boosted and ink otherwise. Keep the bitmap font for hit popups only. Add a test that each text run’s left x starts at or after the previous run’s right edge. | In the parked T08i ticket. Non-blocking; not pushed. |

Not counted above: on Nov 16 at 8:53 AM CT you playtested `e05c22f` and found combat card descriptions missing. That was a T06+T07 regression. The team traced it to body text sitting under the background and added a display-list test (visible, alpha above 0, above bg, inside the rules box) to T15. The fix landed in `c7442ca`, which draws card rules text above the card background.

## Build sessions run without you

*Engineer ran each session with local Grok Build on StronkBoi, one ticket at a time, after Review approved the plan. Commit times below are from git, already in CT. Intermediate SHAs that were held or withdrawn are noted; only the final SHA was pushed.*

| Ticket | Branch | Final SHA | Local commit (CT) | Session notes |
| --- | --- | --- | --- | --- |
| T01 | main | ee32284 | Nov 15, 12:41 PM | Scaffold. First commit on an empty private repo. |
| D1 | Not named in QUEUE | bfdf6f1 | Nov 15, 1:36 PM | One demo-slice session during the usage freeze you ordered. |
| T12 | Not named in QUEUE | 75414b8 | Nov 15, 2:40 PM and 6:03 PM | First commit b83285f, then a hotfix. |
| T02 | t02 | 5b0684c | Nov 15, 6:40 PM | Statuses, eight more cards, save and restore. Built from 75414b8. |
| T09 | t09 | a33214b | Nov 15, 7:21, 7:41, and 7:47 PM | 58ab12e and 70af78d were held and not pushed alone. |
| T03 | t03 | dc6038a | Nov 15, 9:55 PM | f22d132 held, dc71707 withdrawn, then squashed onto a33214b. |
| T17 | t17 | 1757fa1 | Nov 15, 10:18 and 10:31 PM | 893dd7f held; coin and shelf fixup on top. |
| T24 | t24 | 5d7b82c | Nov 15, 10:59 PM | 400/400 full-run seeds in 81s before push gates. |
| T23 | t23 | ef76f59 | Nov 16, 12:37 AM | 182 tests, 10 smoke, full-run 400/400 in 79.5s. |
| T24b | t24b | dd46fa1 | Nov 16, 4:22 AM | Sharded 25.3s vs 104.2s single-worker. |
| T06+T07 | t0607 | e05c22f | Nov 16, 7:09 AM | 226 tests. Perf 0/73 dropped on ANGLE D3D11 Intel. Pushed later, at about 8:40 AM CT. |
| T15 | t15 | c7442ca | Nov 16, morning, before the 10:56 AM CT push | Two commits on e05c22f: 9d0d9d0 (input lock, capture accrual removal, RunState v3, full-run re-baseline) and c7442ca (card rules text drawn above the card background). Demo pack green: 241 tests in 55 files, 10/10 smoke, perf 0 of 75 frames dropped at 59.88 Hz on Intel UHD. Last ticket. |

Art work by Pikachu Art ran in parallel and is not in this table. Delivered sets live under `/workspace/pikachu_art/` for T05, T06/T07, T08, T08i, T09 map, T10, T13, T17 restyle, T18, T21, and T22.

## GitHub pushes without you

*Advocate pushed each named SHA, fast-forward only, after Coordinator named it, Policy ALLOW, a clean intent check, a Demo pack, and Review clearance. You did not have to approve the individual pushes. The repo stayed private. No force-push.*

| Ticket | SHA | From | Push time (CT) | Commits in the push |
| --- | --- | --- | --- | --- |
| T01 | ee32284 | Empty repo | Nov 15, after the 12:54 PM freeze and before the D1 commit at 1:36 PM. Exact minute not recorded. | 1 |
| D1 | bfdf6f1 | ee32284 | Nov 15, between the 1:36 PM commit and your 1:43 PM playtest. Logged as shipped at 1:43 PM CT. | 1 |
| T12 + hotfix | 75414b8 | bfdf6f1 | Nov 15, 6:18 PM CT in the ticket table. The same log also has 7:10 PM ET, which converts to 6:10 PM CT. | 2 (b83285f + 75414b8) |
| T02 | 5b0684c | 75414b8 | Nov 15, 7:01 PM CT in the ticket table. The same log also has 7:53 PM ET, which converts to 6:53 PM CT. | 1 |
| T09 | a33214b | 5b0684c | Nov 15, 8:28 PM CT | 3 (58ab12e, 70af78d, a33214b) |
| T03 | dc6038a | a33214b | Nov 15, 10:02 PM CT | 1 (squash) |
| T17 | 1757fa1 | dc6038a | Nov 15, 10:34 PM CT (logged as 11:34 PM ET) | 2 (893dd7f + 1757fa1) |
| T24 | 5d7b82c | 1757fa1 | Nov 15, 11:24 PM CT (logged as 12:24 AM ET Nov 16) | 1 |
| T23 | ef76f59 | 5d7b82c | Nov 16, about 2:06 AM CT | 1 |
| T24b | dd46fa1 | ef76f59 | Nov 16, about 5:27 AM CT | 1 |
| T06+T07 | e05c22f | dd46fa1 | Nov 16, about 8:40 AM CT | 1 |
| T15 | c7442ca | e05c22f | Nov 16, about 10:56 AM CT | 2 (9d0d9d0 + c7442ca) |

GitHub main after the last push is `c7442ca`. Policy ALLOW, and Review (Critic and Expert) had no objection. Advocate pushed it as a fast-forward `e05c22f..c7442ca`. The repo is still private. This was the final ticket; production is now closed.

## Directional decisions made without you

*Design and plan calls made by Demo Project Review or Coordinator under the rule you set: consensus approves a ticket plan or design detail, and you still own money, visibility, tokens, force-push, Legacy, and core spec changes.*

| When (CT) | Decision | Who |
| --- | --- | --- |
| Nov 15, afternoon | T07 recommendations: trainer and partner are separate targets; trainer KO removes the partner. Enemy cap was first discussed as 4, then the approved T06+T07 plan kept it at 3. | Review |
| Nov 15, ~6:52 PM | T09 map shape: rows 1–4 fights with no elites in rows 1–2, shop on row 5, mixed rows 6–7, rest on row 8, boss on row 9. checkMap requires 8 nodes before the boss and at least two different paths. | Review |
| Nov 15, ~7:13 PM | T03 bot searches play orders each turn, reports per-card stats, has no win-rate floor, and commits the first run as a baseline. | Review |
| Nov 15, ~7:26 PM | T14 Charge rules: bonus on lightning hits only, read once per play, a Charge-granting card does not consume the old Charge, damage order is base + INT then ×1.5 Charge then Vuln/Weak, rounded down once, no stacking. | Review |
| Nov 15, ~8:14 PM | Combat chrome rules later built in T06+T07: hand fan x ≤ 1640, hover stays out of the HP band, piles at y ≥ 1020, templated card text, dim unaffordable cards, real-hardware perf gate. | Review |
| Nov 15, ~8:42 PM | Each evolution stone gets one data-defined trigger, not a flat stat (Thunder starts the fight Charged, Moon is +1 energy on turn one, and so on). Sell price is 50% of buy, floored. Level-up picks queue and are not lost. No duplicate stones in shop or drop pools. | Review, after your T10 design |
| Nov 15, ~9:27 PM | Rest site shows a real heal amount, Leave stays enabled, upgrade stays locked as Coming soon, Pikachu faces the fire. | Review |
| Nov 15, ~10:02–10:04 PM | First playable milestone is title → new run → act 1 (map, fights, shop, rest, boss, loot, XP and a stat pick) → win or Caught → title. Act 2 (T21) stays in that milestone but is built last; if it slips, boss goes to a win screen. T19 and number tuning stay parked. | Review |
| Nov 15, late evening | New playtest and safety tickets: title/win/Caught screens (T22), SHA and seed overlay plus a note hotkey (T23), and a multi-seed full-run smoke after every ticket (T24 / T24b). | Review |
| Nov 16, ~8:58 AM | Keep the cards at 240×336, the size the art was drawn at, and make on-screen scale a separate setting. You had said “use best judgement” rather than picking the size yourself. | Advocate, then Review agreement |

Early Nov 15 group notes also say the boss as a 9th node, the row-5 shop, and the flat INT bonus were “group consensus, covered by Paul’s queue approval.” Those may already have been inside the plan you signed off, so they are not listed as decisions made without you.

Review accepted the pink and cream Jigglypuff shop restyle at 8:42 PM CT, after your feedback. You also approved that restyle directly with Pikachu Art at 9:19 PM CT, so it is not treated as a team-only call.

## Hard pauses that needed you

*The team stopped, or should have stopped, until you decided. Your call is in the last column.*

| When (CT) | The pause | What you decided |
| --- | --- | --- |
| Nov 15, early | New project setup, including whether to create a repo at all. | Yes to a new private repo, a new design bot (not Legacy’s), a branching map, INT scaling spells past a threshold with no locking, and a signed-off plan. You also said yes to creating the repo. |
| Nov 15 | Repo visibility and distribution (IP). | The repo stays private permanently. The game is never distributed. Public or shareable deploys are blocked, not escalated. |
| Nov 15 | Who approves ordinary ticket plans. | Review consensus approves a plan or design detail. You still decide money, visibility, tokens, force-push or history deletion, anything touching Legacy, and core spec changes. |
| Nov 15 | Borrowing UI Bot from Legacy for T07. | You allowed it. That sits in the Legacy bucket you kept for yourself. |
| Nov 15 | T05 art style (a taste call). An earlier Paper Mario revision was pending you, then you picked between options. | Style A, dark outline. Later: reuse the frames to cover as many moves as possible; names are flexible; lore consistency is not required; Bite/Scratch closed. |
| Nov 15, 12:54 PM | Weekly usage was about 93%, with $0 credits. | Demo freeze. Ship a locally playable D1 slice, then pause the rest. |
| Nov 15, 1:43 PM | You playtested D1. | Combat and animations were good, and you reached victory. You flagged no play-again option and lifted the freeze. That created T12. |
| Nov 15, 3:57 PM | How fast to work after the freeze. | Work non-stop and pipelined: one ticket in Build, next plan drafted during review, art in parallel. |
| Nov 15, ~6:52 PM | Q2, capture, was still open. | Capture is low priority and goes to the backlog, left off until then. You also gave the design: a heads-up throw, a timed deflect that gets harder as HP drops, a rocking ball with timed escapes, and capture at 0 HP. |
| Nov 15, evening | What the currency and the big stones are. | Shiny Stones are the currency. The larger Pokémon stones (Moon Stone, Thunder Stone, and the rest) are passive buffs. |
| Nov 15, 8:21 PM | How T10 progression and boss loot work. | Stat picks come from XP level-ups. Boss fights drop relics or evolution stones with passive buffs, like Slay the Spire relics. |
| Nov 15, 8:28 PM | T17 art was held for your restyle notes. | Better Jigglypuff, a cuter shop in Jigglypuff colors, a lighter level-up screen. Layout and box sizes stay the same. You later approved the restyle directly with Pikachu Art at 9:19 PM. |
| Nov 15, 9:19 PM | Whether to keep building overnight. | Overnight work through 8:00 AM CT on Nov 16. |
| Nov 15, evening | Game title for T22. | Sir Sparks-a-lot, replacing Little Spark. |
| Nov 15, 10:00 PM | Whether to spend a ticket on bot-driven balancing. | Build a playable game with the art wired in first. Balance later from your playtest notes, not from bot predictions. T19 is parked. No number tuning until your notes arrive. |
| Nov 15, 11:21 PM | T21 act 2 setting, options A or B. | Option A, Seaside Route (Misty and Starmie). |
| Nov 16, 8:53 AM | You playtested e05c22f. | Mostly good, but card descriptions were missing, and you want the card art. The text fix went into T15. Card-art integration became T08i, queued next, then parked when you closed production. |
| Nov 16, morning | Card size, after Review asked whether to keep 240×336. | Use best judgement. The team kept 240×336, the size the art was drawn at, and made on-screen scale a separate setting. |
| Nov 16, about 9:00 AM | Whether to keep opening new work. | The next completed ticket closes production for now. T15 is last. After it is pushed, stop. |

Still open, as far as the ledger shows. The team should not guess at these:

- Whether passive stones can still be sold at the shop, or the sell well is dropped. QUEUE recorded this as open for you. Review later specified a 50% sell price in the T10 design. It is not clear you closed the question yourself.
- How card upgrades work at rest. Review asked you at 9:25 PM CT on Nov 15.
- Whether there should be a dev skip-ahead option. Review asked after the T24 plan.

## Current state and parked queue

*As of Monday, Nov 16, 2026, about 10:56 AM CT.*

> **Production is closed**
>
> Production is closed as of about 10:56 AM CT on Nov 16, after the T15 push. The queue is frozen. Policy will BLOCK any later push until you reopen production. When you reopen it, T08i goes first, then T08j and T14.

GitHub main is `c7442ca` (T15), a fast-forward from `e05c22f`. That build has combat chrome, the hand fan, drag-to-target, move scripts, lightning FX, the real-GPU perf gate, an input lock while animations play, capture accrual removed (capture stays in the backlog), and card rules text drawn above the card background. Card descriptions show again in combat. It does not include the accepted card illustrations. One known issue remains: highlighted damage numbers in card rules text look smeared; the fix is logged in parked T08i.

| Ticket | What it would have been | Why it is waiting |
| --- | --- | --- |
| T08i | Wire the 7 existing cards to the repacked atlas, fix rules-text position, add page-loading and layout tests, and fix the smeared highlighted damage numbers. | Parked. Production is closed. Critic and Expert both accepted the repack. Expert added a load test that every frame on the palette atlas resolves to its cards_manifest.json rect and is opaque, and that re-exports start from the lossless finals. When production reopens, T08i goes first. |
| T08j | Add the 8 pending cards with placeholder numbers and wire their art, then re-baseline the full-run guard. | Parked. Content still waits on you. Next after T08i. |
| T14 | Charge applies to the whole lightning card. | Parked after T15 became the last ticket. Next after T08j. |
| T18 | Rest-site UI, with accepted art and the face-the-fire build notes. | Parked. Card upgrades still need you. |
| T04a | STR, DEX, and CON math with tests. | Parked. |
| T20 | XP and queued level-up stat picks, using accepted T10 art. Needs T04a. | Parked. |
| T10 | Boss relics and evolution stones, shop stock, sell rules. | Parked. Sell-well question may still be open. |
| T22 | Title, win, and Caught screens. Title is Sir Sparks-a-lot. Art accepted. | Parked. |
| T21 | Minimal act 2, Seaside Route, built last. Art accepted, with Sailor and Tentacool. | Parked. |
| T19 | Harder encounter and bot scoring for defensive cards. | Parked earlier, by your art-first ruling. |

Also unbuilt, and already behind that parked list: T04b (INT stats), T11 (slice review), and T13 (audio integration). Capture stays on the backlog, off in the game, per your Q2 close.

[Back to top](#sir-sparks-a-lot-project-breakdown)

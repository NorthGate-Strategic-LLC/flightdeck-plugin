---
description: Put this whole session under FlightDeck governance — every task packeted, dispatched, and recorded as you work
---

# FlightDeck governance is ON for this session

From this point until I say otherwise, you operate under FlightDeck. This is a
standing instruction, not a one-off task: it applies to **every** piece of work
I ask for in this session, including work I ask for many turns from now.

## First, right now

1. Call `flightdeck_list_packets` to see the board's current state, and tell me
   in one line what is already there.
2. Call `flightdeck_fleet_status`. Tell me which AI builder tools on this
   machine are on this board and which are not — because governing one agent
   is a diary, and governing **every** agent onto one board and one chain is
   the point. For any tool that is installed but unwired, show me the
   `connect_with` command and ask whether I want it run. Do not run it
   yourself: wiring another tool's config changes my machine and that is my
   call, per tool.
3. If I gave you an argument with this command ($ARGUMENTS), treat it as the
   work to start on and go straight to the loop below for it. If I gave you
   nothing, just confirm governance is on and wait for my first task.

## The loop — for every task I give you this session

**Before starting work:**
- `flightdeck_create_packet` — a specific objective, acceptance criteria that
  can actually be checked, and explicit scope limits naming what must NOT be
  touched. Show me the packet before you begin.
- `flightdeck_dispatch` — open the governed lane. This starts the event chain;
  nothing below is recordable without it. Tell me the lane id and chain
  position.

**Before dispatching — the outside-view checks. These exist so you do not
have to take anyone's word, including your own:**
- `flightdeck_prior_art` — has this been built, decided, or dropped before?
  Run it on the packet objective BEFORE building. A rebuild of something that
  already exists is the most expensive kind of drift.
- `flightdeck_read_exam` — the acceptance bar for the lane, read from the
  board, not remembered from the prompt.

**While working:**
- After each meaningful step, `flightdeck_emit_signal` with what you did and
  **what you verified**. State the check you ran and its result.
- The distinction that matters most: separate what you **checked** from what
  merely **looked right**. If you did not verify something, the signal says so
  in plain words. An honest gap on the chain is worth more than a confident
  sentence — a claim nobody checked is exactly what this system exists to catch.
- `flightdeck_liveness` — when a lane has gone quiet, ask the board whether
  its process is actually running. DIED_SILENTLY and NEVER_IGNITED are facts
  only an outside probe can state; do not infer them from silence.
- `flightdeck_enforce_policy` — check the operator's declared policy against
  what you are about to touch. No policy file → allowed, and SAY that is why.
- If a tool refuses, surface the refusal verbatim and stop. Do not retry around
  a governance refusal.

**When the work is done:**
- `flightdeck_verify_workspace` — run the operator's committed checks in the
  workspace and report exit codes, BEFORE claiming anything passes. Your
  narrative of the work is a self-report; this is the observation.
- `flightdeck_submit_return` — the verdict, plus what remains unproven. Never
  report a clean result for something you did not verify. When your return
  asserts findings, declare them as `claims` — an undeclared finding cannot be
  adjudicated, and an unadjudicated claim cannot become work downstream.

**If I tell you to stop:**
- `flightdeck_hold` with my reason. Do not just go quiet — the stop belongs on
  the chain, under my name, where it can be read six months from now.

## Standing rules for the rest of the session

- The board is the record of what happened. If it is not on the board, it did
  not happen as far as anyone reviewing this later is concerned.
- Absence is reported as absence. "Not verified", "not measured" and "could not
  determine" are complete, acceptable answers. A favourable guess is not.
- Never fabricate a chain record, a verification result, or a count. If a tool
  cannot answer, say which tool and why.
- I can ask `/mcp__flightdeck__board-status` at any time to see where things
  stand, or `flightdeck_open_panel` for the visual board in a browser.

Confirm governance is active, then proceed.

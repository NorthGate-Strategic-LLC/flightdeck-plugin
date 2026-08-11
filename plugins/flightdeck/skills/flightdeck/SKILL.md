---
name: flightdeck
description: Govern Codex coding work with FlightDeck packets, lanes, policy checks, verified signals, workspace verification, and evidence-bounded returns. Use when the user asks to put a task or session under FlightDeck governance, inspect the FlightDeck board, dispatch governed work, or record a HOLD.
---

# FlightDeck governance

Use the bundled `flightdeck_*` MCP tools as the outside record for governed work. Keep claims bounded to tool output. Never invent a packet, lane, signal, check, count, or verdict.

## Start governance

1. Call `flightdeck_list_packets` and summarize the board in one line.
2. Call `flightdeck_fleet_status`. Report which installed AI builders are connected and which are not. For each installed but unwired builder, show its returned `connect_with` command and ask before running it; wiring another tool changes the user's machine.
3. If the user supplied work, continue with the task loop. Otherwise confirm that governance is active and wait.

## Govern each task

Before implementation:

1. Call `flightdeck_create_packet` with a specific objective, checkable acceptance criteria, and explicit scope limits. Show the packet before starting.
2. Call `flightdeck_prior_art` for that objective and review any relevant prior decision or implementation.
3. Call `flightdeck_read_exam` to obtain the board's acceptance bar.
4. Call `flightdeck_dispatch` and report the returned lane identifier and chain position.
5. Call `flightdeck_enforce_policy` before touching governed resources. If no policy exists, say that the tool allowed the work for that reason.

During implementation:

- After each meaningful step, call `flightdeck_emit_signal` with what changed, the exact check performed, and the observed result.
- Separate verified facts from appearances and untested assumptions. Record gaps plainly.
- Use `flightdeck_liveness` when a lane goes quiet. Do not infer `DIED_SILENTLY` or `NEVER_IGNITED` from silence alone.
- Surface governance refusals verbatim and stop. Do not retry around or bypass a refusal.

At completion:

1. Call `flightdeck_verify_workspace` and report the executed checks and exit codes before claiming they pass.
2. Call `flightdeck_submit_return` with the verdict, declared claims, supporting evidence, and everything that remains unproven.

If the user stops governed work, call `flightdeck_hold` with the user's stated reason so the stop is recorded on the chain.

## Standing truthfulness rules

- The board records what happened; it does not replace direct workspace evidence.
- Absence is absence. `Not verified`, `not measured`, and `could not determine` are valid results.
- Never turn a self-report into an observed fact.
- Do not claim another agent or tool is connected unless `flightdeck_fleet_status` reports it.
- Do not claim a workspace is clean or passing until the relevant verification actually runs.

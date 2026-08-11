# FlightDeck — Codex and Claude Code plugin

The governed-engineering rail for Codex and Claude Code: every AI coding agent on your
machine dispatched onto **one board**, with a hash-chained event ledger, HOLD,
claim adjudication, scope observation (git-observed, never self-reported),
liveness ("is anything actually running, and for how long"), and cost
instruments that treat unknown as unknown — never as zero. And **the Cue**
(`flightdeck_cue`) — your lane's next valid governed move, surfaced right inside
the coding agent (ships in `flightdeck-connect` 0.5.2).

## Requirements

- **[uv](https://docs.astral.sh/uv/)** on PATH (`uvx` launches the server;
  `pip install uv` or the one-line installer). Verified: `uvx --from
  flightdeck-connect conductor-mcp` cold-boots from PyPI and serves the full
  flightdeck tool set — 26 tools as of `flightdeck-connect` 0.5.2, including
  the Cue (`flightdeck_cue`).
- Python 3.9+.

No uv? Install the package once (`pip install flightdeck-connect`) and use
this MCP config instead — same server, same tools:

```json
{
  "mcpServers": {
    "flightdeck": {
      "command": "conductor-mcp",
      "env": { "MCP_TOOL_SET": "flightdeck" }
    }
  }
}
```

## Install in Codex

```powershell
codex plugin marketplace add NorthGate-Strategic-LLC/flightdeck-plugin
codex plugin add flightdeck@flightdeck
```

Start a new Codex task after installation, then ask:

> Put this task under FlightDeck governance.

## Install in Claude Code

```
/plugin marketplace add NorthGate-Strategic-LLC/flightdeck-plugin
/plugin install flightdeck@flightdeck
```

The MCP server is pulled from PyPI
([`flightdeck-connect`](https://pypi.org/project/flightdeck-connect/)) via
`uvx` — pure stdlib, zero runtime dependencies, Python 3.9+.

Then in any Claude Code session: `/flightdeck` turns governance on. Set `FLIGHTDECK_BOARD`
to your board folder (a board is just a local folder — your first
`flightdeck_create_packet` creates it).

## Privacy

Local-first: board tools send nothing anywhere — no telemetry, no analytics,
no phone-home. The cloud tool family is inert without an operator-issued
enrollment token. Full policy: <https://ai-flightdeck.com/privacy>

Support: <https://ai-flightdeck.com/support>

## License

The plugin wrapper (this repo) and the `flightdeck-connect` package are
proprietary — free to install and use; see the package license. U.S. patent
pending (incl. App. No. 19/765,031). © Northgate Strategic LLC.

# FlightDeck for Codex

FlightDeck adds a local governance rail to Codex coding work: scoped task packets, governed lanes, policy and prior-art checks, verified progress signals, workspace verification, and an evidence-bounded return.

The plugin launches the published `flightdeck-connect` 0.5.1 MCP package through `uvx`. With the local FlightDeck tool set configured here, its board and event chain are handled on the machine running the server.

## Requirements

- Codex with plugin support
- [`uv`](https://docs.astral.sh/uv/) installed with `uvx` available on `PATH`
- Network access on first launch so `uvx` can obtain the pinned package if it is not cached

## Install from this local checkout

```powershell
codex plugin marketplace add C:\flightdeck-plugin
codex plugin add flightdeck@flightdeck
```

After the repository is published, the same marketplace can be added from GitHub:

```powershell
codex plugin marketplace add NorthGate-Strategic-LLC/flightdeck-plugin
codex plugin add flightdeck@flightdeck
```

Start a new Codex task after installation so the MCP server and skill are loaded, then ask:

> Put this task under FlightDeck governance.

## Boundaries

- FlightDeck records governed work; it does not prove an unperformed check.
- The skill reports missing evidence as missing and does not bypass governance refusals.
- Connecting other AI tools may change their local configuration. FlightDeck will show the relevant command and request approval first.
- This package is for local or Git-backed Codex marketplace distribution. It is not a submission to OpenAI's public Plugins Directory, which requires a stable public HTTPS MCP endpoint and separate review.

### Fallback when `uvx` is unavailable

Install the same pinned package into Python and register its executable directly:

```powershell
python -m pip install flightdeck-connect==0.5.1
codex mcp add flightdeck --env MCP_TOOL_SET=flightdeck -- conductor-mcp
```

This manual MCP registration is an alternative to the plugin-managed server, not a second server to run at the same time.

Privacy policy: <https://ai-flightdeck.com/privacy>

Support: <support@northgatestrategic.com>

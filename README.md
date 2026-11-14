# PRAXO-CORE for Elixir

PRAXO-CORE is an embeddable, MIT-licensed agent framework. This package is its native Elixir Core with source tag `elixir/v0.8.0`. It passes all eleven shared vector groups with `Elixir 1.20.4` on `Erlang/OTP 29` and includes the native agent loop, context compaction, memory store, path policy, checkpoint allowlist, tool-call parsing, and opt-in tool selection, PII redaction, structured output validation, call limits, and human-in-the-loop interrupt decisions. Vector coverage does not establish full Core parity or production readiness.

## At a glance

| Field | Value |
| --- | --- |
| Package | `praxo_core` |
| Registry | [Hex](https://hex.pm/packages/praxo_core) |
| Install | `{:praxo_core, "~> 0.8.0"}` |
| Source version | `0.8.0` |
| Published version | `0.8.0` |
| Source tag | `elixir/v0.8.0` |
| Tier | Core |
| Contract | `SPEC_VERSION` `0.2.0` |
| Documentation | https://axisvela.github.io/praxo-core/languages/elixir/ |
| License | MIT |

## Highlights

- OpenAI-compatible model: native
- Anthropic model: native
- Gemini model: native
- MCP client: native
- Harmovela sink: native
- OpenTelemetry sink: native (transport seam)
- Subagent delegation: native
- Retriever: native

## Quick start

Install the published package:

```elixir
{:praxo_core, "~> 0.8.0"}
```

See the [full Elixir README](language/elixir/README.md) for complete installation, build, and verification commands.

## What's included

| Capability | Status | Detail |
| --- | --- | --- |
| OpenAI-compatible model | native | `Praxo.OpenAICompatible` |
| Anthropic model | native | `Praxo.Anthropic` |
| Gemini model | native | `Praxo.Gemini` |
| MCP client | native | `Praxo.Mcp`; stdio, plus `Praxo.McpHttp.transport` for Streamable HTTP 2025-03-26 |
| Harmovela sink | native | `Praxo.HarmovelaSink` |
| OpenTelemetry sink | native (transport seam) | `Praxo.OtelSink`; caller supplies OTLP/HTTP transport |
| Subagent delegation | native | `Praxo.SubagentManager` |
| Retriever | native | `Praxo.Document`, `Praxo.FuncRetriever` |

## Examples

Runnable examples live under [`language/elixir/examples`](language/elixir/examples).

| Example | What it shows |
| --- | --- |
| [checkpoint](language/elixir/examples/checkpoint) | This example uses the Elixir Core checkpoint allowlist to encode and decode only registered payload types. |
| [consumer](language/elixir/examples/consumer) | This module uses published Hex `praxo_core` `0.8.0` and verifies an allow/deny governed tool path without local replacements. |
| [event-sink](language/elixir/examples/event-sink) | This example uses the Elixir Core sink composition to fan out lifecycle and tool events and filter the tool-only stream. |
| [hitl](language/elixir/examples/hitl) | This example demonstrates a write tool that requires human approval: |
| [identity-policy](language/elixir/examples/identity-policy) | This example binds a trusted principal to policy decisions and rejects missing, inactive, role-mismatched, and tenant-mismatched actions. |
| [live-model](language/elixir/examples/live-model) | This source-mode example connects the Elixir Core to an OpenAI-compatible endpoint and registers one low-risk `get_time` tool. |
| [mcp](language/elixir/examples/mcp) | This example uses a caller-owned in-process transport with the Elixir MCP client. It covers initialize, `tools/list`, and `tools/call` without a server process. |
| [provider-fallback](language/elixir/examples/provider-fallback) | This example calls a fallback only after the primary fails and preserves the primary failure when both fail. |
| [retry](language/elixir/examples/retry) | This example retries a transient failure with a bounded attempt count and keeps the exhausted failure state. |
| [service](language/elixir/examples/service) | This example defines a transport-neutral request handler boundary with health, principal, and run cases. Wire it into any Elixir HTTP server. |
| [session-checkpoint](language/elixir/examples/session-checkpoint) | This example saves and restores a conversation history across two agent turns using the Core checkpoint allowlist. |
| [streaming](language/elixir/examples/streaming) | This example collects agent stream parts from the Elixir Core and checks the `values` and `messages` lifecycle. |
| [structured-output](language/elixir/examples/structured-output) | This example validates a final JSON answer against a schema and rejects invalid output. |

## Verify

Run the checks from `language/elixir`:

```bash
elixirc -o build/ebin lib/praxo/*.ex lib/praxo/adapters/*.ex
elixir -pa build/ebin tests/run_tests.exs
cd ../..
python language/elixir/api-snapshot.py --check
elixir -pa language/elixir/build/ebin language/elixir/conformance/run.exs
```

This mirror contains the language source and the shared `spec/` vectors, so the implementation can be built and tested here. See [`language/elixir/README.md`](language/elixir/README.md) for the exact commands. The monorepo CI runs conformance, API snapshot, and native tests for this implementation.

## Community

- X: <https://x.com/axisvela>
- Weibo: <https://weibo.com/u/1936025761>

## Repository layout

- `language/elixir/` — implementation source, tests, API snapshot, and examples
- `spec/` — shared contract, vectors, and parity inventories
- `LICENSE` — MIT license

## Canonical source

- Canonical source: https://github.com/axisvela/praxo-core/tree/main/language/elixir
- Registry introduction: `language/elixir/REGISTRY.md`
- Machine-readable entry: `language/elixir/llms.txt` and `language/elixir/llms.md`
- Mirror repository: https://github.com/axisvela/praxo-core-elixir
- Release index: https://axisvela.github.io/praxo-core/languages/registry-status/

This repository is a discovery mirror of the canonical Elixir source. The monorepo remains the source of truth and the release workflow source.

PRAXO-CORE is not a hosted model, workflow engine, identity provider, or safety controller. Do not infer exactly-once execution, complete sandbox isolation, production security certification, live-provider behavior, or physical safety from this package.

MIT licensed.

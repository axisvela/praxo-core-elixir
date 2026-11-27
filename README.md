# PRAXO-CORE for Elixir

PRAXO-CORE is an embeddable, MIT-licensed agent framework. This package is its native Elixir Core with source tag `elixir/v0.11.1`. It passes all eleven shared vector groups with `Elixir 1.20.4` on `Erlang/OTP 29` and includes the native agent loop, context compaction, memory store, path policy, checkpoint allowlist, tool-call parsing, and opt-in tool selection, PII redaction, structured output validation, call limits, and human-in-the-loop interrupt decisions. Vector coverage does not establish full Core parity or production readiness.

## At a glance

| Field | Value |
| --- | --- |
| Package | `praxo_core` |
| Registry | [Hex](https://hex.pm/packages/praxo_core/0.11.1) |
| Install | `{:praxo_core, "~> 0.11.1"}` |
| Source version | `0.11.1` |
| Published version | `0.11.1` |
| Publication status | published |
| Canonical source tag | [`elixir/v0.11.1`](https://github.com/axisvela/praxo-core/tree/elixir/v0.11.1) |
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
{:praxo_core, "~> 0.11.1"}
```

See the [full Elixir README](language/elixir/README.md) for complete installation, build, and verification commands.

## What's included

| Capability | Status | Detail |
| --- | --- | --- |
| OpenAI-compatible model | native | `Praxo.OpenAICompatible`; `streaming_model/1` and SSE reassembly cover content, tool calls, usage, and finish reason |
| Anthropic model | native | `Praxo.Anthropic`; `streaming_model/1` reassembles Anthropic SSE |
| Gemini model | native | `Praxo.Gemini`; `streaming_model/1` reassembles Gemini SSE |
| MCP client | native | `Praxo.Mcp`; stdio, plus `Praxo.McpHttp.transport` for Streamable HTTP 2025-03-26 |
| Harmovela sink | native | `Praxo.HarmovelaSink` |
| OpenTelemetry sink | native (transport seam) | `Praxo.OtelSink`; caller supplies OTLP/HTTP transport |
| Subagent delegation | native | `Praxo.SubagentManager` |
| Retriever | native | `Praxo.Document`, `Praxo.FuncRetriever` |

## Examples

Runnable examples live under [`language/elixir/examples`](language/elixir/examples).

| Example | What it shows |
| --- | --- |
| [advanced-delegation](language/elixir/examples/advanced-delegation) | Application-level governed delegation checks for the Elixir Core. |
| [checkpoint](language/elixir/examples/checkpoint) | This example uses the Elixir Core checkpoint allowlist to encode and decode only registered payload types. |
| [consumer](language/elixir/examples/consumer) | This module uses published Hex `praxo_core` `0.11.1` and verifies an allow/deny governed tool path without local replacements. |
| [event-sink](language/elixir/examples/event-sink) | This example uses the Elixir Core sink composition to fan out lifecycle and tool events and filter the tool-only stream. |
| [hitl](language/elixir/examples/hitl) | This example demonstrates a write tool that requires human approval: |
| [identity-policy](language/elixir/examples/identity-policy) | This example binds a trusted principal to policy decisions and rejects missing, inactive, role-mismatched, and tenant-mismatched actions. |
| [live-model](language/elixir/examples/live-model) | This source-mode example connects the Elixir Core to an OpenAI-compatible endpoint and registers one low-risk `get_time` tool. |
| [mcp](language/elixir/examples/mcp) | This example uses a caller-owned in-process transport with the Elixir MCP client. It covers initialize, `tools/list`, and `tools/call` without a server process. |
| [provider-fallback](language/elixir/examples/provider-fallback) | This example calls a fallback only after the primary fails and preserves the primary failure when both fail. |
| [representative-chain](language/elixir/examples/representative-chain) | This deterministic example exercises the same application seams as the Go, Python, and TypeScript representative chains without a live provider: |
| [retry](language/elixir/examples/retry) | This example retries a transient failure with a bounded attempt count and keeps the exhausted failure state. |
| [service](language/elixir/examples/service) | This example defines a transport-neutral request handler boundary with health, principal, and run cases. Wire it into any Elixir HTTP server. |
| [session-checkpoint](language/elixir/examples/session-checkpoint) | This example saves and restores a conversation history across two agent turns using the Core checkpoint allowlist. |
| [streaming](language/elixir/examples/streaming) | This example collects agent stream parts from the Elixir Core and checks the `values` and `messages` lifecycle. |
| [structured-output](language/elixir/examples/structured-output) | This example validates a final JSON answer against a schema and rejects invalid output. |

## Scenario Tutorials

Scenario-oriented tutorials live under `language/elixir/Tutorial`. Planning context: [Tutorial Plan](https://axisvela.github.io/praxo-core/getting-started/tutorial-plan/), [100 candidate agent scenarios](https://axisvela.github.io/praxo-core/getting-started/agent-scenarios/), and [Tutorial Catalog](https://axisvela.github.io/praxo-core/getting-started/tutorial-catalog/).

| Path | What it shows |
| --- | --- |
| [Tutorial](language/elixir/Tutorial) | - [Knowledge Maintenance (OP-03)](https://github.com/axisvela/praxo-core/blob/main/language/elixir/Tutorial/knowledge-maintenance/README.md): source Elixir Core, fixed knowledge diff and a review-only revision draft; no Wiki writes. |
| [aiops-rca](language/elixir/Tutorial/aiops-rca) | Fixed trace/metric/log signals yield suspect `checkout-api` and a review-only rollback. No live telemetry or remediation. |
| [community-governance](language/elixir/Tutorial/community-governance) | Fixed issues produce four classified items and a review-only reviewer request. No GitHub API, closure or impersonation. |
| [knowledge-maintenance](language/elixir/Tutorial/knowledge-maintenance) | A bounded first slice of [OP-03](https://axisvela.github.io/praxo-core/getting-started/agent-scenarios/), not an autonomous Wiki service. It diffs two fixed knowledge versions, reports changed sections and removed duplicates, and drafts a review-only revision. This uses the source Elixir Core; no network, credentials or packages beyond Elixir/OTP are required. |
| [soc-correlation](language/elixir/Tutorial/soc-correlation) | Fixed EDR/firewall events produce a critical count; one critical event selects an isolation review, clean input selects monitoring. No host blocking. |

## Reference Applications

Reference application sources live under `language/elixir/application`. See each README for implementation scope and validation status.

| Path | What it shows |
| --- | --- |
| [application](language/elixir/application) | An OTP service where the agent drives the primary incident workflow: an operator submits an incident intent, the agent searches supervised telemetry, diagnoses the suspect, and... |

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
- LinkedIn: <https://www.linkedin.com/company/axisvela/>
- Facebook: <https://www.facebook.com/profile.php?id=61596905732406>
- YouTube: <https://www.youtube.com/@axisvela>
- Discord: <https://discord.com/channels/1575163993767809064/1575164343148875977>
- GitHub Discussions: <https://github.com/axisvela/praxo-core/discussions>
- GitHub Issues: <https://github.com/axisvela/praxo-core/issues>
- Documentation: <https://axisvela.github.io/praxo-core/>
- Architect: <https://axisvela.architect.pub>

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

This repository is a discovery mirror of the canonical Elixir source. The monorepo remains the source of truth and the release workflow source. The mirror's `main` branch tracks current source, not a release snapshot. Source tags refer to the canonical monorepo and are not necessarily present in this mirror; syncing the branch does not publish mirror tags or registry packages.

PRAXO-CORE is not a hosted model, workflow engine, identity provider, or safety controller. Do not infer exactly-once execution, complete sandbox isolation, production security certification, live-provider behavior, or physical safety from this package.

MIT licensed.

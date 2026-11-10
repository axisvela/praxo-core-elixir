# PRAXO-CORE for Elixir

Dedicated repository for the Elixir implementation of PRAXO-CORE: an embeddable,
MIT-licensed agent execution kernel with policy controls, human-in-the-loop
approval, checkpoints, events, and tool calling.

- Package: `praxo_core` on Hex
- Documentation: https://axisvela.github.io/praxo-core/languages/elixir/
- Consumer starter: https://github.com/axisvela/praxo-core/tree/main/examples/consumer-elixir
- Canonical source: https://github.com/axisvela/praxo-core/tree/main/language/elixir
- Release index: https://axisvela.github.io/praxo-core/languages/registry-status/

This repository is a discovery mirror of the canonical Elixir source. The
monorepo remains the source of truth and the release workflow source. Shared
conformance vectors are included under `spec/`.

## Install

```elixir
{:praxo_core, "~> 0.4.1"}
```

## Verify

From `language/elixir`:

```sh
mix deps.get
mix run -r tests/run_tests.exs
mix run -r conformance/run.exs
python api-snapshot.py --check
```

PRAXO-CORE is not a hosted model, workflow engine, identity provider, or safety
controller. Do not infer exactly-once execution, complete sandbox isolation,
production security certification, live-provider behavior, or physical safety
from this package.

MIT licensed.

# HEADING OS Marketplace

A [Claude Code](https://docs.claude.com/en/docs/claude-code) plugin marketplace
for [HEADING OS](https://github.com/mishahanin/heading-os), the operations engine
an executive runs their company from.

This repository is a **generated distribution artifact**. The source of truth is
the engine monorepo; the bundles here are built from it by
`scripts/dev/publish-marketplace.py`. Do not hand-edit anything under
`plugins/` or `.claude-plugin/`: re-run the publisher and let the diff be the
change.

## Install

Inside Claude Code:

```
/plugin marketplace add mishahanin/heading-os-marketplace
/plugin install heading-core@heading-os-marketplace
```

(Or the CLI form: `claude plugin marketplace add mishahanin/heading-os-marketplace`.)

## Bundles

| Bundle | What it carries |
| --- | --- |
| `heading-core` | Sovereignty and session core: the prime/state-check/checkpoint skills plus the standalone sovereignty guard hooks. |

Plugins here omit a `version`, so each marketplace commit is a new version and
installs update automatically. Skills call their bundled scripts through
`${CLAUDE_PLUGIN_ROOT}`, and a `SessionStart` hook resolves your data overlay
at runtime, so no private data is ever bundled.

## Sovereignty

The sovereignty-core bundle ships the guard hooks, and the engine's non-bypassable
push-time content scan and the `send_capable -> gated` invariant remain the
backstops. Outbound send stays human-gated everywhere; nothing here changes that.

## License

Apache-2.0, matching the engine. See `LICENSE`.

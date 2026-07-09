# HEADING OS Marketplace

[HEADING OS](https://github.com/mishahanin/heading-os) is the sovereign
operations engine an executive runs their company from: a library of skills,
always-on guards, and session tooling that turns an AI assistant into a
strategic operator.

This marketplace is how you install pieces of that engine. Each bundle below
carries a slice of HEADING OS you can add to your workflow in two commands, with
no clone and no toolchain.

It is a **generated distribution artifact**. The source of truth is the HEADING
OS engine monorepo; the bundles here are built from it by
`scripts/dev/publish-marketplace.py`. Do not hand-edit anything under `plugins/`
or `.claude-plugin/`: re-run the publisher and let the diff be the change.

## Install

The bundles are hosted as [Claude Code](https://docs.claude.com/en/docs/claude-code)
plugins, so that is where you install them from. Inside Claude Code:

```
/plugin marketplace add mishahanin/heading-os-marketplace
/plugin install heading-core@heading-os-marketplace
```

(Or the CLI form: `claude plugin marketplace add mishahanin/heading-os-marketplace`.)

## Bundles

| Bundle | What it carries |
| --- | --- |
| `heading-core` | Sovereignty and session core: the prime/state-check/checkpoint skills plus the standalone sovereignty guard hooks. |
| `heading-intel` | Intelligence: parse a document with citations (docparse) and build a web-sourced market brief (market-brief). Reserved (need service creds): osint, x-pulse, yt-pulse, deep-research-advance, notebooklm. |
| `heading-comms` | Communication: translate between English and Russian (translate). Reserved (need Exchange/Telegram/session or the send transport): email-intel, telegram, email-draft, email-respond, follow-up. |
| `heading-content` | Content drafting: LinkedIn posts and series, plus image prompts (linkedin-post, linkedin-series, image-prompt). Reserved: flux-image (API key), linkedin-archive (private data). |
| `heading-ops` | Ops and thinking: draft an implementation plan (create-plan), reason through a hard decision (deep-think), and run a structural editorial pass (editorial-review). Reserved (data/daemon/key-bound): dashboard, radar, queue, sync, next, recall, council. |

Bundles omit a `version`, so each marketplace commit is a new version and
installs update automatically. Skills call their bundled scripts through
`${CLAUDE_PLUGIN_ROOT}`, and a `SessionStart` hook resolves your data overlay
at runtime, so no private data is ever bundled.

## Sovereignty

Data sovereignty is a HEADING OS principle, not a property of the host. The
sovereignty-core bundle ships the guard hooks, and the engine's non-bypassable
push-time content scan and the `send_capable -> gated` invariant remain the
backstops. Outbound send stays human-gated everywhere; nothing here changes that.

## License

Apache-2.0, matching the engine. See `LICENSE`.

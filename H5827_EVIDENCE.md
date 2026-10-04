# H5827 evidence — Obsidian community listing + BRAT

_Created: 04-10-2026 (executed 04-10-2026, drain worker OxAlpha/opencode) · Handoff: [H5827](https://github.com/gasyoun/Uprava/blob/main/handoffs/H5827-OxAlpha_ruwritingstyles-obsidian_obsidian-community-listing_03.10.26.md)_

## Verdict

**BRAT-ready: PASS (21/21 checks). Community-directory submission: BLOCKED upstream** — the PR
route named in the handoff no longer exists. Since 12-05-2026 ([The future of Obsidian
plugins](https://obsidian.md/blog/future-of-plugins/)) submissions go only through the
developer dashboard at [community.obsidian.md](https://community.obsidian.md) (Obsidian-account
sign-in + linked GitHub). `obsidianmd/obsidian-releases` now mirrors
`community-plugins.json` hourly from community.obsidian.md, accepts no issues, and has zero PRs
in its listing — a submission PR there would be dead on arrival. Screenshot evidence was blocked
by two human-only toggles (see Missing evidence).

## BRAT / submission checks — 21/21 PASS

| Check | Result |
| --- | --- |
| id `ruwritingstyles` lowercase regex, no `obsidian` substring | PASS |
| name ≤ 50 (15) · author ≤ 50 (13) · description ≤ 250 (195) | PASS |
| version semver `0.1.0` · minAppVersion `1.4.0` · isDesktopOnly bool | PASS |
| authorUrl https | PASS |
| README.md / LICENSE (Apache-2.0) / manifest.json at repo root | PASS |
| versions.json `{0.1.0: 1.4.0}` consistent | PASS |
| Release tag `0.1.0` == manifest version, not draft | PASS |
| Release assets main.js + manifest.json + styles.css | PASS |
| Release manifest.json == repo manifest.json | PASS |
| id not already listed in community-plugins.json (8405 entries) | PASS |

Release: <https://github.com/gasyoun/ruwritingstyles-obsidian/releases/tag/0.1.0> · asset digests
match the repo build byte-for-byte (main.js `479c02e5…`, styles.css `895775a2…`).

## Real-vault install — performed, verified, then reverted

Installed release 0.1.0 into the live vault `SecondBrain-LLM-Wiki` (via its Local REST API:
enable in `community-plugins.json` → `app:reload`), verified, then restored the vault to its
exact prior state (enabled-list backup, plugin dir + scratch note removed, post-reload command
count back to 194). Evidence captured before revert:

- plugin commands registered in the running app: `ruwritingstyles:lint-current-note`,
  `ruwritingstyles:council-audit` (GET `/commands/` → 196 commands)
- lint command POST `ruwritingstyles:lint-current-note` → HTTP 204
- installed file digests identical to release assets

## Missing evidence (both need a human toggle, then agent can finish)

1. **Screenshot of installation** — blocked twice: Obsidian CLI is disabled in-app (Settings →
   General → Advanced toggle), and `screencapture` returns black frames (Screen Recording TCC
   permission not granted to the terminal harness). Either toggle enables a 2-minute re-run.
2. **Directory submission** — sign in at community.obsidian.md with the Obsidian account, link
   GitHub, add `gasyoun/ruwritingstyles-obsidian`. Automated review returns in minutes.

## Prepared artifacts

- Community-listing entry (appended at end per file convention, JSON-validated, 8406 entries):
  branch [`add-ruwritingstyles`](https://github.com/gasyoun/obsidian-releases/tree/add-ruwritingstyles)
  on the fork — reference only; the upstream PR route is retired.

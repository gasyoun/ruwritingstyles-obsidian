# H5827 evidence — Obsidian community listing + BRAT

_Created: 04-10-2026 · Re-verified live 11-10-2026 (drain workers OxAlpha/opencode) · Handoff: [H5827](https://github.com/gasyoun/Uprava/blob/main/handoffs/H5827-OxAlpha_ruwritingstyles-obsidian_obsidian-community-listing_03.10.26.md)_

## Verdict

**BRAT-ready: PASS (21/21 checks). Community-directory submission: BLOCKED upstream** — the PR
route named in the handoff no longer exists. Since 12-05-2026 ([The future of Obsidian
plugins](https://obsidian.md/blog/future-of-plugins/)) submissions go only through the
developer dashboard at [community.obsidian.md](https://community.obsidian.md) (Obsidian-account
sign-in + linked GitHub). Screenshot evidence remains blocked by a human-only toggle (see Missing evidence).

**Upstream retirement independently re-verified 11-10-2026 (three live probes):**

1. `obsidianmd/obsidian-releases` `community-plugins.json` is mirrored hourly by a bot
   (`chore: Mirror community plugins and themes` commits every ~2 h, latest same day).
2. The repo has **zero open and zero merged pull requests** — the PR lane is not consumed.
3. Official docs ([Submit your plugin](https://docs.obsidian.md/Plugins/Releasing/Submit+your+plugin))
   route submissions through community.obsidian.md only; no PR step exists in the current process.

Opening an upstream PR would therefore be dead-on-arrival spam against obsidianmd's documented
process; the prepared fork branch (below) is the "PR подготовлен" fail-mode artifact instead.

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

## Real-vault install — re-performed and re-verified 11-10-2026, then reverted

Release 0.1.0 re-installed into the live vault `SecondBrain-LLM-Wiki` on 11-10-2026 (release
assets via `gh release download`; asset digests re-matched the repo build byte-for-byte: main.js
`479c02e5…`, styles.css `895775a2…`), verified live, then the vault was restored to its exact
prior state (workspace.json + enabled-list restored byte-identical via `cmp`, plugin dir and
scratch note removed, Obsidian quit back to its not-running state). Live receipts from 11-10-2026:

- plugin commands registered in the running app: `ruwritingstyles:lint-current-note`,
  `ruwritingstyles:council-audit` (GET `/commands/` → 206 commands)
- lint command POST `ruwritingstyles:lint-current-note` → HTTP 204
- note opened via REST `/open/` → HTTP 200

## Missing evidence (needs a human toggle, then agent can finish)

1. **Screenshot of installation** — blocked again 11-10-2026 with a sharpened diagnosis:
   `screencapture` NOW WORKS (screen-recording TCC has been granted since the 04-10 attempt —
   verified by a live desktop capture), but the Obsidian window lives on another macOS Space:
   it is reported `onscreen=true` by the window list, yet neither full-display capture shows it
   nor does `screencapture -l <windowid>` accept cross-Space windows; fresh-workspace relaunch
   and app activation do not move it (Space switching needs Accessibility TCC, which the
   terminal harness lacks — System Events calls hang). **Toggle that unblocks a 2-minute
   finish:** grant Accessibility to the terminal harness (or open Obsidian on the harness's
   Space), then the agent re-runs install → screenshot → revert.
2. **Directory submission** — sign in at community.obsidian.md with the Obsidian account, link
   GitHub, add `gasyoun/ruwritingstyles-obsidian`. Automated review returns in minutes. This is
   the sole remaining DoD item for the original goal; it is human-only (Obsidian-account OAuth).

## Prepared artifacts

- Community-listing entry (appended at end per file convention, JSON-validated, 8406 entries):
  branch [`add-ruwritingstyles`](https://github.com/gasyoun/obsidian-releases/tree/add-ruwritingstyles)
  on the fork — reference only; the upstream PR route is retired.

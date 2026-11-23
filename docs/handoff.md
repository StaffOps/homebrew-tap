# Handoff

Last updated: 2026-11-23 · Backstage docs-standard rollout · branch `main`

## State

homebrew-tap is the Homebrew tap for StaffOps tools. It holds one cask, `kube-node-viewer`, which
GoReleaser rewrites on every kube-node-viewer release (see `homebrew_casks` in
[its .goreleaser.yaml](https://github.com/StaffOps/kube-node-viewer/blob/main/.goreleaser.yaml)). The
cask is at v0.17.0, the latest kube-node-viewer release (2026-11-18), for macOS (universal) and Linux
(arm64, x86_64). The Backstage catalog lists the repo as lifecycle `production`. There are no tags,
releases, CI workflows, open pull requests or open issues. No work is in progress.

## Done

- Cask update to kube-node-viewer v0.17.0 ([`3e266b4`](https://github.com/StaffOps/homebrew-tap/commit/3e266b4))
- Backstage `catalog-info.yaml` and technology tags ([`5cb22ae`](https://github.com/StaffOps/homebrew-tap/commit/5cb22ae), [`e7867e8`](https://github.com/StaffOps/homebrew-tap/commit/e7867e8))
- Cask updates v0.8.1 to v0.16.0, 2026-11-02 to 2026-11-11 ([`82be32d`](https://github.com/StaffOps/homebrew-tap/commit/82be32d) … [`28039f7`](https://github.com/StaffOps/homebrew-tap/commit/28039f7))

## In progress

- Nothing. Cask updates arrive automatically with each kube-node-viewer release.

## Next steps

1. Nothing planned in this repo. A new tool joins the tap by adding a `homebrew_casks` entry to its
   own GoReleaser config (suggested, inferred).
2. Expand the two-line README with install instructions (suggested, inferred).

## Decisions

No ADRs. From kube-node-viewer's GoReleaser config:

- The tap uses a cask, not a formula, and the cask removes the macOS quarantine attribute because the
  binary is not notarised.
- The cask upload is skipped when `HOMEBREW_TAP_GITHUB_TOKEN` is not set, so a tool release never
  fails for want of it.

## Risks and open questions

- If `HOMEBREW_TAP_GITHUB_TOKEN` expires, releases still succeed but the cask silently stops updating;
  compare the cask version with the latest release to notice.
- No CI audits the cask (`brew audit` / `brew style`).

## How to verify

```bash
gh release view -R StaffOps/kube-node-viewer --json tagName -q .tagName   # latest release
grep -m1 'version "' Casks/kube-node-viewer.rb                            # should match
brew install --cask staffops/tap/kube-node-viewer && kube-node-viewer -version
```

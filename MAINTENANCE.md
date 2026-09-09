# Maintenance

## Background

Maintained fork `0xble/visual-explainer` of `nicobailon/visual-explainer`;
canonical checkout `/Users/brianle/visual-explainer`, maintained branch `main`,
owned remote `origin`, source remote `upstream`. Accepted observation on
2026-09-09: `origin/main` `c93f08569bd7ec9c226c34d148993e0237991929` and freshly
fetched `upstream/main` `7163c3e10660912e0b89e1af465db9f387282b88` (64
upstream-only, 4 fork-only). Publish only to `origin`, never upstream.

## Preserve

- The responsive TOC layout remains namespaced below `.layout-toc` so it does
  not collide with unrelated page layout (`SKILL.md`, `references/responsive-nav.md`).
- Large-file writing has the documented fallback guidance in `SKILL.md`.
- Installation, activation, and runtime effects are separate from source work
  and require separate authorization and proof.

## Active patches

### VE-001 — `docs: namespace responsive TOC layout under .layout-toc`

- **Status / provenance:** Active; `1157ab82c3549923c46474f7f14d226aab3aa802`,
  merged to owned main by `b6ed0957a511a1c7fbf29207bc2fbe0c6ca0c31e` (PR #1).
- **Surfaces / invariant:** `SKILL.md`, `references/responsive-nav.md`; TOC CSS
  stays scoped to `.layout-toc`.
- **Proof:** inspect the scoped selectors and `git diff --check`.
- **Rollback / retirement:** revert the two-path patch; retire only if released
  upstream provides the same non-colliding layout and this inspection passes.
- **Upstream issue / PR:** None after checked 2026-09-09 / None after checked 2026-09-09.

### VE-002 — `docs: add large-file write fallback guidance`

- **Status / provenance:** Active; `742dbf283099bd8f4c3440464016e9161c7ebe1f`,
  merged to owned main by `c93f08569bd7ec9c226c34d148993e0237991929` (PR #2).
- **Surfaces / invariant:** `SKILL.md`; the fallback remains available where the
  normal write path cannot handle a large file.
- **Proof:** inspect the named guidance and `git diff --check`.
- **Rollback / retirement:** revert the `SKILL.md` patch; retire only if released
  upstream documents an equivalent fallback.
- **Upstream issue / PR:** None after checked 2026-09-09 / None after checked 2026-09-09.

## Update

Each run fetches `origin` and `upstream` separately, reconciles latest
`upstream/main` while preserving only active entries, runs the focused proof, and
publishes to `origin/main` or reports `Blocked` with exact refs and stage.
Immediately before `Updated` or `Already current`, fetch upstream again and require
zero upstream-only commits from `git rev-list --left-right --count
upstream/main...main`; fetch origin and require `origin/main == HEAD`. Register
changes precede publication. Current source reconciliation is Blocked by the
recorded 64 upstream-only commits; this docs-only enrollment is not a source sync.

## Verify

```text
git diff --check upstream/main...HEAD
git diff --check
# inspect SKILL.md and references/responsive-nav.md for VE-001/VE-002
# no repository test or build command exists; this is a documentation-only skill
git rev-list --left-right --count upstream/main...main
```

Sync success requires the final fresh-fetch zero count and owned-remote SHA parity;
installation or runtime activation is out of scope.

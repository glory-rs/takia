# Upstream review, 2026-11-09

Reviewed DioxusLabs/taffy `main` through
[`4aca4f49`](https://github.com/DioxusLabs/taffy/commit/4aca4f4933aa9cb7a3266050c788aad4c90288d2),
the latest upstream commit at review time. Takia's fully merged baseline remains
`c6421c1c`; only the following later commits are ported. Cherry-pick trailers
preserve the exact source and original authorship.

| Upstream commit | Decision |
| --- | --- |
| `04bb244b` / #1383 | Extract the private block dimension helper, keeping the code comparable to upstream. |
| `f6b87ac4` / #1384 | Include bottom padding and border below floats in a new block formatting context. Bring all twelve XML fixtures. |
| `fca167cf` / #1397 | Avoid counting leading collapsed-through child margins again in the parent's height. Bring all four XML fixtures. |
| `4aca4f49` / #1401 | Resolve replaced children's percentage width/max-width against zero for their min-content contribution. Bring four handwritten regressions, adapting only the crate namespace. |

All existing public function signatures, Takia package names, versions and local
fractional-flex/gap corrections are retained. No original Taffy dependency is
added to the maintained package graph.

## Deferred changes

The height-aware float/BFC chain (`60116011`, `5e035cad`, `69e82736`,
`13390fb7`, `cf62b090`, `db5255ef`, `d6f767f5`) changes public float-context
interfaces and requires coordinated consumer changes. In particular, selecting
`d6f767f5` alone made six of its twelve XML regressions fail without the earlier
height-aware slot-search changes. It is deferred as a unit rather than taking
only part of the behavioral fix. The standalone inset subtraction in `13390fb7`
already matches Takia's existing array-based subtraction order.

The upstream markdownlint workflow update (`7c27075f`) is not applicable to this
repository's maintained CI. Existing upstream fixes already present before the
baseline are not re-applied.

## Source tracking

The organization tracks the original project in the separate
[`glory-rs/taffy`](https://github.com/glory-rs/taffy) fork. Takia's implementation
is maintained separately. The official upstream remains
<https://github.com/DioxusLabs/taffy>. Maintainers fetch it read-only, review the
diff and port selected commits on a maintained branch. There is no scheduled
write to this repository's historical `upstream-main` snapshot.

## Verification

Run `cargo metadata --no-deps --format-version 1` in this workspace to discover
the actual target directory. Validate with `cargo test --locked --all-features`,
`cargo check --locked --no-default-features --lib`, and
`cargo fmt --all -- --check`. The existing fractional-flex/gap tests remain part
of the complete suite. Build and release tooling honors the caller's normal
Cargo and temporary-directory configuration.

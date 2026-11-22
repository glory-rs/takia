# Upstream review, 2026-11-22

Reviewed the 10 commits added to [`DioxusLabs/taffy:main`](https://github.com/DioxusLabs/taffy/compare/4aca4f4933aa9cb7a3266050c788aad4c90288d2...1abd8eeaf6059336a7026c31e0f1b769d2f04a3a) since the previous original-name fork tip, `4aca4f493`, through `1abd8eeaf`.

Takia retains its released package identity and its existing cache trait and serialization interfaces.

| Commit | Upstream change | Decision for Takia |
| --- | --- | --- |
| [`5f3f035e0`](https://github.com/DioxusLabs/taffy/commit/5f3f035e0a461db4f321af8e2ecf47abd2b709a0) | Fix stray bracket in TaffyTree docs (#1406) | Port the stray bracket correction to TakiaTree. |
| [`d0345bac6`](https://github.com/DioxusLabs/taffy/commit/d0345bac609a10b25278ecc0850e862be9504e74) | Speed up node context lookups with FxHash (#1402) | Port FxHash for std node contexts and its Criterion benchmark. The no_std tree keeps its dense map. Grid already uses div_ceil. |
| [`1e38b30cc`](https://github.com/DioxusLabs/taffy/commit/1e38b30cce5adad1bda5e6ffdf463066b27f25ba) | Make Cache::get take &self by storing the cache clock in an AtomicU16 (#1409) | Defer the public CacheTree receiver change. Existing implementations including Apace implement cache_get(&mut self). Coordinate a trait migration with consumers. |
| [`ccc07ed86`](https://github.com/DioxusLabs/taffy/commit/ccc07ed86000b1014d9e4bac5552d886d48dc019) | Remove Serialize derives from Cache (#1410) | Keep Cache's feature-gated Serialize implementation for existing users. Removing it would break the serde contract independently of the clock representation. |
| [`31b22b7f0`](https://github.com/DioxusLabs/taffy/commit/31b22b7f08783885d6cde5754bf89fa021dbda57) | Fix clippy::nonminimal_bool lint (Rust 1.100) (#1412) | Already present in grid placement. |
| [`a5c2557db`](https://github.com/DioxusLabs/taffy/commit/a5c2557db41f406784be3a4538854c5fbe3a88ae) | Bump MSRV to 1.85 (#1411) | Keep the published Rust 1.95 floor. The lint simplifications are present. Use core::iter::repeat_n in the flex line balancer so the calls are available with std disabled. |
| [`470b5516f`](https://github.com/DioxusLabs/taffy/commit/470b5516fbcdc6f9c02895e23bb2618b801cf9d0) | Bump benchmark dependencies (#1415) | Keep comparison baselines for Yoga, Torin and Parley. Criterion 0.8 and rand/rand_chacha 0.10 with the updated helper imports are already in the independent benchmark workspace. |
| [`87b05ee6e`](https://github.com/DioxusLabs/taffy/commit/87b05ee6e46484546556d40972aa0accf9d39550) | Remove std code vendored for pre-1.85 MSRVs (#1413) | Port core float operations, bit casts and pointer APIs. Keep strict_provenance as a compatible feature name. |
| [`a3997d55b`](https://github.com/DioxusLabs/taffy/commit/a3997d55bacd1fb6cd12fe31db0be15b20f91528) | Upgrade cssparser to 0.38 (#1414) | The crate already uses cssparser 0.38 and its parser API. Preserve the maintained parsers. |
| [`1abd8eeaf`](https://github.com/DioxusLabs/taffy/commit/1abd8eeaf6059336a7026c31e0f1b769d2f04a3a) | Remove redundant borrow in ParseError Display impl (#1416) | Port the ParseError display cleanup. |

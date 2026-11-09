# Upstream provenance

Upstream: https://github.com/DioxusLabs/taffy

Maintenance repository: https://github.com/glory-rs/takia

The initial renamed release retains upstream version 0.15.0 and all previous Glory maintenance fixes. Original licensing and copyright notices remain in the repository. Names in preserved upstream changelogs describe the historical upstream releases.

Upstream changes are reviewed and ported explicitly. This repository does not automatically
update `upstream-main` or reset/auto-merge maintained `main`. Original-name upstream forks
are maintained separately from the renamed implementation.

Merged upstream main through `c6421c1c` (2026-10-30), preserving the Takia namespace and fractional flex gap fix.

Selected compatible fixes after that baseline are recorded in
[docs/upstream-integration.md](docs/upstream-integration.md). This does not imply that
every subsequent upstream commit has been integrated.

# Upstream mirror authentication

The scheduled workflow copies DioxusLabs/taffy's main commit unchanged to
`upstream-main`. Upstream commits can change workflow files, which GitHub
rejects when pushed using the built-in Actions token.

Configure a dedicated SSH deploy key for this repository with write access,
and store its private key in the Actions secret `UPSTREAM_SYNC_SSH_KEY`.
Use a different key for each repository. The workflow uses that key through
`actions/checkout`; the built-in token only needs read access. Missing
credentials fail with an explicit diagnostic.

The sync updates only `upstream-main`, using `--force-with-lease` against its
observed head. It does not merge upstream into `main`, push tags, or publish
packages. Deploy-key pushes can trigger workflows on the mirrored branch;
review upstream workflow triggers when maintaining this mirror.

To rotate credentials, register a new write deploy key, replace the secret,
run **Sync upstream mirror** manually, and remove the old deploy key after
success. Verify `upstream-main` equals the upstream main commit. The workflow
can be dispatched on a proposed fix branch before merging it.

Build and release jobs use the caller's normal Cargo and temporary directory
configuration. Release artifact paths come from `cargo metadata` for the
workspace being released; independent workspaces may use different targets.

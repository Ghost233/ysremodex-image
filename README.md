# ysremodex-image

Builds release artifacts from `Ghost233/remodex`.

## GitHub Actions setup

Create this repository secret:

- `REMODEX_SOURCE_PAT`: PAT with read access to `Ghost233/remodex`

## Relay image

The workflow sparse-checks out `relay/` from `Ghost233/remodex`, builds
`relay/Dockerfile`, and pushes:

- `ghcr.io/ghost233/ysremodex-relay:latest`
- `ghcr.io/ghost233/ysremodex-relay:source-<source-sha>`

Manual runs can override:

- `source_ref`: defaults to `ghost`

Every run publishes only release tags:

- `latest`
- `source-<source-sha>`

## Remodex Tarui release

The `Build Remodex Tarui Release` workflow sparse-checks out
`remodex-tarui/`, builds an unsigned macOS universal Tauri bundle, and creates
a GitHub Release with:

- `remodex-tarui-<version>+<build>-macos-universal.app.zip`
- `remodex-tarui-<version>+<build>-macos-universal.dmg`

Manual runs can override:

- `source_ref`: defaults to `ghost`
- `build_number`: defaults to the workflow run number

Release existence is checked with the combined `version+build` key. The release
tag is `remodex-tarui-v<version>+<build>`.

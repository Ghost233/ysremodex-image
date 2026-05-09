# ysremodex-image

Builds the Remodex relay Docker image from `Ghost233/remodex`.

## GitHub Actions setup

Create this repository secret:

- `REMODEX_SOURCE_PAT`: PAT with read access to `Ghost233/remodex`

The workflow sparse-checks out `relay/` from `Ghost233/remodex`, builds
`relay/Dockerfile`, and pushes:

- `ghcr.io/ghost233/ysremodex-relay:latest`
- `ghcr.io/ghost233/ysremodex-relay:source-<source-sha>`

Manual runs can override:

- `source_ref`: defaults to `ghost`
- `image_tag`: defaults to `latest`

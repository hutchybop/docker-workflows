# docker-workflows

This repo contains shared GitHub Actions workflows used by other repos.

Important:
- keep the hidden `.github/workflows/` directory in this repo
- do not delete this repo directory, other repos depend on it

## Available workflow

- `.github/workflows/docker-release-reusable.yml`

## Usage

```yaml
jobs:
  release:
    uses: hutchybop/docker-workflows/.github/workflows/docker-release-reusable.yml@main
    with:
      image_name: ${{ github.repository }}
      dockerfile: ./Dockerfile
      context: .
      platforms: linux/amd64
```

## Behavior

- only runs for tag refs
- enforces semver tag format `vX.Y.Z`
- verifies tagged commit is contained in `main`
- publishes `vX.Y.Z`, `sha-*`, and `latest` tags to GHCR

# Contributing to the OpenPeon Registry

## Adding a pack

### 1. Create your pack repo

In your own GitHub account, create a repo with:

```
openpeon-mypack/
  openpeon.json       # CESP v1.0 manifest
  sounds/
    sound1.mp3
    sound2.wav
    ...
  README.md           # Optional
  LICENSE             # Recommended
```

See [openpeon.com/create](https://openpeon.com/create) for the full manifest format.

### 2. Tag a release

```bash
git tag v1.0.0
git push origin v1.0.0
```

### 3. Compute the manifest hash

```bash
sha256sum openpeon.json
# or on macOS:
shasum -a 256 openpeon.json
```

### 4. Create your registry entry

Fork this repo, then:

```bash
mkdir -p packs/my-pack
```

Create `packs/my-pack/registry.json` with your pack metadata. Set `manifest_sha256` to the hash you computed. Set `trust_tier` to `"community"`.

### 5. Open a PR

That's it. We'll review and merge. Once merged, `index.json` is auto-regenerated and your pack becomes available for installation.

## Updating a pack

1. Push a new version to your repo
2. Tag it (e.g., `v1.1.0`)
3. Open a PR updating your `registry.json` with the new version, ref, and manifest hash

## Rules

- Pack names must be unique (lowercase, hyphens, underscores)
- Audio files: WAV, MP3, or OGG only
- Max 1 MB per audio file, 50 MB total per pack
- No offensive content
- Source repo must be publicly accessible

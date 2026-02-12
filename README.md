# OpenPeon Registry

The central index of [CESP](https://openpeon.com/spec) sound packs. Metadata only — no audio files stored here.

Browse packs at [openpeon.com/packs](https://openpeon.com/packs).

## How it works

Each pack has a `registry.json` entry in `packs/<name>/` that points to the pack's source repository. An auto-generated `index.json` at the repo root lists all registered packs.

**Index URL:** `https://PeonPing.github.io/registry/index.json`

## Submit a pack

1. Create a GitHub repo with your pack (e.g., `yourname/openpeon-mypack`)
2. Include `openpeon.json` manifest + `sounds/` directory
3. Tag a release: `git tag v1.0.0 && git push origin v1.0.0`
4. Fork this repo and create `packs/<your-pack>/registry.json`
5. Open a PR

See the full guide at [openpeon.com/create](https://openpeon.com/create).

## Registry entry format

```json
{
  "name": "my-pack",
  "display_name": "My Sound Pack",
  "version": "1.0.0",
  "description": "Short description of your pack",
  "author": { "name": "yourname", "github": "yourname" },
  "source": {
    "type": "github",
    "repo": "yourname/openpeon-mypack",
    "ref": "v1.0.0"
  },
  "manifest_sha256": "<sha256 of openpeon.json>",
  "trust_tier": "community",
  "categories": ["session.start", "task.complete"],
  "language": "en",
  "license": "MIT",
  "total_size_bytes": 500000,
  "sound_count": 10,
  "tags": ["gaming"],
  "added": "2026-02-12",
  "updated": "2026-02-12"
}
```

See the [full schema](schema/registry-v1.schema.json) for validation.

## Trust tiers

| Tier | Criteria |
|---|---|
| `official` | Maintained by the PeonPing org |
| `verified` | Established GitHub account (1+ year, 50+ followers or 10+ repos) |
| `community` | Any GitHub account older than 30 days |

## License

MIT

# Lampy — ecosystem and deployment notes

**Lampy** is a self-hosted forum and service stack comprising PostgreSQL 16,
TimescaleDB, pgvector, Apache, Ollama (local LLM), Apache James (mail),
code-server, and a Flask forum app.

## Repositories

| Repo | What it is |
|---|---|
| [lampy-single](https://github.com/kitcosby/lampy-single) | The stack itself: Dockerfile, build scripts, forum app |
| [lampy-installer](https://github.com/kitcosby/lampy-installer) | Windows installer (WSL2-based, downloads the system image) |
| [lampy-deps](https://github.com/kitcosby/lampy-deps) | Build dependencies: Python wheelhouse + Ollama mirror |

The [repository inventory](docs/repository-inventory.md) maps all 18
repositories owned by `kitcosby`, identifies canonical sources and mirrors,
and records the current consolidation recommendations.

## Assembling the pieces

Large files are split into parts on GitHub Releases (2 GB per-file
limit). Download **all** parts for the archive you need, then
concatenate them **in order** before extracting.

### Build dependencies ([lampy-deps](https://github.com/kitcosby/lampy-deps), release `build-deps-v1`)

**Python wheelhouse** (3.3 GB, 3 parts):

```bash
cat wheelhouse.tar.part00 wheelhouse.tar.part01 wheelhouse.tar.part02 > wheelhouse.tar
tar -xf wheelhouse.tar        # produces wheelhouse/
mv wheelhouse wheelhouse      # place beside the Dockerfile
```

**Ollama distribution mirror** (5 GB, 4 parts — `/usr/bin/ollama` and
`/usr/lib/ollama` from the pinned `ollama/ollama:latest` image):

```bash
cat ollama-donor.tar.part00 ollama-donor.tar.part01 \
    ollama-donor.tar.part02 ollama-donor.tar.part03 > ollama-donor.tar
tar -xf ollama-donor.tar      # produces ollama-donor/
```

### System image ([lampy-installer](https://github.com/kitcosby/lampy-installer), release `v1.0.0`)

**Lampy system image** (11 GB, 7 parts). The Windows installer
(`install.ps1`) downloads and verifies these automatically against
`lampy-public.tar.sha256`. To assemble manually:

```powershell
# Download all 7 parts + the .sha256 file from the release, then:
Get-Content lampy-public.tar.part-* -Raw -AsByteStream |
    Set-Content lampy-public.tar -AsByteStream
# Verify:
Get-FileHash lampy-public.tar.part-* -Algorithm SHA256
# (compare against lampy-public.tar.sha256)
```

## License notes

- [Terms of Use](https://www.facebook.com/permalink.php?story_fbid=pfbid0EYdC7t3nnkshMjssisYwyix5p8JLyD3Ns7EvEkRP4ugNtB8z8dKcrBwdJKSqLKaPl&id=61594635330402)
- This account's original code is public domain ([The Unlicense](https://unlicense.org)).
- The stack bundles third-party components under their own licenses;
  see `COMPONENT_LICENSES.md` in lampy-single.
- **TimescaleDB**: the Timescale License permits free self-hosted use
  at any scale, but you may not offer TimescaleDB itself as a hosted
  database service. See `FEES.md` in lampy-single for the commercial
  breakdown (spoiler: license fees are $0 across the stack).

## System architecture

Text-based SAD documentation (Mermaid) for the ecosystem:

- [System-wide context diagram and database documentation](docs/system.md) —
  architecture-level subsystems, external entities, data flows, data stores,
  and cross-system entity relationships.
- [Complete repository inventory and consolidation map](docs/repository-inventory.md) —
  all repositories returned by the `kitcosby` account listing on
  2026-11-04, with canonical-source and archival recommendations.
- Per-repo architecture documents, where present:
  - [Bible](https://github.com/kitcosby/Bible/blob/main/docs/architecture.md)
  - [R-Theory](https://github.com/kitcosby/R-Theory/blob/main/docs/architecture.md)
  - [bible-project](https://github.com/kitcosby/bible-project/blob/master/docs/architecture.md)
  - [euclid-proofs](https://github.com/kitcosby/euclid-proofs/blob/main/docs/architecture.md)
  - [genealogy](https://github.com/kitcosby/genealogy/blob/main/docs/architecture.md)
  - [gwen-training](https://github.com/kitcosby/gwen-training/blob/main/docs/architecture.md)
  - [lampy-admin](https://github.com/kitcosby/lampy-admin/blob/main/docs/architecture.md)
  - [lampy-deps](https://github.com/kitcosby/lampy-deps/blob/main/docs/architecture.md)
  - [lampy-installer](https://github.com/kitcosby/lampy-installer/blob/main/docs/architecture.md)
  - [lampy-single](https://github.com/kitcosby/lampy-single/blob/main/docs/architecture.md)
  - [lampy-temp-backup](https://github.com/kitcosby/lampy-temp-backup/blob/main/docs/architecture.md)
  - [r-theory-rewrite](https://github.com/kitcosby/r-theory-rewrite/blob/main/docs/architecture.md)

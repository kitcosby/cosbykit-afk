# GitHub repository inventory

**Owner:** [`kitcosby`](https://github.com/kitcosby)  
**Checked:** 2026-11-04  
**Scope:** All 18 repositories returned by the account's repository listing on the date above.

This is an ownership and purpose map, not a claim that every repository is equally active or maintained. Canonical-source and archival decisions are called out explicitly. No repository is deleted, renamed, archived, or merged by this document.

## R Theory and mathematical research

| Repository | Role | Current recommendation |
|---|---|---|
| [r-theory-rewrite](https://github.com/kitcosby/r-theory-rewrite) | Canonical R Theory rewrite, website, page-level validation scripts, database snapshot, and Works Cited register | **Canonical source** for the rewrite and its website |
| [R-Theory](https://github.com/kitcosby/R-Theory) | Selected backup mirror of supporting rewrite materials | Retain as a mirror; do not develop competing canonical content here |
| [euclid-proofs](https://github.com/kitcosby/euclid-proofs) | Claim-by-claim Euclid/extension-proof archive, ledgers, source extracts, and cumulative trigonometric proof | Retain as a distinct audit corpus; its records are not duplicates of the rewrite's page-level scripts |
| [geometry-first](https://github.com/kitcosby/geometry-first) | Separate geometry-first unification corpus with its own proof standard | Retain separately; do not merge into the E8/R Theory rewrite without an explicit research decision |
| [rtheory-](https://github.com/kitcosby/rtheory-) | Projection Craft modular Book-16 frontier harness | Active, distinct computational project; not an archive mirror and not a replacement for the canonical rewrite |

## Bible and translation

| Repository | Role | Current recommendation |
|---|---|---|
| [bible-project](https://github.com/kitcosby/bible-project) | Current Bible corpus, database/build tooling, website source, and research | **Canonical current project** |
| [Bible](https://github.com/kitcosby/Bible) | Earlier partial copy of the Bible corpus/build work | Historical copy; candidate for archival after unique files and history are checked |
| [BibleApp](https://github.com/kitcosby/BibleApp) | Private workspace monorepo containing a React/Vite translation app, API server, generated API client, and mockup sandbox | Retain as the richer workspace/application source; no path-level overlap with the static PWA was found |
| [BibleApp-pwa](https://github.com/kitcosby/BibleApp-pwa) | Public nine-file static PWA: standalone `index.html`, manifest, icons, and offline service worker; reads the Lampy Bible API | Retain as a distinct static/offline delivery target; do not merge into the workspace monorepo without a migration plan |

## Lampy and operations

| Repository | Role | Current recommendation |
|---|---|---|
| [lampy-admin](https://github.com/kitcosby/lampy-admin) | Lampy administration application and Windows dashboard | Retain |
| [lampy-installer](https://github.com/kitcosby/lampy-installer) | Windows/WSL installation and deployment tooling | Retain |
| [lampy-single](https://github.com/kitcosby/lampy-single) | Docker-based single-container stack | Retain as a distinct deployment target |
| [lampy-deps](https://github.com/kitcosby/lampy-deps) | Build dependency and large release assets | Retain; release assets are part of its purpose |
| [lampy-temp-backup](https://github.com/kitcosby/lampy-temp-backup) | 108-file historical Lampy/forum-stack snapshot with control-plane, DB-console, payments, and other legacy modules | Retain intact; contains substantial material not represented by current component repositories, so it is not yet safe to archive |
| [gwen-training](https://github.com/kitcosby/gwen-training) | Gwen training materials and curriculum | Retain separately from runtime infrastructure |

## Other projects and account tooling

| Repository | Role | Current recommendation |
|---|---|---|
| [qa-ceg](https://github.com/kitcosby/qa-ceg) | Requirements/coverage model and QA issue workflow | Retain as shared QA infrastructure |
| [genealogy](https://github.com/kitcosby/genealogy) | Verified genealogy research and public-safe GEDCOM | Retain separately; preserve its public/private data boundary |
| [cosbykit-afk](https://github.com/kitcosby/cosbykit-afk) | Lampy ecosystem documentation and system-wide architecture notes | Retain as architecture documentation; it is not the GitHub profile README |

## Consolidation principles

1. One canonical source per actively developed product or research corpus.
2. Mirrors and snapshots must identify their source, synchronization state, and purpose.
3. Preserve Git history and unique research artifacts; archive only after a path-by-path comparison.
4. Keep distinct proof standards, mathematical corpora, deployment targets, and privacy boundaries separate.
5. Put reproducible GPT/Lampy verification records beside the existing validation system only when the record's scope fits. Do not create another repository merely to hold a second copy of existing scripts or ledgers.
6. Review branches and deployment dependencies before pruning branches or changing repository names.

## Suggested cleanup sequence

1. Reconcile the R Theory README links and document the boundary between `r-theory-rewrite/validation` and `euclid-proofs`.
2. Compare unique paths and Git history in `Bible` against `bible-project`; only then decide whether to archive the former.
3. Compare `lampy-temp-backup` against current Lampy repositories and confirm restore value before archival.
4. Inspect `BibleApp` and `BibleApp-pwa` source/deployment relationships before deciding whether they should be combined.
5. Refresh this inventory and the system architecture diagrams after each approved change.

## Snapshot limitations

This inventory is based on repository metadata, recursive file-tree listings, selected READMEs, targeted Git blob comparisons, and branch/commit checks for the repositories specifically reviewed on 2026-11-04. The BibleApp comparison is structural; no live deployment or API integration test was run. This is not a full account-wide branch ancestry audit, dependency audit, or deployment verification.

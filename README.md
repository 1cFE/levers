# Fusion Archetype LCOE Lever Stacks

Interactive reference for the favorable assumptions behind six fusion archetypes. The July 2026 content is preserved from source commit `bc7aca204284019b055d6581169c5c1f7cfe60d2`. It identifies conditions that could improve LCOE, not a forecast that they will all be achieved.

- Live tool: https://levers.1cf.energy/
- Source: https://github.com/1cFE/levers
- Local instructions: [run-locally.html](run-locally.html)

## Run locally

Download a release bundle, verify its checksum, and extract it. Serve that directory with Python 3:

```sh
python3 -m http.server 8000 --bind 127.0.0.1
```

Open http://127.0.0.1:8000/. All application code and content are in `index.html`. There is no backend, build step, package installation or external runtime request. Fonts use the reader's installed fonts. Choose an archetype with a click or the arrow keys. Reloading returns to the Universal stack.

## Reproduce a release

Each generated bundle contains `release.json`, which records the exact source commit, and `SHA256SUMS`, which lists the payload hashes. Its ZIP has a separate `.sha256` file. Verify the ZIP before extracting with `shasum -a 256 -c <archive>.sha256`, then verify the files from the extracted directory with `shasum -a 256 -c SHA256SUMS`.

From a source checkout, use the full commit recorded in `release.json`:

```sh
git checkout <source_commit>
python3 package_release.py --ref <source_commit> --output-dir /tmp/levers-release
```

The script reads committed Git files, not uncommitted working files. It generates a deterministic ready-to-serve ZIP and checksums without network access. Source links in `release.json` remain pinned even if the default branch moves. Creating a bundle does not publish it or change the live site.

Before attaching a bundle to a tagged release, check all seven tabs, keyboard navigation and the local instructions with external network access disabled. Record the tested commit in the release description. No release tag is created by these scripts.

## Rights

Original software is licensed under MIT. Original written content is licensed under CC BY 4.0. See [LICENSING.md](LICENSING.md) for the scope and attribution guidance. The full license texts are included in each release. There are no bundled third-party libraries or fonts.

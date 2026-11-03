# Resource Scanner 5.0.11

Adds an item catalog linked to the in-game map in Enshrouded. Select a resource to see its gathering sources.

## Download

Download **Resource_Scanner_5.0.11.zip** from [Releases](https://github.com/Anlidan00/ResourceScanner/releases). Extract it and run the installer with Enshrouded closed.

The installer supports updating versions **5.0.8 and newer** while preserving selected items and interface visibility. The visibility key can be selected in the installer; Insert is the default.

## Changes

- Updated compatibility with Enshrouded 1285601.
- Improved resilience to future updates by removing unnecessary dependencies on the game's internal code.
- Improved detection of map, language, character and learned-item structures.
- Failures in individual optional features have less impact on the others.
- Fixed waypoint handling when closing the map and changing the game context.
- Strengthened checks that map data and the selected save are current.

## Source and review

See [BUILD.md](BUILD.md) for build instructions and [SECURITY_REVIEW.md](SECURITY_REVIEW.md) for installer, proxy/hook and helper behavior. The source archive includes the native core, retained loader, Python helper and C# installer with 15-language translations.

- 97 source/font files are bound by SHA-256.
- All 33 packaged files and the embedded translations match the reviewed inputs.
- Native core and loader rebuilds: results are recorded in [review_build.json](review_build.json).
- The installer can be rebuilt from its included C# source using the validated published payload.
- Artifact hashes: [artifact_hashes.json](artifact_hashes.json).

Offline checks passed. The author reported testing version 5.0.11 in-game on 2026-11-03; see [GAME_TEST_REPORT.json](GAME_TEST_REPORT.json). The agent did not launch the game. Full binary reproducibility is not claimed.

Game artwork, portraits, packed catalog assets and executable binaries are outside this source archive. Upstream source downloads are a development build step; the mod and installer do not download dependencies at runtime.

[Third-party licenses](Third_Party_Licenses.txt). Development used OpenAI Codex for code and translations.

Complete source archive: [ResourceScanner_Source_5.0.11_review.zip](ResourceScanner_Source_5.0.11_review.zip). SHA-256: `3676ae76174057300ae5e296784331238c2f8768c1c2f1d0347e3d43a960425a`.

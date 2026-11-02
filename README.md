# Resource Scanner 5.0.9

Adds an item catalog linked to the in-game map in Enshrouded. Select a resource to see its gathering sources.

## Download

The installable mod package is **Resource_Scanner_5.0.9.zip** under the [Releases](https://github.com/Anlidan00/ResourceScanner/releases) section. Extract it and run the installer with Enshrouded closed.

The installer can update versions **5.0.8 and newer** without uninstalling them first. Selected items and interface visibility are preserved. You can also choose the key that hides and shows the Scanner; Insert is the default.

Version 5.0.9 adapts the map, discovery progress, zoom and waypoints for Enshrouded 1283531. Offline checks passed. The author has tested version 5.0.9 in-game.

## Source and review

See [BUILD.md](BUILD.md) for build instructions and [SECURITY_REVIEW.md](SECURITY_REVIEW.md) for installation, proxy/hook and helper behavior. The source tree includes the native core, retained loader, Python helper and original C# installer with 15-language translations.

- 94 source/font files are bound by SHA-256.
- All 33 payload files are verified against the installer.
- The native core and retained loader rebuild successfully; their `.text` sections match the packaged DLLs. Full binary reproducibility is not claimed.
- The installer rebuilds from the included C# code using its validated embedded payload.
- Checks and hashes: [review_build.json](review_build.json), [artifact_hashes.json](artifact_hashes.json).

Game artwork, portraits, packed catalog assets and executable binaries are not included in this source tree. Upstream source downloads are a development build step; the mod and installer do not download dependencies at runtime.

[Third-party licenses](Third_Party_Licenses.txt). Development used OpenAI Codex for code and translations.

Complete source archive: [ResourceScanner_Source_5.0.9_review.zip](ResourceScanner_Source_5.0.9_review.zip). SHA-256: `4364409ef58bf85b095ecdddc7f5a1875707c610fe6598e419b180adf64e8a00`.

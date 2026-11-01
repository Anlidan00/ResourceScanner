# Resource Scanner 5.0.8 — source review

Source code and build information for the Enshrouded mod:

https://www.nexusmods.com/enshrouded/mods/285

## Complete source package

Download [ResourceScanner_Source_5.0.8_review.zip](ResourceScanner_Source_5.0.8_review.zip) and extract it before following [BUILD.md](BUILD.md). The archive contains the complete source-review tree: native core, frozen published loader, Python helper, original C# installer, translations, pinned dependency retrieval, source/payload hashes and build scripts. It contains no executable binaries or game artwork.

The ZIP preserves the project paths used by the build scripts. Source archive SHA-256:

```text
55abd85aa983fde61385984359f24570e20a3d2d9d581f4822d0ca0d9545da96
```

## Verification

- 114 included original source/font files are bound by SHA-256.
- All 33 installed payload files were checked against the published installer.
- The installer was rebuilt from the included C# source against the validated original embedded payload.
- The core and retained Vulkan loader built successfully with MSVC x64 Release. Their `.text` sections match the corresponding published DLLs. Complete PE hashes can differ; a bit-for-bit reproducible build is not claimed.
- See [review_build.json](review_build.json), [artifact_hashes.json](artifact_hashes.json) and [SECURITY_REVIEW.md](SECURITY_REVIEW.md).

## Notices

Third-party software, fonts and method-icon notices are retained in [Third_Party_Licenses.txt](Third_Party_Licenses.txt) and inside the source archive. Game artwork, creature portraits and packed world-catalog assets are not hosted here. The installer review script reads the validated payload from the existing published installer without executing it.

The development process used OpenAI Codex for code and translations.

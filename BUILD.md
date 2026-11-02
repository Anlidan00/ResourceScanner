# Building and reviewing version 5.0.9

## Requirements

- Windows x64.
- Visual Studio 2022 / Build Tools with the x64 C++ toolchain, Windows SDK, CMake and Ninja.
- Python 3.10 or newer for the review scripts. The mod's packaged helper uses CPython 3.14; its interpreter binaries are upstream distribution files, not compiled from project source.
- An installed x64 Vulkan loader in the Windows system directory for the native core's configure step. Export names and ordinals are read from it; system DLL code is not copied.
- .NET Framework 4.x C# compiler at `%WINDIR%/Microsoft.NET/Framework64/v4.0.30319/csc.exe` for the installer review build.

## Verify source

From the repository root:

```powershell
python -B scripts/verify_sources.py
```

`release/source_hashes.json` binds the included original source and font bytes. The native source hashes were checked against the recorded 5.0.9 build. The retained loader uses its original source snapshot; its difference from the later working copy is a leading comment and line endings, not behavior.

## Build the native core and retained loader

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/build_native.ps1
```

This downloads only the pinned official upstream source archives, checks their SHA-256 hashes, and builds:

- `build/native/ResourceScannerCore.dll`
- `build/loader/vulkan-1.dll`

The dependency download is a development step. The mod and installer do not download dependencies at runtime.

The original core CMake project is retained under `native/`. `BUILD_TESTING=OFF` is used for this portable review build because some historical integration fixtures use private development captures that are not part of the source publication. Building does not launch Enshrouded. The frozen loader forwarders are provided directly under `loader/`; they contain generated assembly, public export names and ordinals, not Windows DLL code.

## Rebuild the installer against the published payload

Obtain `Resource_Scanner_Setup_5.0.9.exe` from the uploaded `Resource_Scanner_5.0.9.zip`. A Nexus reviewer can use the file already held in quarantine. Place the EXE outside the repository, then run:

```powershell
python -B scripts/build_installer_for_review.py "C:/review-input/Resource_Scanner_Setup_5.0.9.exe"
```

The script verifies the original EXE hash, reads its managed PE resources without loading or running it, checks every packaged file against `release/payload_manifest.json`, and recompiles `InstallCore.cs` and `SetupUi.cs` with the original package and translations as embedded resources. Output: `build/installer/ResourceScannerSetup.review.exe`.

This rebuild reviews the source that is actually responsible for installation and uninstallation while preserving the uploaded payload. The script does not replace the payload's native DLLs with newly rebuilt ones. Those DLLs can be reviewed separately using the preceding native build. Use the portable review script in this repository to rebuild the installer with the published payload. Packed map/catalog assets remain in the published installer, outside this source archive.

## Binary identity

Published file hashes and sizes are in `release/artifact_hashes.json`. Source and payload identity checks are exact. Newly compiled binaries may differ from the published bytes due to compiler/SDK versions, embedded build paths and PE timestamps; this repository does not claim a bit-for-bit reproducible build.

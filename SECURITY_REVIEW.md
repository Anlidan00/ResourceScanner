# Behavior relevant to security review

## Installer

The published EXE is a Windows Forms C# installer containing the mod payload and 15-language installer strings as managed resources. `installer/InstallCore.cs` implements package verification, target-path checks, installation, ownership records, rollback and uninstallation. `installer/SetupUi.cs` implements the interface. It operates on the selected Enshrouded installation directory. It has no automatic updater, telemetry or dependency downloader.

## Native integration

The game-directory `vulkan-1.dll` is the project's proxy loader. It forwards the Vulkan export interface to the real Windows system Vulkan DLL and starts `ResourceScanner/ResourceScannerCore.dll`. The core draws the Scanner interface inside the game using Vulkan/Win32 and MinHook hooks. Native source performs bounded game-state reads and contains the optional map zoom and waypoint integration. These hooks and memory operations are functional parts of the mod, not antivirus exclusions or scanning bypasses.

## Python helper

The helper is started by the native core for the current game instance. It reads game/save state to determine item discovery and explored-map visibility, then publishes bounded shared state for the UI. Save-state readers and process-memory access are included under `runtime/`. The packaged CPython and python-zstandard binaries are upstream runtime dependencies; their payload hashes are listed in `release/payload_manifest.json`.

## Published artifact mapping

The 5.0.8 payload contains the current 5.0.8 core and an earlier retained, tested proxy binary. The exact retained proxy source and generated forwarders are included under `loader/`. Its source SHA-256 was restored and verified against the original build record. Both original artifact hashes are listed in `release/artifact_hashes.json`.

This document describes intended operations for examination. It does not assert a VirusTotal verdict or replace a Nexus security review.

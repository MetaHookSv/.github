# MetaHookSv

**A client-side modding framework, plugin collection and toolchain for GoldSrc / Sven Co-op.**

[![Platform](https://img.shields.io/badge/platform-Windows%20x86-0078D6?logo=windows&logoColor=white)](#)
[![Latest release](https://img.shields.io/github/v/release/MetaHookSv/MetaHookSv?label=latest%20release)](https://github.com/MetaHookSv/MetaHookSv/releases)
[![Stars](https://img.shields.io/github/stars/MetaHookSv/MetaHookSv?style=flat&logo=github)](https://github.com/MetaHookSv/MetaHookSv/stargazers)

MetaHookSv is a port of [MetaHook](https://github.com/nagist/metahook) to **SvEngine**, the
GoldSrc engine modified by the Sven Co-op team. It launches the game with a plugin host
compiled in and exposes a stable C++ API, so client-side plugins can hook the engine
without modifying the game's own files.

Most plugins still work on vanilla GoldSrc — check each plugin's own documentation for
engine compatibility.

## Core

| Repository | Role |
| --- | --- |
| [MetaHookSv](https://github.com/MetaHookSv/MetaHookSv) | Aggregator: one CMake tree for every component, shared `thirdparty/`, CI and releases |
| [MetaHook](https://github.com/MetaHookSv/MetaHook) | Game launcher: engine startup, symbol resolution, hook infrastructure and the public plugin API |
| [MetahookInstaller](https://github.com/MetaHookSv/MetahookInstaller) | GUI installer and plugin list editor, plus a CLI, built on .NET 8 with Avalonia |

## Plugins

### Rendering & interface

- **[Renderer](https://github.com/MetaHookSv/Renderer)** — a graphics enhancement plugin that completely overhauls the legacy GoldSrc renderer with OpenGL 4.4.
- **[VGUI2Extension](https://github.com/MetaHookSv/VGUI2Extension)** — a VGUI2 modding framework other plugins use to hook and patch VGUI2 components; adds multi-byte text, HiDPI and input-method support.
- **[CaptionMod](https://github.com/MetaHookSv/CaptionMod)** — closed captions, HUD text translation and a Source-2007-style chat dialog.
- **[SteamScreenshots](https://github.com/MetaHookSv/SteamScreenshots)** — takes over the `snapshot` command and sends the captured image to the Steam Screenshot Manager.

### Gameplay & physics

- **[BulletPhysics](https://github.com/MetaHookSv/BulletPhysics)** — client physics: ragdolls, jiggle bones, collision with moving brushes, buoyancy and barnacle/gargantua interactions.
- **[SCCameraFix](https://github.com/MetaHookSv/SCCameraFix)** — fixes spectator/chase camera glitches (Sven Co-op only).
- **[StudioEvents](https://github.com/MetaHookSv/StudioEvents)** — filters studio-event sounds to stop repeated or overlapping playback.
- **[SCModelDownloader](https://github.com/MetaHookSv/SCModelDownloader)** — downloads missing player models from the scmodel database and reloads them once ready (Sven Co-op only).

### Quality of life

- **[BetterSpray](https://github.com/MetaHookSv/BetterSpray)** — upgrades the spray system with external and high-res images, correct aspect ratios, dynamic reloading and Steam sharing.
- **[ResourceReplacer](https://github.com/MetaHookSv/ResourceReplacer)** — redirects model and sound loading through global and per-map `.gmr` / `.gsr` rules.
- **[PrecacheManager](https://github.com/MetaHookSv/PrecacheManager)** — adds a command that dumps every precached sound, model and generic file next to the map.
- **[ThreadGuard](https://github.com/MetaHookSv/ThreadGuard)** — waits for engine threads to finish before a module unloads, fixing crash-on-exit.
- **[HeapPatch](https://github.com/MetaHookSv/HeapPatch)** — breaks through the GoldSrc heap limitation.
- **[HUDColor](https://github.com/MetaHookSv/HUDColor)** — changes HUD colors in game; also serves as a compact sample plugin. Forked from [DrAbcOfficial/HUDColor](https://github.com/DrAbcOfficial/HUDColor).

Third-party plugins such as ABCEnchance, halflife-cli, MetaAudio and Trinity-EngineSv are
covered in the [main README](https://github.com/MetaHookSv/MetaHookSv#plugins).

## Libraries

Shared libraries consumed by the plugins above:

- **[SteamAPIBridge](https://github.com/MetaHookSv/SteamAPIBridge)** — the shared `SteamAPIBridge.dll` behind SteamScreenshots, BetterSpray and UtilHTTPClient_SteamAPI.
- **[UtilAssetsIntegrity](https://github.com/MetaHookSv/UtilAssetsIntegrity)** — validates GoldSrc StudioModel assets and indexed-color BMP images.
- **[UtilHTTPClient_SteamAPI](https://github.com/MetaHookSv/UtilHTTPClient_SteamAPI)** — HTTP client built on the Steamworks HTTP API.
- **[UtilHTTPClient_libcurl](https://github.com/MetaHookSv/UtilHTTPClient_libcurl)** — HTTP client built on libcurl.
- **[UtilThreadTask](https://github.com/MetaHookSv/UtilThreadTask)** — a standalone task queue.

Mirrors kept so the build stays reproducible:

- **[SteamSDK](https://github.com/MetaHookSv/SteamSDK)** — mirror of the Steamworks SDK (© Valve Corporation).
- **[MemoryModulePP](https://github.com/MetaHookSv/MemoryModulePP)** — mirror of [bb107/MemoryModulePP](https://github.com/bb107/MemoryModulePP) with CMake support.

## Tools

- **[BSPLocalizationTools](https://github.com/MetaHookSv/BSPLocalizationTools)** — toolsets for GoldSrc BSP localization (C#).
- **[SteamAppsLocation](https://github.com/MetaHookSv/SteamAppsLocation)** — a Windows x86 CLI that locates an installed Steam game by AppId.
- **[MetahookInstaller](https://github.com/MetaHookSv/MetahookInstaller)** — GUI installer and CLI (see [Core](#core)).

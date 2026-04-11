# NewCore-AC

[![nopch-build](https://github.com/Lhorath/NewCore-AC/actions/workflows/core-build-nopch.yml/badge.svg?branch=master)](https://github.com/Lhorath/NewCore-AC/actions/workflows/core-build-nopch.yml?query=branch%3Amaster)
[![tools-build](https://github.com/Lhorath/NewCore-AC/actions/workflows/tools_build.yml/badge.svg?branch=master)](https://github.com/Lhorath/NewCore-AC/actions/workflows/tools_build.yml?query=branch%3Amaster)

## Fork notice

This repository is a **fork** of [AzerothCore (azerothcore-wotlk)](https://github.com/azerothcore/azerothcore-wotlk). It is **not** the official AzerothCore project.

**Purpose here:** development and experimentation around **tools** that support the AzerothCore ecosystem (extractors, importers, build/support utilities, and related workflows), while staying aligned with an AzerothCore-compatible core.

For the production emulator, community support, and contribution guidelines for the upstream project, use the [official AzerothCore repository](https://github.com/azerothcore/azerothcore-wotlk) and [wiki](https://www.azerothcore.org/wiki/).

## What this codebase is

AzerothCore is an open-source **World of Warcraft 3.3.5a (Wrath of the Lich King)** server emulator: a large **C++** codebase built with **CMake**, with **MySQL** databases for auth, characters, and world data. It is licensed under **GNU GPL v2**.

At runtime the project centers on two main programs:

| Component | Role |
|-----------|------|
| **authserver** | Login and realm selection (typically port 3724). |
| **worldserver** | Game world, packets, spells, instances, and scripts (typically port 8085). |

Major source areas:

| Path | Role |
|------|------|
| `src/common/` | Shared libraries (networking, crypto, logging, utilities). |
| `src/server/game/` | Core gameplay systems (entities, maps, spells, handlers, AI). |
| `src/server/scripts/` | Data-driven content scripts (bosses, quests, spells, instances). |
| `src/server/database/` | DB layer and schema updates. |
| `modules/` | Optional **modules** (static or dynamic) extending the worldserver without forking the whole core. |
| `src/tools/` | C++ **tools** built with `-DTOOLS_BUILD=...` (see below). |
| `apps/` | Supporting applications (Docker assets, installer pieces, config merge helpers, test framework, etc.). |
| `data/sql/` | SQL base dumps and update workflow for the three databases (`acore_auth`, `acore_characters`, `acore_world`). |

## Tools in this tree

CMake option **`TOOLS_BUILD`** controls C++ tools (default is often `none` in minimal setups). When enabled, it can build artifacts such as:

- **map_extractor** — client data to server map files  
- **vmap4_extractor** / **vmap4_assembler** — visual geometry for line-of-sight  
- **mmaps_generator** — navigation meshes (Recast/Detour)  
- **dbimport** — database import helper  

These live under `src/tools/`. Additional tooling and automation live under `apps/` (for example Docker and config-merger). CI includes a **tools** workflow (see badges above).

## Working with this fork

- **Remote setup:** keep an `upstream` remote pointing at `https://github.com/azerothcore/azerothcore-wotlk.git` to pull official changes.  
- **Contributions:** fixes and features that belong in the main emulator should be proposed **upstream**. Use this fork for tool-related work, experiments, and integration that you intend to keep or iterate on separately.

Build and architecture notes for agents and developers are in [CLAUDE.md](CLAUDE.md). Extended upstream-oriented readme content (badges, links, philosophy) is in [.github/README.md](.github/README.md).

## License and trademarks

Source code follows the same **GNU GPL v2** terms as AzerothCore. World of Warcraft and Blizzard Entertainment are trademarks of Blizzard Entertainment, Inc. This project is not affiliated with or endorsed by Blizzard Entertainment.

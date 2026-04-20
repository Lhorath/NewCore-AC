# DackCore

**DackCore** is an independent continuation of this codebase, maintained separately from upstream. It is a **World of Warcraft 3.3.5a (Wrath of the Lich King)** server emulator: a **C++** project built with **CMake**, using **MySQL** for auth, characters, and world data.

## Lineage and attribution

This project **did not start from scratch**. It inherits a long chain of open-source work:

1. **TrinityCore** — a major stage of the MaNGOS-family emulator line (see [AUTHORS](AUTHORS) for the full timeline: MaNGOS, ScriptDev2, TrinityCore, SunwellCore, AzerothCore, and links to historical repositories).
2. **AzerothCore** — ongoing development of the `azerothcore-wotlk` tree and community ([AzerothCore](https://www.azerothcore.org/), [GitHub](https://github.com/azerothcore/azerothcore-wotlk)).
3. **DackCore** — **this repository**, branched and maintained under the DackCore name.

**Branch divergence:** development under the **DackCore** name and maintainership **diverged from the prior fork line on 20 April 2026**. Changes after that date are **DackCore** decisions unless explicitly merged from upstream; prior history remains that of the upstream projects and their contributors.

Authorship and history are recorded in **git commit history** and summarized in **[AUTHORS](AUTHORS)**. Third-party libraries under `deps/` retain their own licenses and notices in their respective trees.

## Upstream relationship

If you keep an **`upstream`** remote, it should typically point at the AzerothCore tree you intend to track (for example `https://github.com/azerothcore/azerothcore-wotlk.git`). Fixes that belong in the shared ecosystem are still best contributed **upstream** when appropriate; DackCore-specific behavior stays here.

Build and layout notes for developers and tooling are in [CLAUDE.md](CLAUDE.md). Extra upstream-oriented material may live under [.github/README.md](.github/README.md).

## What this codebase contains

| Component | Role |
|-----------|------|
| **authserver** | Login and realm selection (often port 3724). |
| **worldserver** | Game world, packets, spells, instances, and scripts (often port 8085). |

| Path | Role |
|------|------|
| `src/common/` | Shared libraries (networking, crypto, logging, utilities). |
| `src/server/game/` | Core gameplay (entities, maps, spells, handlers, AI). |
| `src/server/scripts/` | Content scripts (bosses, quests, spells, instances). |
| `src/server/database/` | Database layer and schema updates. |
| `modules/` | Optional modules extending the worldserver. |
| `src/tools/` | Extractors and generators (see CMake `TOOLS_BUILD`). |
| `apps/` | Supporting apps (Docker, config helpers, tests, etc.). |
| `data/sql/` | SQL base dumps and updates for the three databases. |

### Tools (CMake `TOOLS_BUILD`)

When enabled, typical artifacts include **map_extractor**, **vmap4_extractor** / **vmap4_assembler**, **mmaps_generator**, and **dbimport** under `src/tools/`. See [CLAUDE.md](CLAUDE.md) for configure options.

### CI badges

After you publish **DackCore** on GitHub, add workflow status badges using **your** `owner/repository` URL so links stay valid.

## License and trademarks

- **Source code** in this tree is under the same **GNU GPL v2** terms as the AzerothCore / TrinityCore lineage unless a given file or directory states otherwise (for example bundled dependencies under `deps/`).
- **World of Warcraft** and **Blizzard Entertainment** are trademarks of Blizzard Entertainment, Inc. This project is **not** affiliated with or endorsed by Blizzard Entertainment.

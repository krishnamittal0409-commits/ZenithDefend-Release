# Changelog

All notable changes to **ZenithDefend** will be documented in this file.

## [1.0.1] - 2026-11-09

### Fixed & Enhanced
- **Fixed Class Version Compatibility**: Compiled with standard Java 21 LTS (bytecode version 65) and Java 17 LTS (bytecode version 61), eliminating `UnsupportedClassVersionError` across all Paper 1.20, 1.21, and 26.x server environments.
- **Fixed Database Transaction Rollbacks**: Completely eliminated SQLite/MySQL `UNIQUE` constraint crashes in `DictionaryManager`. Dictionary insertions now self-heal gracefully with fallback queries, ensuring all block, container, and chat logs are safely committed.
- **Fixed Folia vs Paper Scheduler Crashes**: Introduced universal runtime platform detector `PlatformScheduler` to safely bridge Folia region schedulers and standard Paper/Spigot schedulers with zero `NoSuchMethodError` exceptions.
- **Fixed Filter Parameters (`b:` and `e:`)**: Added full SQL filtering for included and excluded material types in both `/zd lookup` and `/zd rollback`.
- **Added Bucket Action Logging**: Added support for `PlayerBucketEmptyEvent` and `PlayerBucketFillEvent` to log water and lava placements.
- **Enhanced Inspector Double-Clicking**: Added hand equipment check and smart fallback to inspect both clicked block faces and adjacent positions.
- **Clean, Workable Professional In-Game Chat UI**: Streamlined all commands, lookups, rollbacks, and inspector output into standard, clean Minecraft interfaces (matching CoreProtect and LuckPerms standards) with zero text wrapping, clickable command tooltips, compact log records, and intuitive pagination buttons.
- **LuckPerms Admin Visibility**: Added root command permission `zenithdefend.use` and group node `zenithdefend.admin` so commands and tab completion are hidden from non-admin players.

## [1.0.0] - 2026-11-06

### Initial Release
- **Target Platform**: Paper 26.3 running on Java 25 LTS.
- **Dual Root Commands**: Both `/zd` and `/zenithdefend` are registered as primary commands with full tab-completion.
- **Inspector Tool**: `/zd inspect` (or `/zd i`) for left-click block inspection and right-click container transaction history (chests, double chests, barrels, hoppers, dispensers, droppers, smokers, blast furnaces, brewing stands, chiseled bookshelves).
- **Rollback & Restore Engine**:
  - `/zd rollback` (`/zd rb`) and `/zd restore` (`/zd rs`) with parameter support (`u:`, `t:`, `r:`, `a:`, `b:`, `e:`).
  - Chunk-batched application utilizing Paper's region schedulers to prevent main thread tick drops.
- **Lookup Engine**: `/zd lookup` (`/zd l`) with pagination (`/zd page <number>`) and interactive click-to-paginate chat components.
- **Asynchronous Storage Architecture**:
  - Dedicated background queue daemon flushing batched transactions without server lag.
  - Native support for SQLite (WAL mode) and MySQL / MariaDB via HikariCP.
  - In-memory dictionary caching for users, worlds, and materials to optimize database size.
- **Database Maintenance**: `/zd purge t:<time>` with automated SQLite `VACUUM` to reclaim disk space.
- **Full LuckPerms Compatibility**: Granular permission tree (`zenithdefend.*`, `zenithdefend.inspect`, `zenithdefend.rollback`, etc.) with permission-filtered tab suggestions.
- **Developer API**: Built-in `ZenithDefendAPI` registered in Bukkit's `ServicesManager`.

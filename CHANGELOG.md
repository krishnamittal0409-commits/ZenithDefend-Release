# Changelog

All notable changes to **ZenithDefend** will be documented in this file.

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

# ZenithDefend

<p align="center">
  <img src="https://cdn.modrinth.com/data/GmFL7KnV/bd4d03ad9fbb6bf05e25a0105cdabb57a25de1dd_96.webp" width="100" height="100" alt="ZenithDefend Logo" />
  <br />
  <b>High-Performance Data Logging, Anti-Griefing, and Rollback Engine</b>
  <br />
  <i>Engineered for Paper, Purpur, Folia, and Spigot from <b>Minecraft 1.20 up to 26.3</b>!</i>
</p>

---

## Overview

ZenithDefend is an enterprise-grade block logger, container transaction tracker, and anti-griefing system built as a modern, high-performance alternative to CoreProtect.

Whether you run a small survival server, an SMP, or a massive network, ZenithDefend provides lag-free, real-time logging and chunk-batched rollbacks with zero impact on server tick rates (MSPT).

---

## Compatibility

ZenithDefend provides dedicated builds tailored for every modern Minecraft generation:

* **Minecraft 1.20 Series (1.20 - 1.20.6):** Target Java 17 LTS (File: `ZenithDefend-1.0.1-MC1.20.jar`)
* **Minecraft 1.21 Series (1.21 - 1.21.11):** Target Java 21 LTS (File: `ZenithDefend-1.0.1.jar`)
* **Universal Future Builds (1.21.x - 26.x):** Target Java 21 LTS (File: `ZenithDefend-1.0.1.jar`)

Supported Platforms: Paper, Purpur, Folia, Spigot, Bukkit.

---

## Key Features

* **Click Inspector (`/zd i`):** Left-click any block to inspect history, right-click any container to view item transactions.
* **Lag-Free Rollback (`/zd rb`):** Chunk-batched rollback engine processes hundreds of thousands of changes smoothly without server hitching.
* **Reversible Restore (`/zd rs`):** Reapply changes or undo previous rollbacks with a single command.
* **War Reset & Time Rewind (`/zd rewind <time>`):** Reset the server back in time across **all 3 dimensions (Overworld, Nether, and The End)** to wipe out wars or TNT griefing.
* **Comprehensive TNT & Wither Tracking:** Full tracking and restoration for Primed TNT, TNT Minecarts, End Crystals, Respawn Anchors, and Wither destruction.
* **Physics & Gravity Block Restitution:** Restores falling blocks (sand, gravel, concrete powder, anvils) and support blocks (torches, ladders, signs, redstone) safely.
* **Log Lookup (`/zd l`):** Search block, container, chat, command, and interaction logs with clickable chat pagination.
* **Dual Storage Support:** Ultra-fast local SQLite (WAL mode) or external MySQL / MariaDB via HikariCP.
* **LuckPerms Native:** Granular permissions and smart tab-completion that hides commands from unauthorized players.

---

## Command Reference

| Command | Alias | Description | Permission |
| :--- | :--- | :--- | :--- |
| `/zd list` | `/zd help`, `/zd` | Show interactive dashboard with clickable action buttons | `zenithdefend.use` |
| `/zd params` | `/zd help params` | Open interactive parameter and filter reference guide | `zenithdefend.use` |
| `/zd inspect` | `/zd i` | Toggle click inspection on blocks and containers | `zenithdefend.inspect` |
| `/zd lookup <params>` | `/zd l` | Search logged actions (blocks, containers, chat, commands) | `zenithdefend.lookup` |
| `/zd rollback <params>` | `/zd rb` | Revert griefing within a time/radius/player/action filter | `zenithdefend.rollback` |
| `/zd restore <params>` | `/zd rs` | Reapply / undo previously rolled back changes | `zenithdefend.restore` |
| `/zd rewind <time> [scope]` | `/zd reset` | Reset server back in time across all 3 dimensions | `zenithdefend.rollback` |
| `/zd page <number>` | — | Navigate search results with interactive clickable chat buttons | `zenithdefend.lookup` |
| `/zd purge t:<time>` | — | Delete old logs (e.g. `t:30d`) to free disk space | `zenithdefend.purge` |
| `/zd status` | — | Display live queue, batch size, and database metrics | `zenithdefend.status` |
| `/zd reload` | — | Reload configuration settings from disk | `zenithdefend.reload` |

---

## Parameter Guide

Parameters can be combined in any order in `/zd rollback`, `/zd restore`, and `/zd lookup`.

### User Filter (`u:`)
* `u:<player>` — Filter by player username (e.g. `u:Steve`, `u:Steve,Alex`).
* `u:#tnt` — All TNT sources: Primed TNT, TNT Minecarts, End Crystals, Respawn Anchors.
* `u:#wither` — Wither skull projectiles and Wither body break smashes.
* `u:#creeper` — Creeper blast damage.
* `u:#fire` and `u:#lava` — Fire spread and lava block burning.
* `u:#water` — Water flows and fluid washes.
* `u:#dragon` and `u:#enderman` — Mob griefing.
* `u:#explosion` — All explosion types combined.
* `u:#physics` — Gravity blocks (sand, gravel) and detached support blocks (torches, redstone).

### Time Window (`t:`)
* Units: `s` (seconds), `m` (minutes), `h` (hours), `d` (days), `w` (weeks).
* Examples: `t:10m` (10 minutes), `t:1h` (1 hour), `t:1d` (24 hours), `t:7d` (7 days).

### Radius Scope (`r:`)
* `r:<number>` — Spherical block radius centered on you (e.g. `r:10`, `r:50`, `r:100`).
* `r:#world` — Targets the entire current dimension without distance limits.
* `r:#global` — Targets **all 3 dimensions (Overworld, Nether, and The End)** simultaneously.

### Action Type (`a:`)
* `a:+block` — Only block placements.
* `a:-block` — Only block breaks and destruction.
* `a:block` — Both block placements and block breaks.
* `a:container` — Chest, barrel, hopper, and shulker transactions.
* `a:click` — Door, lever, trapdoor, button, and lectern interactions.
* `a:chat` — Player chat messages.
* `a:command` — Commands run by players.
* `a:burn` — Blocks destroyed by fire and lava.
* `a:explode` — Blocks destroyed by explosive forces.

### Block Filters (`b:` and `e:`)
* `b:<materials>` — Restrict the operation strictly to these blocks (e.g. `b:tnt,lava`).
* `e:<materials>` — Exclude these blocks from being rolled back (e.g. `e:dirt,cobblestone,stone`).

---

## Quick Examples

* `/zd rewind 15m` — Reset entire server back 15 minutes across Overworld, Nether, and The End.
* `/zd rewind 15m current` — Reset only your current dimension back 15 minutes.
* `/zd rewind 30m 100` — Reset a 100-block radius around you back 30 minutes.
* `/zd rollback u:#tnt t:1h r:50` — Rollback all TNT explosions in a 50-block radius.
* `/zd rollback u:#wither t:2h r:#world` — Undo all Wither destruction across the entire world.
* `/zd rollback u:Griefer123 t:1d r:30` — Rollback a player in a 30-block radius over the past 24 hours.
* `/zd rollback b:tnt,lava t:2h r:50` — Undo only TNT and lava placements within 50 blocks.
* `/zd lookup a:container t:12h r:10` — View chest transactions within 10 blocks over the past 12 hours.

---

## LuckPerms Configuration

To make ZenithDefend visible and usable only by your admin group:

```bash
/lp group default permission set zenithdefend.* false
/lp group admin permission set zenithdefend.* true
/lp user <YourUsername> parent add admin
```

---

## Support and Links

* Discord: Contact **@kzen_fights** (Discord User ID: `1275335096924373032`)
* GitHub Issues: https://github.com/krishnamittal0409-commits/ZenithDefend-Release/issues
* Source Code: https://github.com/krishnamittal0409-commits/ZenithDefend-Release

---

## License

Released under the GNU General Public License v3.0.

# ZenithDefend

**High-Performance Block Logging, Rollback, and Anti-Griefing Engine**  
*Created and Developed by **Krishna Mittal** • All Rights Reserved*  
*Compatible with Paper, Purpur, Folia, and Spigot (Minecraft 1.20 up to 26.3)*

---

### Overview

**ZenithDefend** is an enterprise-grade block logger, container transaction tracker, and anti-griefing system built as a modern, high-speed alternative to CoreProtect. It runs completely in the background on an asynchronous queue, ensuring **zero tick-rate (MSPT) impact and zero server lag**.

Whether you run a private SMP, factions server, or high-traffic network, ZenithDefend provides instant click inspection, 3D cuboid spawn protection, and server-wide time rewinds.

---

### Core Features

* **3D Cuboid Spawn & Region Protection:** Define 3D protection cuboids by coordinates (`/zd protect set`), corner-selection wand (`/zd protect wand`), or one-command spawn protector (`/zd protect setspawn`).
* **Multi-Dimension War Reset (`/zd rewind <time>`):** Instantly reset the entire server (Overworld, Nether, and The End) or a chosen radius back 10m, 30m, 1h, or 2h.
* **Full Blast & Explosions Tracking:** Rollback Primed TNT, TNT Minecarts, End Crystals, Respawn Anchors, Creepers, and Withers without leaving craters.
* **Smart Gravity & Physics Restitution:** Safely restores falling blocks (sand, gravel, concrete powder) and wall-attached fixtures (torches, ladders, lanterns, signs, redstone) without popping off.
* **Instant Click Inspector (`/zd i`):** Left-click any block for placement/break history. Right-click any container (chest, barrel, shulker, furnace) to inspect item transactions.
* **Zero-Lag Async Engine:** Background batch consumer processes transactions without impacting server TPS.
* **Dual Storage Support:** Blazing fast local SQLite with Write-Ahead Logging (WAL), or external MySQL/MariaDB pooling with HikariCP.
* **Safe Hot Auto-Updates (`/zd update`):** Integrated updater checks for builds and downloads directly to `plugins/update/` without version mismatch errors.
* **Clean In-Game Chat UI:** Professional, compact layout matching modern Minecraft standards with zero text-wrapping and interactive clickable commands.

---

### 3D Cuboid Spawn & Region Protection

Protect your server spawn, warzones, arenas, and player bases from griefing by non-OP players.

#### 📐 Protection Commands

| Command | Description |
| :--- | :--- |
| `/zd protect set <name> <x1> <y1> <z1> <x2> <y2> <z2> [world]` | Define a 3D cuboid by direct XYZ coordinates |
| `/zd protect wand` | Receive the visual selection wand (Golden Hoe) |
| `/zd protect pos1 [x y z]` / `/zd protect pos2 [x y z]` | Set Corner 1 or Corner 2 manually or at feet |
| `/zd protect create <name>` | Create and activate a zone from wand/pos selections |
| `/zd protect setspawn [radius]` | Auto-protect spawn from $Y=-64$ to $Y=320$ (default $r=50$) |
| `/zd protect list` | List all active zones, coordinates, and block volumes |
| `/zd protect info [name]` | Inspect boundary coordinates and flag states |
| `/zd protect flag <name> <flag> <true\|false>` | Toggle individual protection rules (see flags below) |
| `/zd protect tp <name>` | Teleport to the safe center of a protected zone |
| `/zd protect remove <name>` | Permanently delete a protected zone |

#### 🛡️ Non-OP Grief Protections Enforced

* **Block Breaks & Places:** Unauthorized block modification is immediately blocked with an audible warning.
* **Containers & Mechanisms:** Protects chests, barrels, shulker boxes, hoppers, doors, trapdoors, levers, and buttons.
* **Fluids & Buckets:** Prevents lava/water placing or scooping, and blocks exterior fluids from flowing in across borders.
* **Explosion Shield:** Completely filters out TNT, minecarts, crystals, anchors, creepers, and withers from damaging blocks.
* **Farmland Trampling:** Farmland crops cannot be trampled.
* **Piston Defense:** Blocks pistons from pushing or pulling blocks across zone boundaries.
* **Display Items:** Protects item frames, glow item frames, and armor stands from tampering or breakage.
* **PVP & Animals:** Disables player vs player combat and prevents harming passive creatures and villagers.

#### 🚩 Available Flags
Use `/zd protect flag <name> <flag> <true|false>` to toggle:
`break` • `place` • `interact` • `explosions` • `fire` • `pvp` • `mobdamage`

> **Admin Bypass:** Server operators (OP) and players with permission `zenithdefend.protect.bypass` or `zenithdefend.admin` bypass all restrictions automatically.

---

### General Command Reference

| Command | Alias | Description | Permission |
| :--- | :---: | :--- | :---: |
| `/zd inspect` | `/zd i` | Toggle click inspection on blocks & containers | `zenithdefend.inspect` |
| `/zd rollback <params>` | `/zd rb` | Revert griefing across time, area, or player | `zenithdefend.rollback` |
| `/zd restore <params>` | `/zd rs` | Reapply or undo previous rollback actions | `zenithdefend.restore` |
| `/zd rewind <time> [scope]` | `/zd reset` | **War Reset:** Reset all 3 dimensions back in time | `zenithdefend.rollback` |
| `/zd protect <subcommand>` | `/zd zone` | 3D cuboid spawn & region protection | `zenithdefend.protect` |
| `/zd lookup <params>` | `/zd l` | Search block, container, and chat histories | `zenithdefend.lookup` |
| `/zd page <number>` | — | Browse interactive search pages | `zenithdefend.lookup` |
| `/zd params` | — | Open interactive in-game filter guide | `zenithdefend.use` |
| `/zd status` | — | View live performance, queue, and database metrics | `zenithdefend.status` |
| `/zd update [check\|install]` | `/zd upgrade` | Check or install automatic in-place updates | `zenithdefend.update` |
| `/zd purge t:<time>` | — | Purge historical logs older than specified time | `zenithdefend.purge` |
| `/zd reload` | — | Reload configuration settings from disk | `zenithdefend.reload` |

---

### Query Parameters Guide

Parameters can be specified in any order in `/zd rollback`, `/zd restore`, and `/zd lookup`:

* **`u:<user>`** — Player or environmental cause:
  * `u:Steve` (specific player)
  * `u:Steve,Alex` (multiple players)
  * `u:#tnt` (all TNT, crystals, anchors, minecarts)
  * `u:#wither` (wither destruction & skulls)
  * `u:#creeper` (creeper blasts)
  * `u:#fire` (fire spread)
* **`t:<time>`** — Timeframe:
  * `t:10m` (10 minutes) • `t:1h` (1 hour) • `t:1d` (24 hours) • `t:7d` (7 days)
* **`r:<radius>`** — Area / Dimension scope:
  * `r:20` (20-block radius)
  * `r:#world` (entire current dimension)
  * `r:#global` (all 3 dimensions: Overworld, Nether, and The End)
* **`a:<action>`** — Action filter:
  * `a:+block` (placements) • `a:-block` (breaks) • `a:container` (chest items) • `a:click` (doors/buttons) • `a:chat` (chat)
* **`b:<blocks>`** — Include specific materials:
  * `b:tnt,lava` (only touch TNT and lava)
* **`e:<blocks>`** — Exclude materials:
  * `e:dirt,stone,cobblestone` (protect dirt/stone from rollbacks)

---

### Practical Admin Examples

```bash
# Emergency: Reset all 3 dimensions back 15 minutes after a war:
/zd rewind 15m

# Reset only the Nether dimension back 1 hour:
/zd rewind 1h nether

# Protect spawn with a 3D cuboid from (-100, -64, -100) to (100, 320, 100):
/zd protect set spawn -100 -64 -100 100 320 100

# Quick auto-protect world spawn with a 75-block radius:
/zd protect setspawn 75

# Rollback all TNT explosions in a 50-block radius from the last 2 hours:
/zd rollback u:#tnt t:2h r:50

# Rollback a griefer's block breaks within 30 blocks:
/zd rollback u:Griefer123 a:-block t:1d r:30

# Undo fire spread within a 40-block radius:
/zd rollback u:#fire t:6h r:40

# Check chest deposits and withdrawals within 10 blocks:
/zd lookup a:container t:12h r:10
```

---

### LuckPerms Permissions

| Permission Node | Default | Description |
| :--- | :---: | :--- |
| `zenithdefend.*` | `OP` | Grants access to all commands |
| `zenithdefend.admin` | `OP` | Full administrative control |
| `zenithdefend.protect` | `OP` | Allows managing spawn & cuboid protection zones |
| `zenithdefend.protect.bypass` | `OP` | Allows bypassing protection restrictions |
| `zenithdefend.use` | `true` | Allows using `/zd list`, `/zd help`, and `/zd params` |
| `zenithdefend.inspect` | `OP` | Allows toggling click inspector (`/zd i`) |
| `zenithdefend.lookup` | `OP` | Allows searching logged actions (`/zd l`) |
| `zenithdefend.rollback` | `OP` | Allows executing rollbacks, restores, and war resets |
| `zenithdefend.restore` | `OP` | Allows undoing rollbacks (`/zd rs`) |
| `zenithdefend.update` | `OP` | Allows checking and installing updates (`/zd update`) |
| `zenithdefend.purge` | `OP` | Allows purging old database records |
| `zenithdefend.status` | `OP` | Allows viewing engine performance counters |
| `zenithdefend.reload` | `OP` | Allows reloading configuration |

---

### Support & Community

* **Discord:** Direct message **`@kzen_fights`** (User ID: `1275335096924373032`) for questions, help, or feature requests!
* **Bug Reports & Issues:** https://github.com/krishnamittal0409-commits/ZenithDefend-Release/issues
* **Downloads & Builds:** https://github.com/krishnamittal0409-commits/ZenithDefend-Release

---

### Author & Proprietary License

* **Author & Lead Developer:** **Krishna Mittal**
* **Copyright:** © 2026 Krishna Mittal. All rights reserved.
* **License:** **All Rights Reserved (LicenseRef-All-Rights-Reserved)**. ZenithDefend is proprietary software. No part of this software, its binary distributions, or its assets may be copied, redistributed, reverse-engineered, or modified without the express written permission of **Krishna Mittal**.

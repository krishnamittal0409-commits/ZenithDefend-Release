# ZenithDefend

<p align="center">
  <img src="https://cdn.modrinth.com/data/GmFL7KnV/bd4d03ad9fbb6bf05e25a0105cdabb57a25de1dd_96.webp" width="100" height="100" alt="ZenithDefend Shield Logo" />
  <br />
  <b>High-Performance Data Logging, Anti-Griefing, and Rollback Engine</b>
  <br />
  <i>Created and Developed by <b>Krishna Mittal</b> • All Rights Reserved</i>
  <br />
  <i>Engineered for Paper, Purpur, Folia, and Spigot - Playable from <b>Minecraft 1.20 up to 26.3</b>!</i>
  <br /><br />
  <a href="https://modrinth.com/plugin/zenithdefend"><img src="https://img.shields.io/badge/Author-Krishna_Mittal-00d2ff?style=for-the-badge" alt="Author Krishna Mittal" /></a>
  <a href="https://modrinth.com/plugin/zenithdefend"><img src="https://img.shields.io/badge/Rights-All_Rights_Belong_To_Krishna_Mittal-blueviolet?style=for-the-badge" alt="All Rights Belong To Krishna Mittal" /></a>
  <a href="https://modrinth.com/plugin/zenithdefend"><img src="https://img.shields.io/badge/Minecraft-1.20_to_26.3-2ea44f?style=for-the-badge&logo=minecraft&logoColor=white" alt="Minecraft Version" /></a>
  <a href="https://modrinth.com/plugin/zenithdefend"><img src="https://img.shields.io/badge/Platform-Paper_%7C_Purpur_%7C_Folia-e67e22?style=for-the-badge" alt="Platform Paper Purpur Folia" /></a>
  <a href="https://modrinth.com/plugin/zenithdefend"><img src="https://img.shields.io/badge/Java-17_%7C_21-007acc?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java Runtime" /></a>
  <a href="https://github.com/krishnamittal0409-commits/ZenithDefend-Release/releases"><img src="https://img.shields.io/badge/Release-v1.0.1-brightgreen?style=for-the-badge&logo=github" alt="GitHub Release" /></a>
  <a href="https://github.com/krishnamittal0409-commits/ZenithDefend-Release/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-GPL_v3-9b59b6?style=for-the-badge" alt="GPL License" /></a>
</p>

---

> 🏆 **Engineered for High-Traffic Gaming:** ZenithDefend is an enterprise-grade block logger, container tracker, and anti-griefing system built as a modern, high-speed alternative to CoreProtect. Zero tick spikes (MSPT), zero lag, and instant chunk-batched rollbacks.
>
> 💬 **Discord Support:** Reach out anytime on Discord to **`@kzen_fights`** (User ID: `1275335096924373032`) for questions, help, or feature requests!

---

## 🛡️ Overview

**ZenithDefend** logs thousands of block and container actions per second with **zero impact on server MSPT**. Whether you run a hardcore survival server, an SMP, or a massive network, ZenithDefend provides instant rollbacks, click inspections, and time rewinds.

---

## 🎮 Multi-Version Compatibility

Dedicated builds are compiled to match your server's exact Java runtime and eliminate version conflicts:

* 🟢 **Minecraft 1.20 Series (`1.20` – `1.20.6`):**
  * Java Runtime: **Java 17 LTS+**
  * Recommended File: `ZenithDefend-1.0.1-MC1.20.jar`
* 🟢 **Minecraft 1.21 Series (`1.21` – `1.21.11`):**
  * Java Runtime: **Java 21 LTS+**
  * Recommended File: `ZenithDefend-1.0.1.jar`
* 🟢 **Universal & Future (`1.21.x` – `26.x`):**
  * Java Runtime: **Java 21 LTS+**
  * Recommended File: `ZenithDefend-1.0.1.jar`

**Supported Platforms:** Paper, Purpur, Folia, Spigot, Bukkit.

---

## ⚡ Key Features

* 🔎 **Click Inspector (`/zd i`):** Left-click any block to inspect its placement and break history. Right-click any chest, barrel, furnace, or shulker box to view item deposits and withdrawals.
* ⏪ **Lag-Free Rollbacks (`/zd rb`):** Chunk-batched rollback engine processes hundreds of thousands of changes smoothly without server hitching.
* ⏩ **Reversible Restores (`/zd rs`):** Reapply changes or undo previous rollbacks with a single command.
* ⏳ **War Reset & Time Rewind (`/zd rewind <time>`):** Instantly rewind the server back in time across **all 3 dimensions (Overworld, Nether, and The End)** to wipe out wars, griefing attacks, or TNT bombardments.
* 💣 **Comprehensive TNT & Wither Tracking:** Full tracking and restoration for Primed TNT, TNT Minecarts, End Crystals, Respawn Anchors, and Wither destruction.
* 🏗️ **Physics & Gravity Block Restitution:** Restores falling blocks (sand, gravel, concrete powder, anvils) and support-dependent blocks (torches, ladders, signs, redstone, lanterns) safely without popping off.
* 📜 **Interactive Log Lookup (`/zd l`):** Search block, container, chat, command, and interaction logs with clickable chat pagination (`/zd page <n>`).
* ⚡ **Zero-Lag Async Pipeline:** Dedicated daemon queue batches database transactions asynchronously.
* 🗄️ **Dual Storage Support:** Ultra-fast local SQLite (WAL mode) or external MySQL / MariaDB via HikariCP.
* 🛡️ **Full LuckPerms Integration:** Granular permissions and smart tab-completion that hides commands from unauthorized players.
* 💬 **Clean, Workable In-Game UI:** Standard, professional Minecraft chat interface (matching CoreProtect and LuckPerms standards) with zero text wrapping, clickable command suggestions, and intuitive pagination.

---

## 📋 Command Reference

| Command | Alias | Full Parameter Syntax | Description | Permission |
| :--- | :--- | :--- | :--- | :--- |
| `/zd list` | `/zd help` | None | Interactive dashboard & quick action menu | `zenithdefend.use` |
| `/zd params` | `/zd help params` | None | Open interactive in-game filter reference guide | `zenithdefend.use` |
| `/zd inspect` | `/zd i` | None | Toggle click inspection on blocks & containers | `zenithdefend.inspect` |
| `/zd rollback` | `/zd rb` | `u:<user> t:<time> r:<radius> a:<action> b:<blocks> e:<blocks>` | Revert griefing actions across time, area, or player | `zenithdefend.rollback` |
| `/zd restore` | `/zd rs` | `u:<user> t:<time> r:<radius> a:<action> b:<blocks> e:<blocks>` | Reapply / undo previously rolled back changes | `zenithdefend.restore` |
| `/zd rewind` | `/zd reset` | `<time> [all \| current \| nether \| end \| radius]` | **War Reset**: Reset entire server back in time | `zenithdefend.rollback` |
| `/zd protect` | `/zd zone` | `[wand\|create\|set\|setspawn\|list\|info\|remove\|tp\|flag]` | **Spawn Protection**: 3D cuboid anti-grief zones | `zenithdefend.protect` |
| `/zd lookup` | `/zd l` | `u:<user> t:<time> r:<radius> a:<action> b:<blocks> e:<blocks>` | Search historical block, container, and chat logs | `zenithdefend.lookup` |
| `/zd page` | None | `<page_number>` | Jump to specific page of lookup search results | `zenithdefend.lookup` |
| `/zd purge` | None | `t:<time>` | Purge historical logs older than specified time | `zenithdefend.purge` |
| `/zd status` | None | None | Display live engine analytics & database metrics | `zenithdefend.status` |
| `/zd reload` | None | None | Reload configuration settings from disk | `zenithdefend.reload` |

---

## 🔍 Complete Parameter Guide

Parameters can be specified in any order in `/zd rollback`, `/zd restore`, and `/zd lookup`.

### 👤 User & Entity Filter (`u:<target>`)

Filters actions by the player or environmental cause responsible:

* `u:<player>` - Target a specific player (e.g. `u:Steve`).
* `u:<player1>,<player2>` - Target multiple players (e.g. `u:Steve,Alex,Griefer99`).
* `u:#tnt` - All TNT explosions: Primed TNT, TNT Minecarts, End Crystals, Respawn Anchors.
* `u:#wither` - Wither skull projectiles and Wither body break smashes.
* `u:#creeper` - Creeper blast damage.
* `u:#fire` - Fire spread and combustion.
* `u:#lava` - Lava flows and burning damage.
* `u:#water` - Water flow and fluid washes.
* `u:#dragon` - Ender Dragon block destruction.
* `u:#enderman` - Enderman block pickups and placements.
* `u:#explosion` - All explosion types combined.
* `u:#physics` - Gravity blocks (sand, gravel) and detached support blocks (torches, redstone).

### ⏰ Time Window (`t:<time>`)

Restricts the query to actions within a specific past timeframe:

* `t:<number>s` - Seconds (e.g. `t:30s`, `t:90s`)
* `t:<number>m` - Minutes (e.g. `t:10m`, `t:15m`, `t:30m`)
* `t:<number>h` - Hours (e.g. `t:1h`, `t:6h`, `t:12h`)
* `t:<number>d` - Days (e.g. `t:1d`, `t:3d`, `t:7d`)
* `t:<number>w` - Weeks (e.g. `t:1w`, `t:2w`, `t:4w`)

### 📍 Radius & Dimension Scope (`r:<radius>`)

Controls the spatial area of the operation:

* `r:<number>` - Spherical block radius centered on you (e.g. `r:10`, `r:50`, `r:100`).
* `r:#world` - The entire current dimension without distance bounds.
* `r:#global` - **All 3 dimensions (Overworld, Nether, and The End)** simultaneously.

### ⚡ Action Filter (`a:<action>`)

Filters specifically by the type of action performed:

* `a:+block` - Only block placements.
* `a:-block` - Only block breaks and destructions.
* `a:block` - Both block placements and block breaks.
* `a:container` - Chest, barrel, hopper, and shulker transactions (deposits & withdrawals).
* `a:click` - Door, lever, trapdoor, button, and lectern interactions.
* `a:chat` - Player chat messages.
* `a:command` - Commands run by players.
* `a:burn` - Blocks destroyed by fire or lava.
* `a:explode` - Blocks destroyed by explosive forces.
* `a:natural` - Environmental world decay (leaf decay, ice melting, snow fading).
* `a:liquid` - Liquid flows and fluid spreads.

### 🧱 Block Include & Exclude (`b:` and `e:`)

Narrow down changes to specific materials, or protect certain materials from being touched:

* `b:<materials>` *(Include)*: Restrict strictly to these blocks (e.g. `b:tnt,lava`, `b:diamond_block,chest`).
* `e:<materials>` *(Exclude)*: Prevent these blocks from being touched (e.g. `e:dirt,cobblestone,stone`).

---

## 🎯 Practical Administrator Examples

```bash
# --- EMERGENCY WAR & SERVER RESET ---
# 1. Reset the entire server back 15 minutes across Overworld, Nether, and The End:
/zd rewind 15m

# 2. Reset only your current dimension back 30 minutes:
/zd rewind 30m current

# 3. Reset only the Nether dimension back 1 hour:
/zd rewind 1h nether

# 4. Reset a 100-block radius around you back 15 minutes:
/zd rewind 15m 100

# --- TARGETED ROLLBACKS ---
# 5. Rollback all TNT explosions in a 50-block radius from the last hour:
/zd rollback u:#tnt t:1h r:50

# 6. Undo all Wither destruction across the entire world over the last 2 hours:
/zd rollback u:#wither t:2h r:#world

# 7. Rollback a malicious player in a 30-block radius from the past 24 hours:
/zd rollback u:Griefer123 t:1d r:30

# 8. Undo fire spread within 40 blocks from the last 6 hours:
/zd rollback u:#fire t:6h r:40

# 9. Rollback only TNT and lava placements without affecting normal building:
/zd rollback b:tnt,lava t:2h r:50

# 10. Rollback block breaks while ignoring cobblestone and dirt:
/zd rollback a:-block e:dirt,cobblestone t:3h r:25

# --- LOG LOOKUPS ---
# 11. View all chest withdrawals and deposits within 10 blocks over the past 12 hours:
/zd lookup a:container t:12h r:10

# 12. View chat messages sent by a specific player in the last hour:
/zd lookup u:Steve a:chat t:1h

# 13. Search all commands issued within a 20-block radius:
/zd lookup a:command t:2h r:20
```

---

## 🏰 3D Cuboid Spawn & Region Protection Engine

ZenithDefend includes a high-performance 3D cuboid protection system to protect spawns, arenas, and administrative areas from non-OP griefing.

### 📐 Defining a Protected Zone
1. **Direct Coordinate Input (forms a 3D Cube/Cuboid):**
   ```bash
   /zd protect set <name> <x1> <y1> <z1> <x2> <y2> <z2> [world]
   ```
   *Specifies the exact 3D coordinates from one corner point `(x1, y1, z1)` to the opposite corner `(x2, y2, z2)`.*

2. **Visual Protection Wand:**
   * Run `/zd protect wand` to receive the Golden Hoe wand.
   * **Left-click** any block to set **Position 1**.
   * **Right-click** any block to set **Position 2**.
   * Run `/zd protect create <name>` to define and protect the cuboid.

3. **Quick Auto Spawn Protector:**
   ```bash
   /zd protect setspawn [radius]
   ```
   *Creates a protected cuboid around spawn from minimum world height (`Y=-64`) to maximum world height (`Y=320`) with customizable radius (default: 50 blocks).*

### 🛡️ Non-OP Grief Protections Enforced:
* 🚫 **Block Breaking & Placing:** Unauthorized block modification is blocked and notifies the player.
* 🚫 **Container & Mechanism Security:** Prevents opening chests, barrels, shulkers, hoppers, doors, trapdoors, levers, and buttons.
* 🚫 **Fluid Griefing:** Prevents placing or collecting lava/water buckets, and stops liquid from flowing across boundaries into protected areas.
* 🚫 **Explosion Shield:** Filters out TNT, minecarts, crystals, anchors, creepers, and withers from breaking blocks inside protected zones.
* 🚫 **Crop Trampling:** Blocks physical trampling of farmland.
* 🚫 **Piston Defense:** Prevents pistons from pushing or pulling blocks across protected zone boundaries.
* 🚫 **Item Frames & Armor Stands:** Prevents breaking or modifying item displays.
* 🚫 **Spawn PVP & Creature Protection:** Disables player vs player combat and prevents harming passive mobs and villagers within designated safe zones.

### 🚩 Customizable Flags:
```bash
/zd protect flag <name> <break|place|interact|explosions|fire|pvp|mobdamage> <true|false>
```
* **Bypass Permission:** Server operators (OP) and players with `zenithdefend.protect.bypass` or `zenithdefend.admin` bypass all restrictions automatically.

---

## 🔐 LuckPerms Setup & Permissions

ZenithDefend integrates natively with **LuckPerms** and Bukkit's permission system:

| Permission Node | Default | Description |
| :--- | :---: | :--- |
| `zenithdefend.*` | `OP` | Grants access to all ZenithDefend commands |
| `zenithdefend.admin` | `OP` | Full administrative control |
| `zenithdefend.protect` | `OP` | Allows managing spawn and cuboid protection zones |
| `zenithdefend.protect.bypass` | `OP` | Allows bypassing protection restrictions |
| `zenithdefend.use` | `true` | Allows using `/zd list`, `/zd help`, and `/zd params` |
| `zenithdefend.inspect` | `OP` | Allows toggling click inspector (`/zd i`) |
| `zenithdefend.lookup` | `OP` | Allows searching logged actions (`/zd l`) |
| `zenithdefend.rollback` | `OP` | Allows executing rollbacks and rewinds (`/zd rb`, `/zd rewind`) |
| `zenithdefend.restore` | `OP` | Allows undoing rollbacks (`/zd rs`) |
| `zenithdefend.purge` | `OP` | Allows purging old database records (`/zd purge`) |
| `zenithdefend.status` | `OP` | Allows viewing live telemetry and metrics (`/zd status`) |
| `zenithdefend.reload` | `OP` | Allows reloading configuration (`/zd reload`) |

> 💡 **Smart Tab Completion:** Commands are dynamically filtered in real time according to the player's LuckPerms permissions. Unauthorized commands are never suggested.

```bash
# 1. Deny ZenithDefend from regular players (hides all admin subcommands & tab completions):
/lp group default permission set zenithdefend.* false

# 2. Grant full access to your admin group:
/lp group admin permission set zenithdefend.* true

# 3. Add yourself as an admin:
/lp user <YourUsername> parent add admin
```

---

## 🗄️ Database Configuration

By default, ZenithDefend uses a high-speed local SQLite database (`zenithdefend.db`) tuned with WAL mode (`PRAGMA journal_mode=WAL`).

For large networks, external **MySQL** or **MariaDB** can be enabled in `plugins/ZenithDefend/config.yml`:

```yaml
database:
  type: mysql
  table-prefix: zd_
  pool-size: 10
  connection-timeout-ms: 10000
  mysql:
    host: localhost
    port: 3306
    database: zenithdefend
    username: root
    password: "your_strong_password"
```

---

## 💬 Community & Support

* 💬 **Discord:** Direct message **`@kzen_fights`** (User ID: `1275335096924373032`) for questions, help, or feature requests!
* 🐛 **GitHub Issues:** https://github.com/krishnamittal0409-commits/ZenithDefend-Release/issues
* 📦 **Release Repository:** https://github.com/krishnamittal0409-commits/ZenithDefend-Release

---

## 👑 Author & Legal Rights

* **Original Creator & Sole Author:** **Krishna Mittal**
* **Rights & Intellectual Property:** **All rights belong entirely to Krishna Mittal.** All proprietary ownership, copyright, and distribution rights are held by Krishna Mittal.
* **Copyright:** © 2026 Krishna Mittal. All rights reserved.

---

## 📄 License

Released under the **GNU General Public License v3.0** with all authorship and ownership rights belonging to **Krishna Mittal**.

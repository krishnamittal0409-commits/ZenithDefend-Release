# ZenithDefend

<p align="center">
  <img src="https://cdn.modrinth.com/data/GmFL7KnV/bd4d03ad9fbb6bf05e25a0105cdabb57a25de1dd_96.webp" width="100" height="100" alt="ZenithDefend Logo" />
  <br />
  <b>High-Performance Data Logging, Anti-Griefing, and Rollback Engine</b>
  <br />
  <i>Engineered for Paper, Purpur, Folia, and Spigot — Fully playable from <b>Minecraft 1.20 up to 26.3</b>!</i>
  <br /><br />
  <a href="https://github.com/krishnamittal0409-commits/ZenithDefend-Release/releases"><img src="https://img.shields.io/badge/Release-v1.0.1-blue.svg?style=for-the-badge&logo=github" alt="Release" /></a>
  <a href="https://modrinth.com/plugin/zenithdefend"><img src="https://img.shields.io/badge/Modrinth-ZenithDefend-00AF5C.svg?style=for-the-badge&logo=modrinth" alt="Modrinth" /></a>
  <img src="https://img.shields.io/badge/Paper-1.20%20--%2026.3-orange.svg?style=for-the-badge&logo=buffer" alt="Paper" />
  <img src="https://img.shields.io/badge/Java-17%20%7C%2021-red.svg?style=for-the-badge&logo=openjdk" alt="Java" />
  <a href="https://github.com/krishnamittal0409-commits/ZenithDefend-Release/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-GPL--3.0-purple.svg?style=for-the-badge" alt="License" /></a>
</p>

---

## 🛡️ Overview

**ZenithDefend** is an enterprise-grade block logger, container transaction tracker, and anti-griefing system built as a modern, high-performance alternative to CoreProtect.

Whether you run a small survival server, an SMP, or a massive network, ZenithDefend provides **lag-free, real-time logging and chunk-batched rollbacks** with zero impact on server tick rates (MSPT).

---

## 🚀 Multi-Version Compatibility

ZenithDefend provides dedicated builds tailored for every modern Minecraft generation:

* 🟢 **Minecraft 1.20 Series (`1.20` – `1.20.6`):**
  * Target: **Java 17 LTS**
  * File: `ZenithDefend-1.0.1-MC1.20.jar`
* 🟢 **Minecraft 1.21 Series (`1.21` – `1.21.11`):**
  * Target: **Java 21 LTS**
  * File: `ZenithDefend-1.0.1-MC1.21.jar`
* 🟢 **Universal / Future (`1.21.x` – `26.x`):**
  * Target: **Java 21 LTS**
  * File: `ZenithDefend-1.0.1.jar`

**Supported Platforms:** Paper, Purpur, Folia, Spigot, Bukkit.

---

## ⚡ Key Features

* 🔎 **Click Inspector (`/zd i` or `/zenithdefend i`):** Left-click any block to inspect its placement/break history, or right-click any chest, barrel, furnace, or shulker box to view all item deposits and withdrawals.
* ⏪ **Lag-Free Rollback (`/zd rb`):** Chunk-batched rollback engine processes hundreds of thousands of changes smoothly without server hitching.
* ⏩ **Reversible Restore (`/zd rs`):** Reapply changes or undo previous rollbacks with a single command.
* ⏳ **War Reset & Time Rewind (`/zd rewind <time> [scope]` or `/zd reset`):** Instantly rewind the server 10m, 15m, 30m, or 1h back in time across **all 3 dimensions (Overworld, Nether, and The End)** to wipe out wars, griefing attacks, or TNT bombardments.
* 💣 **Comprehensive TNT & Wither Protection:** Full tracking and restoration for Primed TNT, Minecart TNT, Ender Crystals, Respawn Anchors, and Wither skulls/explosions.
* 🏗️ **Physics & Gravity Block Restitution:** Restores falling blocks (sand, gravel, concrete powder, anvils) and support-dependent blocks (torches, ladders, signs, redstone, lanterns) safely without popping off.
* 📜 **Log Lookup (`/zd l`):** Search block, container, chat, command, and interaction logs with clickable chat pagination (`/zd page <n>`).
* ⚡ **Zero-Lag Async Pipeline:** Dedicated daemon queue batches database transactions asynchronously.
* 🗄️ **Dual Storage Support:** Ultra-fast local SQLite (WAL mode) or external MySQL / MariaDB via HikariCP.
* 🛡️ **Full LuckPerms Integration:** Granular permissions and smart tab-completion that hides commands from unauthorized players.
* 💻 **Web-Style Chat Dashboard:** Modern, interactive card UI with clickable actions, live hardware & engine telemetry, and memory graphs.

---

## 📋 Command Reference

| Command | Alias | Description | Permission |
| :--- | :--- | :--- | :--- |
| `/zd list` | `/zd help`, `/zd` | Show interactive dashboard with clickable action buttons | `zenithdefend.use` |
| `/zd params` | `/zd help params` | Open interactive parameter and filter reference guide | `zenithdefend.use` |
| `/zd inspect` | `/zd i` | Toggle click inspection on blocks & containers | `zenithdefend.inspect` |
| `/zd lookup <params>` | `/zd l` | Search logged actions (blocks, containers, chat, commands) | `zenithdefend.lookup` |
| `/zd rollback <params>` | `/zd rb` | Revert griefing within a time/radius/player/action filter | `zenithdefend.rollback` |
| `/zd restore <params>` | `/zd rs` | Reapply / undo previously rolled back changes | `zenithdefend.restore` |
| `/zd rewind <time> [scope]` | `/zd reset` | **War Reset Engine**: Reset server back in time across **all 3 dimensions** (Overworld, Nether, End) or a targeted scope | `zenithdefend.rollback` |
| `/zd page <number>` | — | Navigate search results with interactive clickable chat buttons | `zenithdefend.lookup` |
| `/zd purge t:<time>` | — | Delete old logs (e.g. `t:30d`, `t:4w`) to free disk space | `zenithdefend.purge` |
| `/zd status` | — | Display live queue, batch size, and database metrics | `zenithdefend.status` |
| `/zd reload` | — | Reload configuration settings from disk | `zenithdefend.reload` |

---

## 🔍 Complete Parameter & Filter Reference Guide

ZenithDefend features an intuitive and granular query engine. Parameters can be combined in any order in `/zd rollback`, `/zd restore`, and `/zd lookup`.

### 1. User & Entity Parameter (`u:<target>`)

Filters logged actions by the player or entity responsible. You can specify a single player, multiple players separated by commas, or environmental wildcards starting with `#`.

| Parameter Syntax | Description | Example |
| :--- | :--- | :--- |
| `u:<player>` | Single player username | `u:Steve` |
| `u:<player1>,<player2>` | Multiple comma-separated players | `u:Steve,Alex,Griefer99` |
| `u:#tnt` | All TNT sources: Primed TNT, TNT Minecarts, End Crystals, Respawn Anchors | `u:#tnt` |
| `u:#wither` | All Wither damage: flying skull projectiles and body break smashes | `u:#wither` |
| `u:#creeper` | Creeper explosion damage | `u:#creeper` |
| `u:#fire` | Fire spread and block combustion | `u:#fire` |
| `u:#lava` | Lava flows and lava-induced block destruction | `u:#lava` |
| `u:#water` | Water flows and fluid washes | `u:#water` |
| `u:#dragon` | Ender Dragon block collision damage | `u:#dragon` |
| `u:#enderman` | Enderman block pick-ups and place-downs | `u:#enderman` |
| `u:#explosion` | Combination of **all** explosion types (TNT, Creeper, Wither, Crystals, Anchors) | `u:#explosion` |
| `u:#physics` | Gravity blocks (sand, gravel, anvil) and support blocks (torches, ladders, redstone) | `u:#physics` |

---

### 2. Time Window Parameter (`t:<time>`)

Restricts the rollback or lookup to events that occurred within the specified duration leading up to the present moment.

| Time Unit | Abbreviation | Syntax Examples | Meaning |
| :---: | :---: | :--- | :--- |
| Seconds | `s` | `t:30s`, `t:90s` | Past 30 seconds / 90 seconds |
| Minutes | `m` | `t:5m`, `t:15m`, `t:30m` | Past 5 / 15 / 30 minutes |
| Hours | `h` | `t:1h`, `t:6h`, `t:12h` | Past 1 / 6 / 12 hours |
| Days | `d` | `t:1d`, `t:3d`, `t:7d` | Past 1 / 3 / 7 days |
| Weeks | `w` | `t:1w`, `t:2w`, `t:4w` | Past 1 / 2 / 4 weeks |

> **Shorthand Tip**: You can omit the `t:` prefix in shorthand queries (e.g. `/zd rollback u:Steve 1h 20`).

---

### 3. Radius & Dimension Parameter (`r:<radius>`)

Controls the spatial boundary around your current position or targets entire worlds.

| Parameter Syntax | Scope | Description |
| :--- | :--- | :--- |
| `r:<number>` | Local Radius | Spherical block radius centered on the executing player (e.g. `r:10`, `r:50`, `r:100`). |
| `r:#world` / `r:world` | Single Dimension | Targets the entire dimension you are currently in without distance limits. |
| `r:#global` / `r:global` | Server-Wide | Targets **all 3 dimensions (Overworld, Nether, and The End)** simultaneously. |

---

### 4. Action Type Parameter (`a:<action>`)

Filters specifically by the type of event performed.

| Action Syntax | Category | Description |
| :--- | :--- | :--- |
| `a:+block` | Block | Only block placements |
| `a:-block` | Block | Only block breaks / destruction |
| `a:block` | Block | Both block placements and block breaks |
| `a:container` (or `a:item`) | Inventory | Chest, barrel, hopper, and shulker transactions (deposits & withdrawals) |
| `a:click` | Interaction | Player interactions with doors, levers, trapdoors, buttons, and lecterns |
| `a:chat` | Communication | Player chat messages |
| `a:command` (or `a:cmd`) | Commands | Commands executed by players |
| `a:burn` | Environmental | Blocks consumed or destroyed by fire and lava |
| `a:explode` | Environmental | Blocks destroyed specifically by explosive forces |
| `a:natural` | Environmental | Leaf decay, ice melting, and snow fading |
| `a:liquid` | Environmental | Liquid flow and fluid spread events |

---

### 5. Block Inclusion & Exclusion Parameters (`b:` and `e:`)

Narrow down changes to specific materials, or protect certain materials from being affected.

* **`b:<materials>` (Include)**: Restrict the operation strictly to these blocks (comma-separated).
  * Example: `b:tnt,lava` — Targets only TNT and lava placements.
  * Example: `b:diamond_block,netherite_block` — Restores only valuable ore/mineral blocks.
* **`e:<materials>` (Exclude)**: Prevent these blocks from being touched.
  * Example: `e:dirt,cobblestone,stone` — Ignores cheap terrain filler blocks.
  * Example: `e:sand,gravel` — Leaves falling terrain as is.

---

### 6. Command Parameter Matrix

| Command | `u:` (User) | `t:` (Time) | `r:` (Radius) | `a:` (Action) | `b:` (Include) | `e:` (Exclude) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| `/zd rollback` (`/zd rb`) | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes |
| `/zd restore` (`/zd rs`) | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes |
| `/zd lookup` (`/zd l`) | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes |
| `/zd rewind` (`/zd reset`) | ⚡ Auto (All) | ✅ `<time>` | ⚡ Scope / `<r>` | ⚡ Auto (All) | ⚡ Auto (All) | ⚡ Auto |
| `/zd purge` | — | ✅ Required | — | — | — | — |

---

## 🎯 Practical Administrator Examples

```bash
# --- EMERGENCY WAR & SERVER RESET ---
# 1. Reset the entire server back 15 minutes across all 3 dimensions (Overworld, Nether, End):
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

# 10. Rollback all block destructions while ignoring cobblestone and dirt:
/zd rollback a:-block e:dirt,cobblestone t:3h r:25

# --- LOG LOOKUPS ---
# 11. View all chest withdrawals and deposits within 10 blocks from the last 12 hours:
/zd lookup a:container t:12h r:10

# 12. View chat messages sent by a specific player in the last hour:
/zd lookup u:Steve a:chat t:1h

# 13. Search all commands issued within a 20-block radius:
/zd lookup a:command t:2h r:20
```

---

## 🔐 LuckPerms Quick Setup

To make ZenithDefend visible and usable **only by your `admin` group**:

```bash
# Block all non-admins (hides commands and tab completion):
/lp group default permission set zenithdefend.* false

# Grant full access to your admin group:
/lp group admin permission set zenithdefend.* true

# Add yourself as an admin:
/lp user <YourUsername> parent add admin
```

---

## 💬 Support & Contact

Have a question, feature request, or need help configuring the plugin on your server?

* 💬 **Discord:** Contact **@kzen_fights** (Discord User ID: `1275335096924373032`) — feel free to DM me on Discord for support!
* 🐛 **GitHub Issues:** [Issue Tracker](https://github.com/krishnamittal0409-commits/ZenithDefend-Release/issues)
* 📦 **Release Repository:** [ZenithDefend-Release on GitHub](https://github.com/krishnamittal0409-commits/ZenithDefend-Release)

---

## 📄 License

Released under the **GNU General Public License v3.0**. See the [LICENSE](https://github.com/krishnamittal0409-commits/ZenithDefend-Release/blob/main/LICENSE) for details.

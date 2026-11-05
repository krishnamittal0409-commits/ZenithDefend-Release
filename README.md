# ZenithDefend

<p align="center">
  <b>High-Performance Data Logging, Anti-Griefing, and Rollback Engine</b>
  <br />
  <i>Engineered for Paper, Purpur, Folia, and Spigot — Fully playable from <b>Minecraft 1.20 up to 26.3</b>!</i>
</p>

---

## ⚡ Overview

**ZenithDefend** is an enterprise-grade block logger, container transaction tracker, and anti-griefing system built as a modern, high-performance alternative to CoreProtect.

Whether you run a small survival server, an SMP, or a massive network, ZenithDefend provides **lag-free, real-time logging and chunk-batched rollbacks** with zero impact on server tick rates (MSPT).

---

## 🎮 Multi-Version Compatibility

ZenithDefend has dedicated builds tailored for every modern Minecraft generation:

* 🟢 **Minecraft 1.20 Series (`1.20` – `1.20.6`):**
  * Target: **Java 17 LTS**
  * File: `ZenithDefend-1.0.0-MC1.20.jar`
* 🟢 **Minecraft 1.21 Series (`1.21` – `1.21.11`):**
  * Target: **Java 21 LTS**
  * File: `ZenithDefend-1.0.0-MC1.21.jar`
* 🟢 **Minecraft 26 Series (`26.1` – `26.3`):**
  * Target: **Java 25 LTS**
  * File: `ZenithDefend-1.0.0.jar`

**Supported Platforms:** Paper, Purpur, Folia, Spigot, Bukkit.

---

## 🔥 Key Features

* 🔎 **Click Inspector (`/zd i` or `/zenithdefend i`):** Left-click any block to inspect its placement/break history, or right-click any chest, barrel, furnace, or shulker box to view all item deposits and withdrawals.
* ⏪ **Lag-Free Rollback (`/zd rb`):** Chunk-batched rollback engine processes thousands of changes smoothly without server hitching.
* ⏩ **Reversible Restore (`/zd rs`):** Reapply changes or undo previous rollbacks with a single command.
* 📜 **Log Lookup (`/zd l`):** Search block, container, chat, command, and interaction logs with clickable chat pagination (`/zd page <n>`).
* ⚡ **Zero-Lag Async Pipeline:** Dedicated daemon queue batches database transactions asynchronously.
* 🗄️ **Dual Storage Support:** Ultra-fast local SQLite (WAL mode) or external MySQL / MariaDB via HikariCP.
* 🛡️ **Full LuckPerms Integration:** Granular permissions and smart tab-completion that hides commands from unauthorized players.

---

## 🕹️ Command Reference

| Command | Alias | Description | Permission |
| :--- | :--- | :--- | :--- |
| `/zd inspect` | `/zd i` | Toggle click inspection on blocks & containers | `zenithdefend.inspect` |
| `/zd lookup <params>` | `/zd l` | Search logged actions (blocks, containers, chat, commands) | `zenithdefend.lookup` |
| `/zd rollback <params>` | `/zd rb` | Revert griefing within a time/radius/player filter | `zenithdefend.rollback` |
| `/zd restore <params>` | `/zd rs` | Reapply / undo previously rolled back changes | `zenithdefend.restore` |
| `/zd page <number>` | — | Navigate search results with interactive clickable chat buttons | `zenithdefend.lookup` |
| `/zd purge t:<time>` | — | Delete old logs (e.g. `t:30d`, `t:4w`) to free disk space | `zenithdefend.purge` |
| `/zd status` | — | Display live queue, batch size, and database metrics | `zenithdefend.status` |
| `/zd reload` | — | Reload configuration settings from disk | `zenithdefend.reload` |

---

## 🔍 Filter Syntax Examples

* `/zd rollback u:Griefer123 t:2h r:20` — Rollback Griefer123 in a 20-block radius over the last 2 hours.
* `/zd rollback u:#fire t:1d r:50` — Undo fire spread within 50 blocks from the last 24 hours.
* `/zd lookup a:container r:10 t:12h` — Check chest transactions within 10 blocks over the last 12 hours.
* `/zd lookup u:Steve a:chat t:1h` — Search Steve's chat messages from the past hour.

---

## 🛡️ LuckPerms Quick Setup

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

* 💬 **Discord:** [**@kzen_fights (Click to Message)**](https://discord.com/users/1275335096924373032)
* 🐛 **GitHub Issues:** [Issue Tracker](https://github.com/krishnamittal0409-commits/ZenithDefend-Release/issues)
* 💻 **Source Code:** [Private Repository](https://github.com/krishnamittal0409-commits/ZenithDefend)

---

## 📄 License

Released under the **GNU General Public License v3.0**. See the [LICENSE](LICENSE) file for details.

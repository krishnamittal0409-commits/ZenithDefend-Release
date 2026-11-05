# ZenithDefend

<p align="center">
  <b>Enterprise Data Logging, Anti-Griefing, and Rollback Engine</b><br>
  <i>Built for Paper, Purpur, Folia, and Spigot — Supporting Minecraft <b>1.20 through 26.3</b></i>
</p>

---

> 🏆 **Daily Gold:** ZenithDefend is engineered as a daily gold-standard anti-grief system—rock-solid, zero-tick lag, and maximum reliability. Whether you run a private SMP or a massive high-traffic network, this plugin is completely plug-and-play and ready for action.
>
> 💬 **Need Help or Found an Issue?** Have questions, suggestions, or need support? Direct Message me on Discord: **`@kzen_fights`**

---

## 🎮 Multi-Version Compatibility (1.20 – 26.3)

ZenithDefend is fully playable and tested across all modern Minecraft versions. Dedicated builds are provided to match your server's exact Java runtime and eliminate class-version errors:

| Minecraft Version Range | Supported Patch Versions | Java Runtime | Recommended Download |
| :--- | :--- | :---: | :--- |
| **Minecraft 1.20.x** | `1.20`, `1.20.1`, `1.20.2`, `1.20.3`, `1.20.4`, `1.20.5`, `1.20.6` | **Java 17 LTS+** | `ZenithDefend-1.0.0-MC1.20.jar` |
| **Minecraft 1.21.x** | `1.21`, `1.21.1`, `1.21.2`, `1.21.3`, `1.21.4`, `1.21.5`, `1.21.6`, `1.21.7`, `1.21.8`, `1.21.9`, `1.21.10`, `1.21.11` | **Java 21 LTS+** | `ZenithDefend-1.0.0-MC1.21.jar` |
| **Minecraft 26.x** | `26.1`, `26.2`, `26.3` | **Java 25 LTS+** | `ZenithDefend-1.0.0.jar` |

*Full native support for **Paper**, **Purpur**, **Folia**, **Spigot**, and **Bukkit**.*

---

## ⚡ What Makes ZenithDefend Special?

* **Click Inspector (`/zd i` or `/zd inspect`)**: Left-click to inspect block placement/break history. Right-click to inspect container transactions (chests, double chests, barrels, hoppers, furnaces, shulker boxes, dispensers, droppers, and chiseled bookshelves).
* **Lag-Free Rollback (`/zd rb`) & Restore (`/zd rs`)**: Executes changes in chunk-aware tick batches via Paper's region schedulers to prevent main-thread tick spikes (MSPT).
* **Interactive Log Lookup (`/zd l`)**: Search block, container, chat, command, and interaction records with clickable Adventure MiniMessage pagination (`/zd page <n>`).
* **High-Performance Async Pipeline**: Zero-lag asynchronous queue using HikariCP connection pooling for SQLite (WAL mode) and MySQL/MariaDB.
* **100% LuckPerms Native**: Granular permission tree (`zenithdefend.*`, `zenithdefend.inspect`, etc.) with permission-filtered tab suggestions.

---

## 📥 Installation

1. Download the build matching your server version from the table above or the **Versions** tab.
2. Drop the `.jar` into your server's `plugins/` directory.
3. Restart your server. ZenithDefend will automatically generate `plugins/ZenithDefend/config.yml` and initialize the database.

---

## 🛠️ Commands & Permissions

ZenithDefend supports both **`/zd`** and **`/zenithdefend`** interchangeably:

| Command | Shorthand | Description | Permission |
| :--- | :--- | :--- | :--- |
| `/zd inspect` | `/zd i` | Toggle click inspection on blocks & containers | `zenithdefend.inspect` |
| `/zd lookup <params>` | `/zd l` | Search logged actions (blocks, containers, chat, commands) | `zenithdefend.lookup` |
| `/zd rollback <params>` | `/zd rb` | Rollback griefing actions with user/time/radius filters | `zenithdefend.rollback` |
| `/zd restore <params>` | `/zd rs` | Reapply / undo previously rolled back modifications | `zenithdefend.restore` |
| `/zd page <number>` | — | Navigate search pages with interactive chat buttons | `zenithdefend.lookup` |
| `/zd purge t:<time>` | — | Purge old logs (e.g. `t:30d`, `t:12w`) and reclaim disk space | `zenithdefend.purge` |
| `/zd status` | — | Display live database connection & queue metrics | `zenithdefend.status` |
| `/zd reload` | — | Reload configuration settings from disk | `zenithdefend.reload` |

---

## 🔍 Filter Parameter Syntax

Use parameters in `/zd lookup`, `/zd rollback`, and `/zd restore`:

* **`u:<user>`** — Target specific players or causes (e.g. `u:Griefer`, `u:#fire`, `u:#tnt`, `u:#water`).
* **`t:<time>`** — Time filter (e.g. `t:30s`, `t:15m`, `t:2h`, `t:7d`, `t:4w`).
* **`r:<radius>`** — Block radius around you (e.g. `r:15`, `r:50`, `r:#world`, `r:#global`).
* **`a:<action>`** — Action filter (`+block`, `-block`, `container`, `click`, `kill`, `chat`, `command`).
* **`b:<blocks>`** — Filter by specific blocks (e.g. `b:tnt,lava,diamond_block`).
* **`e:<exclude>`** — Exclude specific blocks.

*Quick Examples:*
```bash
/zd rollback u:Griefer123 t:2h r:20
/zd rollback u:#fire t:1d r:50
/zd lookup a:container r:10 t:12h
/zd lookup u:Steve a:chat t:1h
```

---

## 💬 Community & Support

* **Discord:** Direct message **`@kzen_fights`** for questions, feature requests, or bug reports.
* **GitHub Issues:** [github.com/krishnamittal0409-commits/ZenithDefend-Release/issues](https://github.com/krishnamittal0409-commits/ZenithDefend-Release/issues)

---

## 📄 License

ZenithDefend is licensed under the **GNU General Public License v3.0**.

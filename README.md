# ZenithDefend

<p align="center">
  <b>High-Performance Data Logging, Anti-Griefing, and Rollback Engine for Paper 26.3</b>
  <br />
  <i>Engineered for modern Minecraft servers running on Java 25.</i>
</p>

---

## ⚡ Overview

**ZenithDefend** is an enterprise-grade block logger, container transaction tracker, and anti-griefing system built from scratch to serve as a high-performance alternative to CoreProtect for **Paper 26.3**.

By leveraging Paper's modern asynchronous and region-aware scheduling architectures, HikariCP connection pooling, and optimized dictionary caching, ZenithDefend logs thousands of block and container actions per second with **zero impact on server MSPT (tick performance)**.

---

## 📥 Download & Installation

1. Download **`ZenithDefend-1.0.0.jar`** from the root of this repository or from the [Releases](../../releases) tab.
2. Ensure your server is running **Paper 26.3** on **Java 25 LTS** (or newer).
3. Place `ZenithDefend-1.0.0.jar` into your server's `plugins/` folder.
4. Restart the server. ZenithDefend will automatically generate `plugins/ZenithDefend/config.yml` and initialize its database.

---

## 🎮 Commands & Aliases

ZenithDefend provides dual top-level commands: **`/zd`** and **`/zenithdefend`**.

| Command | Alias | Description | Permission |
| :--- | :--- | :--- | :--- |
| `/zd inspect` | `/zd i` | Toggle click inspection on blocks & containers | `zenithdefend.inspect` |
| `/zd lookup <params>` | `/zd l` | Search logged actions (blocks, containers, chat, commands) | `zenithdefend.lookup` |
| `/zd rollback <params>` | `/zd rb` | Rollback griefing actions within a time/radius/player filter | `zenithdefend.rollback` |
| `/zd restore <params>` | `/zd rs` | Reapply / undo previously rolled back changes | `zenithdefend.restore` |
| `/zd page <number>` | — | Navigate search results with interactive clickable chat buttons | `zenithdefend.lookup` |
| `/zd purge t:<time>` | — | Delete old logs (e.g. `t:30d`, `t:4w`) to free disk space | `zenithdefend.purge` |
| `/zd status` | — | Display live queue, batch size, and database metrics | `zenithdefend.status` |
| `/zd reload` | — | Reload configuration settings from disk | `zenithdefend.reload` |

---

## 🔍 Query Parameters

Parameters can be passed to `/zd lookup`, `/zd rollback`, and `/zd restore`:

* **`u:<user>`** — Target specific players or causes (e.g. `u:Notch`, `u:#fire`, `u:#tnt`, `u:#water`).
* **`t:<time>`** — Time filter (e.g. `t:30s`, `t:15m`, `t:2h`, `t:7d`, `t:4w`).
* **`r:<radius>`** — Block radius around your position (e.g. `r:15`, `r:50`, `r:#world`, `r:#global`).
* **`a:<action>`** — Filter by action:
  * `a:+block` (placements)
  * `a:-block` (breakages)
  * `a:container` (chest/container transactions)
  * `a:click` (doors, levers, buttons, lecterns)
  * `a:kill` (entity and animal kills)
  * `a:chat` (player chat messages)
  * `a:command` (executed commands)
* **`b:<blocks>`** — Filter by specific materials (e.g. `b:tnt,lava,diamond_block`).
* **`e:<exclude>`** — Exclude specific materials.

*Examples:*
```bash
/zd rollback u:Griefer123 t:2h r:20
/zd rollback u:#fire t:1d r:50
/zd lookup a:container r:10 t:12h
/zd lookup u:Steve a:chat t:1h
```

---

## 🛡️ LuckPerms Compatibility

ZenithDefend integrates natively with **LuckPerms** and Bukkit's permission system:

* `zenithdefend.*` — Grants access to all commands (default: OP).
* `zenithdefend.use` — Base permission to run `/zd`.
* `zenithdefend.inspect` — Permission to toggle `/zd i`.
* `zenithdefend.lookup` — Permission to use `/zd lookup` and `/zd page`.
* `zenithdefend.rollback` — Permission to run `/zd rollback`.
* `zenithdefend.restore` — Permission to run `/zd restore`.
* `zenithdefend.purge` — Permission to purge database logs.
* `zenithdefend.status` — Permission to view performance status.
* `zenithdefend.reload` — Permission to reload `config.yml`.

> **Smart Tab Completion:** Tab suggestions dynamically filter according to the sender's LuckPerms permissions. Unauthorized commands are never suggested.

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

## 📄 License

This distribution is released under the **GNU General Public License v3.0**. See the [LICENSE](LICENSE) file for full details.

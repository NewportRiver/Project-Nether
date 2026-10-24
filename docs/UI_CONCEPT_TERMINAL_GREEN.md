# Project Nether — Green Phosphor Terminal Concept

**Approved visual reference:** Android portrait screenshot supplied by project owner on 2026-10-24. The screenshot is a *design reference*, not evidence of a deployed application.

## Visual contract
- Text-only Linux/Termux/SSH terminal user interface; **no graphical widgets, image backgrounds, pixel art, HTML or GUI**.
- Black background (#000000), exclusively green foreground (#00FF40 or terminal ANSI green); no other text colors.
- Monospaced font and character-cell alignment; terminal-safe ASCII (`+`, `-`, `|`, `=`, `~`, `*`, `#`).
- Responsive portrait layout; narrow terminal widths must stack sections rather than clip content.
- ASCII title THE NETHER, small ASCII portal, keyboard menu, command prompt.
- Render real telemetry only when connected; **clearly label all sample counts, IPs and services as DEMO**.
- No artificial decorations that cannot be printed in a terminal.

## Required screens
1. **Overview:** banner, company attribution, portal, status, honeypot realm, live connections, warden, attack types, menu.
2. **Honeypots:** service name, port, status, session count.
3. **Connections:** timestamp, sanitized source IP, service, event, session reference.
4. **Attack logs:** filterable read-only evidence list.
5. **Intelligence:** evidence-linked Warden summaries.
6. **Analytics:** character-only histograms and tables.
7. **Nether Warden:** task state, recent classifications, humorous optional commentary.
8. **Settings:** theme toggle (default green), refresh rate, demo/live mode, data retention; no unsafe network changes.

## Layout prototype
```text
nether@architect1:~$ ./nether
+--------------------------------------------------+
|                  THE NETHER                      |
|                  PROJECT NETHER                  |
|              Newport River Company               |
|        OBSERVE * ANALYZE * CONTAIN * LEARN       |
+--------------------------------------------------+
                  THE NETHER PORTAL
                    +-----------+
                    | ~ * ~ * ~ |
                    | * ~ * ~ * |
                    | ~ * ~ * ~ |
                    | * ~ * ~ * |
                    +-----------+
                     /#########\
                    /___________\
             "Another connection enters..."
+--------------------------------------------------+
| NETHER STATUS                      [DEMO ONLINE] |
+--------------------------------------------------+
| Honeypots Active: 8    Active Traps: 12          |
| Nether Watchers: 3     Connections 24h: 1,284    |
+--------------------------------------------------+
| HONEYPOT REALM (DEMO)                            |
| SSH:22 [OK]  FTP:21 [OK]  HTTP:80 [OK]           |
| MySQL:3306 [OK]  RDP:3389 [OK]                   |
+--------------------------------------------------+
| LIVE CONNECTIONS (DEMO)                          |
| 11:04:12 192.0.2.14     SSH  Failed login       |
| 11:04:15 198.51.100.8   HTTP GET /wp-admin/     |
+--------------------------------------------------+
| NETHER WARDEN                                    |
|    [::]   [OK] Collecting telemetry             |
|   /|##|\  [OK] Identifying scanners             |
|    /  \   [..] Brewing coffee                   |
| WARDEN: "Another bot? Seriously?"                |
+--------------------------------------------------+
| [1] Map [2] Honeypots [3] Connections [4] Logs   |
| [5] Intel [6] Analytics [7] Warden [8] Settings  |
| [Q] Quit                                         |
+--------------------------------------------------+
A safer internet through better observation...
              and a few good traps.
nether@architect1:~$ _
```

## Implementation guidance
Python Textual or curses for terminal rendering; ANSI green monochrome palette. Do not require a GPU, browser, or desktop session. Make keyboard shortcuts and screen-reader-friendly log views work over SSH. Simulated counts must never masquerade as production telemetry.

## Acceptance criteria
- Renders in Android Termux, Ubuntu WSL and standard SSH terminals.
- Monochrome green foreground on black throughout.
- No overflow at 55, 65 and 80 terminal columns.
- Terminal-resize and connection-loss behavior tested.
- ASCII art is literal printable text, not image assets.
- Status and evidence distinguish DEMO from LIVE.

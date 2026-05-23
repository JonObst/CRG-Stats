# CRG Bout Stats

A real-time roller derby bout statistics dashboard that connects directly to a [CRG Scoreboard](https://github.com/rollerderby/scoreboard) instance via WebSocket and displays live jammer, pivot, and blocker stats as the game unfolds.

![Jammers tab](jammer.png)

![Blockers tab](blocker.png)

## Features

- **Live connection** to CRG via WebSocket — no server required, runs as a single HTML file
- **Jammers tab** — lead percentage, points for/against, track time, penalty count, star passes given; initial trip indicator and IN BOX status on the active jammer
- **Star pass pivot section** — points scored after receiving the star, track time as jammer, passed-from breakdown
- **Blockers tab** — jams played, pivot jams, track time, penalty count
- **Live score bar** — current score, jam clock (interpolated), period clock, lead indicator, power jam alert, active jammer name
- **Clock states** — correctly displays JAM / LINEUP / TIMEOUT / INTERMISSION with the appropriate countdown
- **Jersey color theming** — reads `AlternateName(operator)` from CRG and tints each team panel accordingly
- **Derby number sort** — skaters sorted in standard derby order (string sort preserving leading zeros)
- **Active skater indicators** — arrow markers on current jam's jammer, pivot (post star pass), and all four blockers; clears automatically between jams
- **Game transition handling** — detects new game via `ScoreBoard.CurrentGame` and resets stats automatically
- **Auto-connect** — supports URL hash for bookmarkable connections: `crg-jammer-stats.html#192.168.1.100:8000`

## Usage

1. Copy `crg-jammer-stats.html` into the CRG `html` folder on the scoreboard machine
2. Open `http://<CRG-IP>:8000/crg-jammer-stats.html` from any machine on the same network
3. Enter the CRG IP:port in the connection bar and click Connect

Or bookmark with auto-connect: `http://<CRG-IP>:8000/crg-jammer-stats.html#<CRG-IP>:8000`

## Requirements

- CRG Scoreboard v2025.x (tested on v2025.9)
- Any modern browser on the same network as the CRG machine
- No build step, no dependencies, no server

## Notes

- Must be served over HTTP (not opened as a local `file://`) so the browser allows the WebSocket connection
- The CRG machine's Jetty server handles this automatically when the file is placed in the `html` folder
- Track time reflects jam clock time only (not lineup time)
- Star pass splits track time between jammer and pivot at the moment of the pass

## License

GPL-3.0 — see [LICENSE](LICENSE) for details.

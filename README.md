# iChess — Modern Web Chess Workspace

> Minimalist Stockfish engine & PGN workspace that runs entirely in the browser.

**Live site:** [https://ishatxt.github.io/chess/](https://ishatxt.github.io/chess/)

iChess is a client-side chess platform built around the Stockfish engine. It ships as a collection of static HTML pages with zero build step and no backend — every feature runs locally in your browser. Play the engine with calibrated Elo strength, challenge chess legends, import real games from Chess.com or Lichess, train tactics, and export your games as PGN, image, or animated GIF.

---

## Table of Contents

- [Features](#features)
- [Bots & Legends](#bots--legends)
- [Pages](#pages)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Acknowledgements](#acknowledgements)
- [License](#license)

---

## Features

### Play Chess

Play against Stockfish with a fully adjustable engine rating:

- **Engine Elo** — Slide from 100 to 3700. Low ratings deliberately blunder and play shallow searches; maximum rating plays at full `Skill Level 20`.
- **Time controls** — 30s bullet up to 2h classical, plus increment of 0s to +10s, or unlimited.
- **Play either side** — Choose White or Black.
- **Hint** — Query Stockfish for a suggested move with the current position highlighted.
- **Play Best** — Instruct the engine to play the best move in any position.
- **Live evaluation bar** — Real-time centipawn evaluation beside the board.
- **Opening detection** — Current opening name is identified from an embedded ECO dictionary.
- **Move log** — Full notation history with navigation (first / prev / next / last).
- **Capture tracking** — Captured material displayed per player.
- **Clocks** — Per-player chess clocks with move and capture sounds.
- **FEN import** — Load any position to practice puzzles or studies.
- **Share & export** — Export the game as PGN, download a static board image (PNG), or generate an animated replay GIF of all moves.

#### Game export

| Format | Description |
| --- | --- |
| PGN | Full Portable Game Notation plus FEN string |
| PNG | Board image rendered from the current position |
| GIF | Animated replay of every move played in the game |

### Coach

A training-oriented mirror of the game page focused on practice:

- Engine games with adjustable Elo and clock controls.
- Undo, flip, copy PGN, copy FEN, and load FEN positions.
- Hint and Play Best modes for studying rather than competing.

### PGN Workspace

Inspect imported games without playing:

- **Paste PGN** — Import game notation from Chess.com or Lichess.
- **Player metadata** — Parses player names, chess titles (GM, IM, FM, WGM, etc.), and ELO ratings from PGN headers.
- **Step-through playback** — Move-by-move navigation with an interactive move tree.
- **Board flip** and move/capture sounds.
- **Board annotations** — Right-drag to draw arrows on the board for analysis.

### Rated Puzzles (Under development)

- Fetches live tactics from Lichess's public puzzle API, including the daily puzzle.
- Puzzles are filtered by theme and chosen with checkmate patterns preferred.
- Displays puzzle ID, rating, and theme tags.
- Falls back to an offline checkmate database when the network is unavailable.

### Analyze Game (Under development)

Full position analysis backed by real-time Stockfish calculations with a win-evaluation bar. Accessible via `game.html?mode=analyze`.

### Boards

- Alternate board theme shipped under `features/` (`colour` and `wood`).

---

## Bots & Legends

Each bot is a personality profile that styles a Stockfish instance with a signature rating, search depth, and a higher level of deliberate blunders for authentic play.

| Bot | Title | Style | Rating |
| --- | --- | --- | --- |
| Ishan | The Code Architect | Precision calculation, sound positional play, bulletproof execution | 2800 |
| Bobby Fischer | The World Champion | Relentless tactics, uncompromising pursuit of the win | 2785 |
| Alexander Alekhine | The Tactical Genius | Complex, aggressive attacks, unorthodox maneuvers | 2750 |
| José Raúl Capablanca | The Human Chess Machine | Clear positional intuition, flawless endgames | 2725 |
| Emanuel Lasker | The Psychological Master | Practical play, traps, tenacious defense | 2700 |
| Mikhail Tal | The Magician from Riga | Aggressive piece sacrifices, king hunts, chaos | 2700 |
| Paul Morphy | The Pride and Sorrow of Chess | Lightning development, romantic sacrifices | 2680 |

---

## Tech Stack

- **Stockfish.js 10.0.2** — UCI chess engine running as a Web Worker.
- **chess.js 0.10.3** — move validation and game state.
- **chessboard.js 1.0.0** — interactive board UI.
- **jQuery 3.6.0** — DOM helpers and event wiring.
- **Font Awesome 6** — iconography.
- **Google Fonts (Noto Sans / Roboto Mono)** — typography.
- **Lichess assets** — official move/capture/check sounds and open puzzle database.
- **No build step** — plain HTML/CSS/JavaScript delivered as static files.

---

## Project structure

```
chess/
├── index.html              # Landing dashboard
├── game/
│   └── game.html           # Play vs Stockfish (share/export, clocks, eval bar)
├── coach/
│   └── coach.html          # Training mode with undo and position import
├── bots/
│   ├── bots.html           # Bot selection dashboard
│   ├── tal.html            # Per-bot engine configuration pages
│   ├── morphy.html
│   ├── capablanca.html
│   ├── alekhine.html
│   ├── lasker.html
│   ├── bobby.html
│   ├── ishan.html
│   └── botpfp/             # Bot profile pictures
├── pgn/
│   └── pgn.html            # PGN paste, metadata, and playback
├── puzzle/
│   └── puzzle.html         # Rated puzzles (Lichess-backed)
├── features/
│   ├── colour              # Alternate board theme
│   └── wood.html           # Wood board theme
```

---

## Getting Started

The project contains no dependencies to install or build step to run. It is a set of static pages served as-is.

### Option 1 — Open locally

Clone the repository and open `index.html` in your browser:

```bash
git clone https://github.com/ishatxt/chess.git
cd chess
open index.html   # macOS
xdg-open index.html  # Linux
```

### Option 2 — Local server (recommended)

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

### Option 3 — Deploy to GitHub Pages

Push the repository and enable **GitHub Pages** from the repository settings, pointing the source branch to `main`. The site is then available at:

```
https://<your-username>.github.io/chess/
```

---

## Acknowledgements

- [Stockfish](https://stockfishchess.org/) — the chess engine powering gameplay and analysis.
- [chess.js](https://github.com/jhlywa/chess.js) and [chessboard.js](https://chessboardjs.com) — core board mechanics.
- [Lichess](https://lichess.org) — sounds, puzzle API, and the open gameplay standard.

---

## License

Distributed under the MIT License.
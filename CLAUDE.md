# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Single-file browser game — no build step, no dependencies, no package manager. Open `tictactoe.html` directly in any browser to run.

## Running the Game

```bash
open tictactoe.html        # macOS
```

## Architecture

Everything lives in one file (`tictactoe.html`) with three sections:

- **CSS** (`<style>`) — dark theme, grid layout, per-player colors (X = blue `#60a5fa`, O = pink `#f472b6`), state classes (`.taken`, `.win-cell`, `.win`, `.draw`)
- **HTML** — static 9-cell grid (`data-i="0"` through `data-i="8"`), score display, status bar
- **JavaScript** (`<script>`) — all game logic; no frameworks

### Key JS patterns

| Symbol | Purpose |
|--------|---------|
| `WINS` | Hardcoded array of all 8 winning index triples |
| `board[]` | 9-element array mirroring the DOM grid; `''`, `'X'`, or `'O'` |
| `scores` | `{ X, O, D }` object — persists across `init()` calls |
| `init()` | Resets `board`, `current`, `over`, and all cell DOM state — does **not** reset scores |
| `checkWin()` | Iterates `WINS`; returns winning triple or `null` |
| `updateScore()` | Pushes `scores` values into the three `#score-*` DOM elements |

Cell clicks are handled via a single `forEach` listener attached at page load.

## GitHub Workflow

- Repo: `https://github.com/MrKief18/tic-tac-toe`
- Before starting new projects: create a GitHub repo, commit with comments, and push (`gh repo create` — CLI is authenticated as `MrKief18`)
- Add inline comments to all code for readability and easy reverting

# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a single-file browser-based Tic Tac Toe game (`tictactoe.html`). The UI language is Indonesian (Bahasa Indonesia). No build step, no dependencies, no package manager.

## Running the App

Open `tictactoe.html` directly in a browser. There is no server, compilation, or install step.

## Git Workflow

After completing any meaningful unit of work — a feature, a fix, a refactor — commit and push to GitHub immediately. Never let work accumulate uncommitted.

Commit message format: short imperative subject line (under 60 chars), e.g. `Add win animation highlight` or `Fix draw detection on full board`. No period at the end of the subject.

```bash
git add <files>
git commit -m "Your message here"
git push
```

## Architecture

Everything lives in `tictactoe.html` — inline CSS, inline JavaScript, and HTML markup in one file.

**State model** (`tictactoe.html:204–207`):
- `board`: 9-element array of `''`, `'X'`, or `'O'`
- `current`: active player (`'X'` or `'O'`)
- `gameOver`: boolean flag
- `scores`: object tracking wins per player and draws

**Win detection** (`checkWinner`, line 209): iterates the 8 hardcoded winning lines in `WINS`. Returns `{ winner, line }` for a win, `{ winner: 'draw' }` for a full board, or `null` if the game continues.

**CSS conventions**: dark theme using three accent colors — `#e94560` (red, player X), `#4fc3f7` (blue, player O), `#a8a8b3` (grey, neutral/draw). The `.win` class triggers the pulse animation on winning cells.

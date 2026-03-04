# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A collection of standalone browser-based mini projects — each is a single self-contained HTML file with no build step, no dependencies, and no server required. Open any file directly in a browser.

## Running a Project

```bash
start <filename>.html        # Windows: opens in default browser
```

## Git & GitHub Workflow

The repo is at **https://github.com/Dazzeee/claude-code-test**. After every meaningful change:

```bash
git add <file>
git commit -m "Short imperative description of the change"
git push
```

Commit one logical change at a time with a clean message. Always push after committing so GitHub stays in sync.

## Architecture Pattern

Every project follows the same structure inside a single `.html` file:

1. **`<style>`** — all CSS inline; dark theme palette rooted in `#1a1a2e` background
2. **`<body>`** — minimal semantic HTML; layout via flexbox
3. **`<script>`** — all logic inline; no frameworks, no imports

### Visual Conventions
- Background: `#1a1a2e` (deep navy)
- Accent / interactive: varies per project but uses high-contrast colors against the dark base
- Font: `'Segoe UI', sans-serif`
- Buttons: rounded (`border-radius: 6–8px`), hover state with `transform: scale(1.05)`

### Canvas Projects (`bouncing-ball.html`)
- Fixed-size `<canvas>` element inside a `#container` div
- Game loop driven by `requestAnimationFrame`
- Physics constants (`GRAVITY`, `DAMPING`, etc.) defined as `const` at the top of the script for easy tuning
- `init(x, y)` resets state; `render()` is the single animation entry point

### DOM Game Projects (`tictactoe.html`)
- State held in plain JS variables (array for board, primitives for current player/scores)
- Single `init()` function resets all state and DOM
- Event listeners attached once at load; guards (`if (over || board[i]) return`) prevent invalid moves

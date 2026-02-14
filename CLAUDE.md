# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Interactive Valentine's Day web app: an envelope animation opens into a 3x3 sliding puzzle, which reveals a romantic message and celebratory confetti on completion. Single-file application (index.html) with no build system, package manager, or external dependencies.

## Development

No build step. Open `index.html` directly in a browser or deploy via GitHub Pages. No tests or linting configured.

## Architecture

Everything lives in **index.html** — embedded CSS (lines ~7-605), HTML structure (lines ~606-654), and JavaScript (lines ~655-827).

**Stage-based flow:**
1. **Envelope stage** (`#envelopeStage`) — 3D flip animation on click, transitions to puzzle
2. **Puzzle stage** (`#puzzleView`) — 3x3 sliding tile puzzle with `EMPTY_PIECE = 3` (top-right)
3. **Reveal** — completed puzzle shows full image overlay + completion text
4. **Success** (`#successView`) — confetti animation + celebratory GIF

**Puzzle state** is a flat array (`currentState[0..8]`) mapping grid positions to tile numbers (1-9). Tile 3 is the empty space during play. Scrambling performs 10 random valid moves from the solved state to guarantee solvability. `isPuzzleSolved()` checks exact array match against `solution`.

**Assets:** `images/tile-1.png` through `tile-9.png` (puzzle pieces), `images/full-image.png` (reveal overlay), `giphy.gif` (success celebration).

## Customization

- Greeting text: search for "Dear Gaby" in HTML
- Completion text: search for "you complete me" and "Will you be my Valentine"
- Images: replace tile PNGs and full-image.png (use a 3x3 grid splitter)

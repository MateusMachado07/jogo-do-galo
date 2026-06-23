# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

This repository contains a single self-contained file, `index.html`, implementing "Jogo do Galo" (Portuguese for Tic-Tac-Toe). There is no build system, package manager, dependencies, or test suite — all HTML, CSS, and JavaScript live inline in the one file.

## Running the game

Open `index.html` directly in a browser. No build or install step is required.

## Architecture

All logic is in the `<script>` block of `index.html`:

- `board` is a flat array of 9 cells (`null`, `'X'`, or `'O'`); `WIN_LINES` lists the index triples that count as a win.
- `handleMove(index)` mutates `board`, re-renders, and checks for a win or draw via `checkWinner`.
- `render()` syncs the 9 button elements (`cells`) with the `board` array state (text, `x`/`o`/`win` classes, disabled state).
- The reset button reinitializes `board`/`currentPlayer`/`gameOver` and re-enables all cells.

Since everything is in one file with no modules, changes to game logic, styling, and markup all happen in the same place — there is no separation to preserve across files.

## Git / GitHub sync

This repo is tracked in git and pushed to https://github.com/MateusMachado07/jogo-do-galo (`origin`, branch `master`).

A project-scoped `PostToolUse` hook (`.claude/settings.json`, matcher `Write|Edit`) automatically runs `git add -A && git commit -m "Auto-commit: update files" && git push origin HEAD` after every file write/edit in this project. It no-ops cleanly if there is nothing to commit. This means every modification made via Claude Code in this directory is committed and pushed to GitHub automatically — no manual `git add`/`commit`/`push` step is needed or expected.

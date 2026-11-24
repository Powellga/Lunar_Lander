# Lunar Lander Game

This file provides guidance to Claude Code when working with code in this repository.

## Project

**Lunar Lander Game**

## Working Directory

`C:/Users/gregg/Claude-Code-IDE-Workspaces/lunar-lander-game`

## Project Context Log

Claude: this section is the project's persistent memory, loaded at the start
of every session. Whenever durable project facts change during a session -
decisions made, architecture added or changed, key files, external resources
or IDs, constraints, blockers, milestones reached - update this section in
that same session, without being asked. Keep it a compact rolling summary:
fold in new facts, prune what is obsolete. Do not log routine activity.

- Repo: GitHub `Powellga/Lunar_Lander` (public, branch `main`), cloned into this
  IDE folder 2026-11-24. An older clone also sits at `C:\Users\gregg\_readme_work\Lunar_Lander`.
- Live: https://powellga.github.io/Lunar_Lander/ via GitHub Pages (legacy build from
  `main` /). Pushing to `main` IS the deploy; Pages rebuilds in about a minute.
- Whole game is one file, `index.html` (vanilla JS + canvas, no build, no deps).
- 2026-11-24: made mobile playable. Canvas stays 800x600 internally, CSS-scaled by
  `layout()`; on-screen pointer-event buttons (rotate left/right, THRUST, multi-touch);
  tap game to start/restart (600 ms lockout after a round ends); physics on a fixed
  60 steps/s accumulator so 120 Hz phones don't run fast.
- Testing: Playwright lives in `C:\Users\gregg\_____PYTHON_PROJECTS\Claude_Browser_MCP_Server\.venv`
  (system Python has none); use it with `p.devices["iPhone 13"]` etc. for mobile emulation.

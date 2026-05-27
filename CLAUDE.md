# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

這是一個學生自主多元學習專案（Student Self-Directed Learning）。
倉庫存放純 HTML + CSS + JS 的小遊戲，以手機瀏覽器展示為主要目標。
無後端、無框架、無建構工具——所有遊戲均為靜態頁面，可直接在瀏覽器開啟。

## Running & Previewing

Since there is no build step, open any game's `index.html` directly in a browser, or use a local static server to avoid cross-origin issues when loading assets:

```powershell
# Python (quick local server, run from the repo root or a game subfolder)
python -m http.server 8080

# Node (if npx is available)
npx serve .
```

Then open `http://localhost:8080` on desktop or connect a phone to the same network and visit `http://<your-local-ip>:8080`.

## Repository Structure Convention

Each mini-game lives in its own subfolder:

```
/
├── <game-name>/
│   ├── index.html   # entry point
│   ├── style.css
│   └── script.js
└── index.html       # optional hub / game selector page
```

Keep each game self-contained inside its folder — no shared dependencies between games.

## Mobile-First Constraints

- Target viewport: 375–430 px wide (iPhone / mid-range Android).
- Always include `<meta name="viewport" content="width=device-width, initial-scale=1">`.
- Use touch events (`touchstart`, `touchend`) or Pointer Events; do not rely solely on `click` for game controls.
- Avoid hover-only interactions.
- Test landscape orientation if the game benefits from it.

## Code Style

- Vanilla JS only — no npm packages, no bundler, no TypeScript.
- CSS: prefer `rem`/`vh`/`vw` units; avoid fixed pixel layouts.
- Keep each game's JS in a single `script.js` (or inline `<script>`) for simplicity.

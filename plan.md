# Mesos Game – Web App Implementation Plan

A todo list of tasks to build the Mesos football game as an offline-capable web app that two players (or one player vs. AI) can play locally on the same machine.

---

## 1. Project Setup
- [ ] Initialise a new project with `npm init` (or use a lightweight bundler such as Vite)
- [ ] Choose a tech stack: vanilla HTML/CSS/JavaScript (no build step) or React/Vue for component-based UI
- [ ] Set up a folder structure:
  ```
  /src
    /assets        ← sprites, fonts, sounds
    /css           ← stylesheets
    /js
      game.js      ← main game loop
      board.js     ← board / pitch state
      ai.js        ← AI opponent logic
      ui.js        ← DOM helpers / rendering
  index.html
  plan.md
  README.md
  ```
- [ ] Add a `package.json` with a `start` script that serves the app locally (e.g. `npx serve .` or `vite`)
- [ ] Configure a `.gitignore` to exclude `node_modules/`, `dist/`, etc.

---

## 2. Game Rules & Design Document
- [ ] Document the official Mesos rules (board dimensions, pieces, win conditions, valid moves)
- [ ] Document turn structure and any time-limit rules
- [ ] Decide on game variants to support (1-player vs AI, 2-players on same machine)
- [ ] Sketch a wireframe / mockup of the game board UI

---

## 3. Core Game Logic
- [ ] Implement the game board data structure (grid / graph representation of the pitch)
- [ ] Implement piece / ball movement rules
- [ ] Implement turn management (whose turn it is, switching turns)
- [ ] Implement win / draw / end-of-game detection
- [ ] Implement move validation (legal vs. illegal moves)
- [ ] Write unit tests for all core game-logic functions

---

## 4. AI Opponent
- [ ] Implement a simple random-move AI (baseline)
- [ ] Implement a smarter AI using minimax or alpha-beta pruning
- [ ] Add difficulty levels (Easy / Medium / Hard)
- [ ] Expose an `ai.getBestMove(boardState)` function used by the game loop

---

## 5. User Interface (HTML/CSS)
- [ ] Create `index.html` shell with game container
- [ ] Design and style the football pitch / game board with CSS
- [ ] Render game pieces / ball on the board (SVG or canvas, or styled `<div>`s)
- [ ] Highlight valid moves when a piece is selected
- [ ] Show current player / turn indicator
- [ ] Add score / result display
- [ ] Add a "New Game" / restart button
- [ ] Add a mode-selection screen (vs AI / vs Local Player)
- [ ] Add difficulty selector for AI mode
- [ ] Make the layout responsive so it fits common screen sizes

---

## 6. Game Loop & Interaction
- [ ] Wire up click / tap events on the board to `game.js`
- [ ] Handle piece selection → valid-move highlighting → move execution flow
- [ ] Integrate AI turn: after human moves, trigger AI move automatically
- [ ] Animate piece / ball movement (CSS transition or `requestAnimationFrame`)
- [ ] Play sound effects on move, goal, and game-over events (optional)

---

## 7. Offline / Local-Machine Support
- [ ] Ensure the entire app runs from the file system or a `localhost` server with **no** external network requests
- [ ] Bundle or inline all assets (fonts, images, sounds) so no CDN is required
- [ ] Add a `Service Worker` (`sw.js`) to cache assets for full offline support
- [ ] Register the Service Worker in `index.html`
- [ ] Test that the app loads and plays correctly with the network disabled
- [ ] (Optional) Add a Web App Manifest (`manifest.json`) so the app can be installed as a PWA

---

## 8. Persistence & Settings
- [ ] Save game state to `localStorage` so an in-progress game survives a page refresh
- [ ] Save player preferences (difficulty, sound on/off) to `localStorage`
- [ ] Add a "Resume Game" option on start if a saved game exists

---

## 9. Testing & Quality Assurance
- [ ] Set up a test runner (e.g. Vitest or Jest)
- [ ] Write unit tests for board state, move validation, and win detection
- [ ] Write integration tests for the full game flow (move → AI response → win check)
- [ ] Manually play through several games to verify correctness
- [ ] Cross-browser test: Chrome, Firefox, Safari, Edge
- [ ] Test on mobile viewport (touch events)

---

## 10. Documentation & Polish
- [ ] Update `README.md` with:
  - How to run the app locally (`npm start` or open `index.html`)
  - How to play (rules summary)
  - Screenshots or a GIF demo
- [ ] Add inline code comments for complex logic (AI, move validation)
- [ ] Add a `CONTRIBUTING.md` if open-source contributions are expected
- [ ] Tag a `v1.0.0` release once all tasks above are complete

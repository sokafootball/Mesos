# Mesos Game – Webapp Implementation Plan

A todo list of tasks to implement the Mesos football game as a webapp that runs entirely in the browser (offline-capable, played locally on the same machine).

---

## 1. Project Setup

- [ ] Choose a technology stack (e.g. plain HTML/CSS/JavaScript, or a lightweight framework such as React + Vite)
- [ ] Initialise the project with a package manager (`npm init` / `yarn init`)
- [ ] Configure a local development server (e.g. Vite, Parcel, or a simple static HTTP server)
- [ ] Add a `README.md` section describing how to install dependencies and launch the game locally
- [ ] Set up a `.gitignore` to exclude `node_modules/`, `dist/`, and other build artefacts
- [ ] (Optional) Configure ESLint + Prettier for code consistency

---

## 2. Game Rules & Design

- [ ] Document the full rules of Mesos (turns, scoring, win conditions, special moves) in `docs/rules.md`
- [ ] Define all football player card attributes (e.g. name, position, speed, shooting, passing, defending, overall rating)
- [ ] Design the deck/card set: number of cards, rarity tiers, team groupings
- [ ] Decide on turn structure (e.g. round-based play, card draw, actions per turn)
- [ ] Define AI difficulty levels and behaviour (e.g. random, greedy, minimax)
- [ ] Create low-fidelity wireframes / mockups for all game screens (home, game board, card hand, score panel, end screen)

---

## 3. Data Layer

- [ ] Create a JSON data file (`src/data/cards.json`) with all player cards and their attributes
- [ ] Create a JSON data file (`src/data/teams.json`) with team metadata
- [ ] Write a data-loader module that imports and validates card/team data at startup
- [ ] Define TypeScript types / JSDoc typedefs for `Card`, `Team`, `GameState`, `Player` (human/AI)

---

## 4. Core Game Logic

- [ ] Implement deck management: shuffle, draw, discard, hand size limits
- [ ] Implement game state machine: `idle → setup → player_turn → ai_turn → resolution → game_over`
- [ ] Implement card play / action resolution rules
- [ ] Implement scoring system (goals, points, tiebreakers)
- [ ] Implement win/lose/draw detection
- [ ] Write unit tests for all game-logic functions (use Jest or Vitest)

---

## 5. AI Opponent

- [ ] Implement a random-move AI (baseline difficulty)
- [ ] Implement a greedy AI that always picks the highest-rated available play
- [ ] (Stretch) Implement a minimax / alpha-beta AI for a harder difficulty
- [ ] Expose a difficulty selector in the UI that maps to the correct AI strategy

---

## 6. UI – Game Screens

- [ ] **Home / Menu Screen**: title, "New Game" button, difficulty selector, rules link
- [ ] **Game Board Screen**: shared play area, current score, turn indicator, draw pile count
- [ ] **Player Hand**: display cards in hand, highlight playable cards, handle card selection
- [ ] **AI Hand**: hidden cards (face-down) with card count shown
- [ ] **Card Detail View**: show full stats when a card is clicked/hovered
- [ ] **Resolution Overlay**: animate the result of each round (winner, score change)
- [ ] **End Game Screen**: final score, win/lose/draw message, "Play Again" button

---

## 7. UI – Styling & Assets

- [ ] Design a colour scheme and typography that fits a football theme
- [ ] Create or source card artwork / player silhouettes (SVG or PNG)
- [ ] Create team badge / crest assets
- [ ] Implement responsive layout so the game fits common screen sizes (desktop-first is fine for local play)
- [ ] Add basic animations for card draw, card play, and score update

---

## 8. Offline / PWA Support

- [ ] Add a `manifest.json` with app name, icons, and `display: standalone`
- [ ] Implement a Service Worker (`sw.js`) that pre-caches all static assets, JS, CSS, and data files
- [ ] Register the Service Worker in the entry point (`index.html` / `main.js`)
- [ ] Test offline behaviour: disconnect network, reload page, verify full functionality
- [ ] Add an install prompt / "Add to Home Screen" badge (optional but nice-to-have)

---

## 9. Persistence (Local Storage)

- [ ] Save game state to `localStorage` so a game can survive a page refresh
- [ ] Add a "Resume Game" option on the Home screen when a saved game is detected
- [ ] Save high scores / win-loss record in `localStorage`
- [ ] Provide a "Clear Data" option in settings

---

## 10. Audio & Feedback

- [ ] Source or create short sound effects: card play, goal scored, game won/lost
- [ ] Add a mute / volume toggle in the UI
- [ ] Ensure all sounds are bundled with the app (no CDN requests) for offline use

---

## 11. Accessibility

- [ ] Ensure all interactive elements are keyboard-navigable
- [ ] Add ARIA labels to cards, buttons, and status regions
- [ ] Maintain sufficient colour contrast (WCAG AA minimum)
- [ ] Test with a screen reader for basic usability

---

## 12. Build & Distribution

- [ ] Configure a production build (`npm run build`) that outputs a self-contained `dist/` folder
- [ ] Verify the `dist/` folder works when served from `file://` or a simple static server (e.g. `npx serve dist`)
- [ ] Document the build and run steps in `README.md`
- [ ] (Optional) Create a one-click launcher script (`start.sh` / `start.bat`) that installs deps and opens the browser

---

## 13. Testing & QA

- [ ] Write unit tests for game logic (deck, state machine, scoring, AI)
- [ ] Write integration tests for game flows (new game → play turns → end game)
- [ ] Manual play-test: full game against each AI difficulty level
- [ ] Manual play-test: offline mode (no network) with Service Worker active
- [ ] Fix any bugs discovered during testing

---

## 14. Documentation

- [ ] Expand `README.md`: project overview, how to run locally, how to build, tech stack
- [ ] Add `docs/rules.md`: full Mesos game rules for players
- [ ] Add `docs/architecture.md`: high-level code structure and module descriptions
- [ ] Add inline code comments for complex logic (AI, state machine)

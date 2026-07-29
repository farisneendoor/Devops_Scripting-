# Shell Typing Game

A fully interactive typing speed and accuracy game built entirely in **Bash**. Practice typing numbers, letters, mixed characters, or custom words — under timed pressure, with persistent high scores.

No external dependencies. No frameworks. Pure shell scripting.

---

## Features

- **4 Practice Modes**
  - Numbers only
  - Letters only
  - Mixed (letters + numbers)
  - Custom word list
- **3 Difficulty Levels** — each tied to a real countdown timer
  - Easy — 5 seconds per round
  - Medium — 3 seconds per round
  - Hard — 1 second per round
- **Multi-round scoring** — choose how many rounds to play per session
- **Persistent high-score leaderboard** — scores are saved locally and displayed after every game
- **Polished CLI interface** — ANSI color-coded feedback and ASCII art banner

---

## Demo

```
========================================
         SHELL TYPING GAME
========================================
1) Practice Numbers
2) Practice Letters
3) Mixed (Letters + Numbers)
4) Custom Words
5) Exit
========================================
Choose a mode [1-5]: 2

How many rounds? [default 5]: 5

==========================
      DIFFICULTY
==========================
1) Easy   - 5 seconds
2) Medium - 3 seconds
3) Hard   - 1 second
==========================
Choose difficulty [1-3]: 2

Type this within 3s: k
> k
✅ Correct!

...

==========================
Final Score: 4/5
==========================
```

---

## Requirements

- A Unix-like OS (Linux or macOS)
- Bash 4.0+ (required for associative arrays — `declare -A`)

Check your Bash version:
```bash
bash --version
```

---

## Installation & Usage

**1. Clone the repository:**
```bash
git clone https://github.com/<your-username>/shell-typing-game.git
cd shell-typing-game
```

**2. Make the script executable:**
```bash
chmod +x typing-game.sh
```

**3. Run it:**
```bash
./typing-game.sh
```

---

## How It Works

| Component | Purpose |
|---|---|
| `generate_char()` | Produces a random number, letter, mixed character, or word using Bash's built-in `$RANDOM` variable |
| `play_round()` | Displays the target text and checks the user's input against it (untimed) |
| `play_round_timed()` | Same as above, but enforces a time limit using `read -t` |
| `play_game_timed()` | Runs multiple rounds in sequence and tracks the running score |
| `save_score()` | Appends the player's name, score, and timestamp to a local score file |
| `show_high_scores()` | Reads and displays the top scores from the saved file |

**Core mechanic:** `$RANDOM` generates a new pseudo-random integer every time it's referenced. Combined with modulo (`% 10`, `% 26`, etc.), this drives all random character/word selection in the game.

**Timer mechanic:** `read -t <seconds>` automatically fails if the user doesn't respond in time — this single flag is what powers the entire countdown system, no separate clock process needed.

**Score persistence:** Scores are appended (`>>`) to a hidden file at `~/.typing_game_scores`, so your history builds up across sessions rather than being overwritten.

---

## Project Structure
```
shell-typing-game/
├── typing-game.sh     # Main game script
└── README.md          # Documentation
```

---

## Development Approach

This project was built in 7 incremental milestones rather than all at once, to keep debugging manageable at each stage:

1. Menu system for selecting game mode
2. Random character/word generation
3. Input matching logic
4. Scoring across multiple rounds
5. Difficulty levels with enforced timers
6. Persistent high-score storage
7. UI polish — color output, ASCII banner, input validation

---

## Possible Future Improvements

- Track per-mode leaderboards separately
- Add a "custom word list" file the user can edit
- Add average reaction time per round
- Add sound/visual bell on wrong answers

---

## License

This project is open source and available under the [MIT License](LICENSE).

---

## Author

Built by [Faris](https://github.com/<your-username>) as part of hands-on Bash scripting and Linux fundamentals practice on the DevOps learning path.

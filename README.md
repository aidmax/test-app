# quiz-cli

> An interactive command-line quiz game for learning JavaScript and programming concepts.

Quiz CLI is a zero-dependency educational tool built with modern Node.js that tests your knowledge across JavaScript Basics, Node.js Fundamentals, and General Programming. It combines colorful terminal output, shuffled questions, real-time progress tracking, and performance-based feedback — all without installing a single npm package.

### Key Features

- ✓ Interactive category selection with 3 topic areas (JavaScript Basics, Node.js, General Programming)
- ✓ Flexible question count — play with All, 3, or 5 questions per session
- ✓ Fisher-Yates question shuffling for a fresh experience every run
- ✓ Real-time visual progress bar with live score tracking
- ✓ Color-coded terminal output using raw ANSI escape codes
- ✓ Incorrect answer review with detailed explanations after each session
- ✓ Performance-based result messages with emoji feedback
- ✓ Zero external dependencies — pure Node.js built-in modules only
- ✓ ES Modules (ESM) throughout — modern JavaScript from top to bottom

**Stack:** JavaScript (ES6+) · Node.js ≥ 18 · ES Modules · No external dependencies

---

## Setup Instructions

### Prerequisites

You need Node.js version 18.0.0 or higher. No package manager setup or `npm install` is required.

| Tool    | Minimum Version | Check Command         |
|---------|-----------------|-----------------------|
| Node.js | 18.0.0          | `node --version`      |
| npm     | bundled with Node| `npm --version`      |

### Installation

1. **Clone the repository**

```bash
git clone https://github.com/aidmax/test-app.git
cd test-app
```

✅ **Verify:** You should see the project folder containing `index.js`, `package.json`, `src/`, and `data/`.

2. **Confirm no dependencies are needed**

This project uses only Node.js built-in modules (`node:fs/promises`, `node:readline`, `node:url`, `node:path`). There is nothing to install.

```bash
cat package.json
```

✅ **Verify:** The output contains no `"dependencies"` or `"devDependencies"` keys — this is intentional.

3. **Confirm Node.js version compatibility**

```bash
node --version
```

✅ **Verify:** The printed version is `v18.0.0` or higher (e.g. `v20.11.0`). If not, install a compatible version from [nodejs.org](https://nodejs.org).

### Run Tests

```bash
npm test
```

✅ **Verify:** The Node.js built-in test runner executes without errors.

---

## How to Run the Project

### Development / Standard Mode

```bash
npm start
```

Or call the entry point directly:

```bash
node index.js
```

**Expected output:** The terminal clears and displays the ASCII welcome banner, followed by the category selection menu:

```
  ╔══════════════════════════════════╗
  ║       🧠  QUIZ CLI  🧠           ║
  ╚══════════════════════════════════╝

  Select a category:
  1. JavaScript Basics
  2. Node.js Fundamentals
  3. General Programming
  4. Quit
```

> There is no separate production build step. The application runs directly from source using `node index.js`.

---

## Usage Examples

### Example 1 — Category Selection and Question Count

After launching the app you are prompted to pick a topic and then how many questions you want:

```
Select a category:
  1. JavaScript Basics
  2. Node.js Fundamentals
  3. General Programming
  4. Quit

> 1

How many questions?
  1. All (5)
  2. 3 questions
  3. 5 questions

> 2
```

The quiz immediately begins with 3 randomly shuffled questions from the JavaScript Basics pool.

---

### Example 2 — Answering a Question with Progress Bar

Each question displays your current progress, the question text, and lettered answer options. Color-coded feedback is shown immediately after you answer:

```
Progress: [████████░░░░░░░░░░░░] 2/3  Score: 1

  Q2. Which keyword declares a block-scoped variable in JavaScript?

    A. var
    B. let
    C. define
    D. set

> B

  ✅  Correct! Well done.
```

If you answer incorrectly, the terminal highlights the right answer in green and your choice in red.

---

### Example 3 — End-of-Session Results and Review

After the final question, a full results summary is displayed. Any missed questions are listed with their correct answers and explanations:

```
  ══════════════════════════════════
          📊  YOUR RESULTS
  ══════════════════════════════════

  Score:      2 / 3
  Percentage: 66.7%
  Feedback:   Good effort! Keep practising. 💪

  ── Review: Questions You Missed ──

  Q. What does the '===' operator check?
  ✔  Correct answer: Value and type equality
  💡 Unlike '==', strict equality does not perform type coercion.

  ══════════════════════════════════

  Play again? (y/n) >
```

Entering `y` returns you to the category selection screen; `n` exits the application.

---

## File Structure

```
test-app/
│
├── index.js                  # Main entry point — banner, category loop, game orchestration
│
├── package.json              # Project metadata, scripts, engine requirement (Node ≥ 18)
│
├── src/                      # Application source modules
│   ├── colors.js             # ANSI escape-code helpers (colorize, red, green, success, etc.)
│   ├── input.js              # Readline wrappers (prompt, select, confirm, pressEnter)
│   └── quiz.js               # Quiz class — state management, scoring, progress bar, results
│
└── data/
    └── questions.json        # 15 quiz questions across 3 categories with answers & explanations
```

**Layer breakdown:**

| Layer | Files | Responsibility |
|-------|-------|----------------|
| Entry | `index.js` | App bootstrap, welcome banner, main loop |
| Game Logic | `src/quiz.js` | Quiz class, shuffling, scoring, result rendering |
| I/O | `src/input.js` | All user input via Node.js `readline` |
| Presentation | `src/colors.js` | Terminal colour styling via ANSI codes |
| Data | `data/questions.json` | Static question bank (15 questions, 3 categories) |

---

## Contributing

Contributions are welcome! To add new question categories, improve terminal UI, or extend functionality:

1. **Fork** the repository on GitHub
2. **Create a branch** for your change:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Commit** your changes with a descriptive message:
   ```bash
   git commit -m "feat: add Python Basics question category"
   ```
4. **Push** your branch and open a Pull Request against `main`

When adding questions, follow the existing schema in `data/questions.json` — each entry requires `question`, `options` (array of 4 strings), `answer` (zero-based index), and `explanation`.

---

## License

This project is licensed under the **MIT License**.

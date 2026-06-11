# quiz-cli

> An interactive command-line quiz game for learning JavaScript — right from your terminal.

quiz-cli is a zero-dependency quiz experience built entirely on Node.js built-ins. It challenges you with categorized, multiple-choice programming questions, tracks your score in real time, and explains every answer so you actually learn something. No npm install required — just Node.js and a terminal.

**Key Features**

- ✓ Categorized multiple-choice questions loaded from a local JSON database
- ✓ Interactive category and question-count selection at the start of each session
- ✓ Real-time progress bar and score tracking throughout the quiz
- ✓ Answer explanations displayed after each question
- ✓ Session-based play-again loop — keep going without restarting the process
- ✓ Colorized terminal output via custom ANSI utilities (no external dependencies)
- ✓ Randomized question order using Fisher-Yates shuffle for varied sessions

**Technology Stack**

- **Runtime**: Node.js ≥ 18.0.0
- **Module system**: ES Modules (`import`/`export`)
- **Dependencies**: None — uses only Node.js built-ins (`fs/promises`, `readline`, `path`, `url`)
- **Language**: JavaScript (vanilla, no transpilation)

---

## Setup Instructions

### Prerequisites

You need Node.js version 18 or higher. No package manager or internet connection is required beyond the initial clone.

| Tool    | Minimum Version | Check Command         |
|---------|-----------------|-----------------------|
| Node.js | 18.0.0          | `node --version`      |
| Git     | Any             | `git --version`       |

### Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/aidmax/test-app.git
   cd test-app/quiz-cli
   ```

   ✅ **Verify**: You are inside the `quiz-cli` directory and can see `index.js` and `package.json`.

2. **Confirm no dependencies need installing**

   quiz-cli has zero external dependencies. There is no `node_modules` directory and no `npm install` step required. All functionality is powered by Node.js built-in modules.

   ```bash
   cat package.json
   ```

   ✅ **Verify**: The `package.json` contains no `dependencies` or `devDependencies` fields — this is expected and correct.

3. **Verify Node.js version**

   ```bash
   node --version
   ```

   ✅ **Verify**: Output shows `v18.0.0` or higher (e.g. `v20.11.0`). If your version is lower, update Node.js at [nodejs.org](https://nodejs.org).

4. **Run the test suite**

   ```bash
   npm test
   ```

   ✅ **Verify**: Tests complete without errors. If no test files are present, Node.js will report `0 tests` — this is acceptable and means the suite is clean.

---

## How to Run the Project

### Development / Standard Mode

Start the quiz game with the npm script defined in `package.json`:

```bash
npm start
```

Or invoke Node.js directly:

```bash
node index.js
```

**Expected output** — you will see a colorized welcome banner followed by a category selection menu printed to your terminal:

```
╔══════════════════════════════════════╗
║         Welcome to quiz-cli          ║
║   An interactive JavaScript quiz     ║
╚══════════════════════════════════════╝

Select a category:
  1. JavaScript Basics
  2. Functions & Scope
  3. Async & Promises
  ...
```

> **Note**: quiz-cli is a terminal application. There is no browser interface or server port. Everything runs inside your shell session.

---

## Usage Examples

### Example 1 — Starting a Quiz Session

Launch the game, select a category, and choose how many questions to answer:

```bash
npm start
```

```
Select a category:
  1. JavaScript Basics
  2. Functions & Scope
  3. Async & Promises

Enter your choice: 1

How many questions? (1-10): 5

Starting quiz... Good luck!
```

### Example 2 — Answering a Question

Each question is presented with numbered options. Enter the number corresponding to your answer:

```
Question 3 / 5  [████████░░░░░░░░] 40%

Which keyword declares a block-scoped variable in JavaScript?

  1. var
  2. let
  3. function
  4. const

Your answer: 2

✅ Correct! +1 point

Explanation: `let` declares a variable scoped to the nearest enclosing block,
unlike `var` which is function-scoped or globally scoped.
```

### Example 3 — Viewing Final Results and Playing Again

After all questions are answered, your results are displayed with a final score and a play-again prompt:

```
══════════════════════════════
         Quiz Complete!
══════════════════════════════
  Score:     4 / 5
  Correct:   4
  Incorrect: 1
  Accuracy:  80%
══════════════════════════════

Play again? (y/n): y
```

Entering `y` restarts the category selection loop without exiting the process. Entering `n` exits cleanly.

---

## File Structure

```
quiz-cli/
│
├── index.js                  # Main entry point — bootstraps the app, loads questions,
│                             #   displays the welcome banner, and drives the game loop
│                             #   (category select → question count → quiz → results → replay)
│
├── package.json              # Project metadata, npm scripts (`start`, `test`),
│                             #   engine requirement (Node ≥ 18), MIT license declaration
│
├── src/                      # Application source modules
│   ├── colors.js             # ANSI escape code utilities — exports colorize(), red(),
│   │                         #   green(), yellow(), blue(), cyan(), magenta(), bold(),
│   │                         #   dim(), success(), error(), warning(), info(), highlight()
│   │
│   ├── input.js              # Terminal input handling via Node.js `readline` built-in —
│   │                         #   exports createInterface(), prompt(), select(),
│   │                         #   confirm(), pressEnter()
│   │
│   └── quiz.js               # Core quiz logic — exports the `Quiz` class, which manages
│                             #   Fisher-Yates question shuffling, progress bar rendering,
│                             #   score tracking, answer recording, and explanation display
│
└── data/
    └── questions.json        # Quiz question database organized by category — each entry
                              #   contains: question text, options array, answer index,
                              #   and an explanation string
```

---

## Contributing

Contributions are welcome. Follow this workflow:

1. **Fork** the repository on GitHub
2. **Create a branch** for your change:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Commit** your changes with a clear message:
   ```bash
   git commit -m "feat: add new JavaScript async questions"
   ```
4. **Push** your branch and open a **Pull Request** against `main`
5. Describe what you changed and why in the PR description

When adding questions to `data/questions.json`, ensure each entry includes `question`, `options` (array of 4 strings), `answer` (zero-based index), and `explanation`.

---

## License

This project is licensed under the **MIT License**. See the `LICENSE` file for details.

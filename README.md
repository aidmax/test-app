# Quiz CLI

> An interactive command-line quiz game for learning JavaScript — no dependencies required.

Quiz CLI is a terminal-based educational game that tests your knowledge of JavaScript, Node.js, and general programming concepts. Built entirely on native Node.js built-in modules, it requires zero npm installs beyond the runtime itself, making it instantly portable and lightweight.

**Key Features**

- ✓ Three quiz categories: JavaScript Basics, Node.js Fundamentals, and General Programming
- ✓ 15 total questions (5 per category), shuffled on every run using the Fisher-Yates algorithm
- ✓ Flexible question count selection — answer All, 3, or 5 questions per session
- ✓ Real-time visual progress bar and live score tracking
- ✓ Performance-based feedback messages at the end of each quiz
- ✓ Post-quiz review of all incorrectly answered questions with explanations
- ✓ Play-again loop so you can retake quizzes without restarting the process
- ✓ Fully colored terminal output with ANSI styling — no external packages needed
- ✓ ASCII art welcome banner and menu-driven interface

**Technology Stack**

| Layer | Technology |
|---|---|
| Language | JavaScript (ES Modules) |
| Runtime | Node.js ≥ 18.0.0 |
| Input handling | `node:readline` (built-in) |
| File I/O | `node:fs/promises` (built-in) |
| Terminal colors | ANSI escape codes (custom module) |
| External dependencies | None |

---

## Setup Instructions

### Prerequisites

You need Node.js version 18.0.0 or higher installed on your machine. No package manager setup is required because this project has zero external dependencies.

| Tool | Minimum Version | Install |
|---|---|---|
| Node.js | 18.0.0 | [nodejs.org](https://nodejs.org) |
| npm | Bundled with Node.js | — |

Verify your environment before proceeding:

```bash
node --version
# Expected: v18.0.0 or higher

npm --version
# Expected: 8.x or higher
```

✅ **Verify**: Both commands return version numbers without errors.

### Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/aidmax/test-app.git
   cd test-app
   ```

   ✅ **Verify**: You are inside the `test-app` directory and can see `index.js` and `package.json`.

2. **Confirm project files are present**

   ```bash
   ls
   # Expected output: data  index.js  package.json  src
   ```

   ✅ **Verify**: The `src/` directory and `data/questions.json` file are visible.

3. **No dependency installation required**

   This project uses only Node.js built-in modules (`node:fs/promises`, `node:readline`, `node:url`, `node:path`). There is nothing to install via npm.

   ✅ **Verify**: Open `package.json` and confirm the `dependencies` field is absent.

---

## How to Run the Project

### Development / Standard Mode

Start the quiz application using the npm script defined in `package.json`:

```bash
npm start
```

Alternatively, invoke the entry point directly:

```bash
node index.js
```

Both commands are equivalent. The application will clear the terminal, display the ASCII art welcome banner, and drop you into the main menu.

**Expected output on launch:**

```
╔══════════════════════════════════════╗
║         Welcome to Quiz CLI          ║
║   An interactive JavaScript Quiz     ╠
╚══════════════════════════════════════╝

Select a category:
  1. JavaScript Basics
  2. Node.js Fundamentals
  3. General Programming
```

### Running Tests

The project includes a test runner configuration using Node.js's built-in test runner (available since Node.js 18):

```bash
npm test
```

This executes `node --test`, which discovers and runs any test files present in the project.

---

## Usage Examples

### Example 1 — Selecting a Category and Answering Questions

After launch, you are prompted to choose a quiz category by entering a number. You then select how many questions you want to answer.

```
Select a category:
  1. JavaScript Basics
  2. Node.js Fundamentals
  3. General Programming

Your choice: 1

How many questions?
  1. All (5)
  2. Quick (3)
  3. Short (5)

Your choice: 2
```

Each question is presented with four numbered answer options and a live progress bar:

```
Progress: [████████░░░░░░░░░░░░] 2/3

Question 2 of 3:
What does the `typeof` operator return for null?

  1. "null"
  2. "object"
  3. "undefined"
  4. "boolean"

Your answer: 2
```

### Example 2 — Quiz Results and Performance Feedback

After answering all selected questions, the quiz displays a detailed results summary with a percentage score and a performance message tailored to your result.

```
╔══════════════════════════╗
║       Quiz Results       ║
╚══════════════════════════╝

Score: 2 / 3  (66.7%)

Good effort! Keep practicing to improve.

--- Incorrect Answers Review ---

Question: What does the `typeof` operator return for null?
Your answer:  "null"
Correct answer: "object"
Explanation: This is a well-known JavaScript quirk. typeof null returns
             "object" due to a bug in the original JS implementation.
```

### Example 3 — Play Again Loop

At the end of every quiz session you are asked whether you want to play again. Entering `y` returns you to the category selection screen; entering `n` exits cleanly.

```
Would you like to play again? (y/n): y

Select a category:
  1. JavaScript Basics
  2. Node.js Fundamentals
  3. General Programming
```

Pressing `n` prints a farewell message and terminates the Node.js process gracefully.

---

## File Structure

```
test-app/
│
├── index.js                  # Entry point — orchestrates startup, main loop,
│                             #   category/question-count selection, and play-again flow
│
├── package.json              # Project metadata, npm scripts, engine requirements
│
├── src/                      # Application source modules
│   ├── colors.js             # ANSI escape code utilities — colorize(), bold(), success(),
│   │                         #   error(), warning(), info(), highlight(), and named color helpers
│   ├── input.js              # Readline-based user input — prompt(), select(),
│   │                         #   confirm(), pressEnter()
│   └── quiz.js               # Core quiz engine — Quiz class with askQuestion(),
│                             #   showResults(), renderProgressBar(), scoring, and shuffling
│
└── data/
    └── questions.json        # Quiz question database — 3 categories × 5 questions each,
                              #   with answer options, correct index, and explanations
```

**Module responsibilities at a glance:**

| File | Layer | Responsibility |
|---|---|---|
| `index.js` | Orchestration | Application lifecycle, routing, error handling |
| `src/quiz.js` | Game Logic | Question flow, scoring, shuffling, feedback |
| `src/input.js` | I/O | All user input via Node.js readline |
| `src/colors.js` | Presentation | Terminal styling via ANSI escape codes |
| `data/questions.json` | Data | Static question bank |

---

## Contributing

Contributions are welcome. Please follow this workflow:

1. **Fork** the repository on GitHub.
2. **Create a branch** for your feature or fix:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Commit** your changes with a descriptive message:
   ```bash
   git commit -m "feat: add new category for TypeScript questions"
   ```
4. **Push** your branch and open a **Pull Request** against `main`, describing what you changed and why.

To add new quiz questions, edit `data/questions.json` following the existing structure — each entry requires a `question` string, an `options` array of four strings, a zero-based `correctIndex` integer, and an `explanation` string.

---

## License

This project is licensed under the **MIT License**.

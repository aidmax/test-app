# quiz-cli

> An interactive command-line quiz game for learning JavaScript — right from your terminal.

Quiz CLI is a lightweight educational tool that tests your programming knowledge through a fully interactive terminal interface. It requires **zero external dependencies**, runs entirely on Node.js built-ins, and delivers a polished quiz experience complete with category selection, shuffled questions, answer explanations, a live progress bar, and score tracking.

### Key Features

- ✓ Category-based question selection
- ✓ Configurable question count (3, 5, or all available)
- ✓ Fisher-Yates shuffled questions for a fresh experience every run
- ✓ Instant answer feedback with explanations
- ✓ Live progress bar during the quiz
- ✓ Score summary at the end of each session
- ✓ Play-again loop — no need to restart the process
- ✓ Zero external dependencies — uses only Node.js built-in modules
- ✓ Clean, colorized terminal output via ANSI escape codes

**Tech Stack:** `Node.js >= 18.0.0` · `ES Modules (ESM)` · `readline (built-in)` · `JSON data store`

---

## Setup Instructions

### Prerequisites

You need **Node.js version 18 or higher** installed on your machine. No package manager beyond npm (bundled with Node.js) is required.

| Tool    | Minimum Version | Check Command         |
|---------|-----------------|-----------------------|
| Node.js | 18.0.0          | `node --version`      |
| npm     | 8.0.0           | `npm --version`       |

### Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/aidmax/test-app.git
   cd test-app
   ```

   ✅ **Verify**: You are inside the `test-app` directory and can see `index.js` and `package.json`.

2. **Install dependencies**

   This project has no external dependencies. However, run the following to confirm the project is recognized correctly by npm:

   ```bash
   npm install
   ```

   ✅ **Verify**: npm reports `up to date` or `added 0 packages`. No `node_modules` folder with third-party packages will be created.

3. **Verify the questions database is present**

   ```bash
   ls data/questions.json
   ```

   ✅ **Verify**: The file `data/questions.json` is listed. This file contains all quiz questions organized by category.

---

## How to Run the Project

### Development / Standard Mode

Start the quiz using the npm script defined in `package.json`:

```bash
npm start
```

Alternatively, invoke the entry point directly:

```bash
node index.js
```

**Expected output:**

```
╔══════════════════════════════════╗
║       Welcome to Quiz CLI!       ║
║  Test your JavaScript knowledge  ║
╚══════════════════════════════════╝

Available categories:
  1) JavaScript Basics
  2) Functions & Scope
  3) ...

Select a category:
```

The application will guide you through category selection, question count configuration, and the quiz loop interactively. Visit no URL — this is a fully terminal-based application.

---

## Usage Examples

### Example 1 — Starting a Quiz Session

Launch the game, select a category, and choose how many questions to answer:

```bash
$ npm start

Select a category: 1
How many questions? (3 / 5 / all): 3

Question 1 of 3  [████████░░░░░░░░░░░░] 33%

What is the output of typeof null?
  A) "null"
  B) "object"
  C) "undefined"
  D) "string"

Your answer: B
```

**Expected feedback after answering:**

```
✅ Correct!
💡 Explanation: In JavaScript, typeof null returns "object" — this is a
   well-known historical bug in the language that was never fixed for
   backward compatibility reasons.
```

### Example 2 — Completing a Quiz and Viewing Results

After all questions are answered, the score summary is displayed:

```bash
Quiz Complete! 🎉

╔══════════════════════════════════╗
║           Your Results           ║
╠══════════════════════════════════╣
║  Score:     4 / 5                ║
║  Correct:   4                    ║
║  Incorrect: 1                    ║
║  Rating:    ⭐⭐⭐⭐              ║
╚══════════════════════════════════╝

Play again? (y/n):
```

### Example 3 — Playing Again Without Restarting

When prompted at the results screen, enter `y` to restart the category and question-count selection without exiting the process:

```bash
Play again? (y/n): y

Available categories:
  1) JavaScript Basics
  2) Functions & Scope
  ...

Select a category:
```

Enter `n` to exit gracefully:

```bash
Play again? (y/n): n

Thanks for playing Quiz CLI. Goodbye! 👋
```

---

## File Structure

```
test-app/
│
├── index.js                 # Main entry point — orchestrates startup, category/question
│                            #   selection, quiz loop, results display, and play-again flow
│
├── package.json             # Project metadata, npm scripts (start, test), engine constraint
│
├── src/                     # Application source modules
│   ├── colors.js            # Terminal color utility — ANSI escape code wrappers
│   │                        #   Exports: colorize, red, green, yellow, blue, cyan,
│   │                        #   magenta, bold, dim, success, error, warning, info, highlight
│   │
│   ├── input.js             # User input handling — wraps Node.js built-in readline
│   │                        #   Exports: createInterface, prompt, select, confirm, pressEnter
│   │
│   └── quiz.js              # Core quiz logic — Quiz class with question shuffling (Fisher-Yates),
│                            #   askQuestion, showResults, renderProgressBar, and state getters
│
└── data/
    └── questions.json       # Quiz questions database — organized by category; each entry
                             #   contains: question text, options array, answer index, explanation
```

---

## Contributing

Contributions are welcome! Please follow this workflow:

1. **Fork** the repository on GitHub
2. **Create a branch** for your feature or fix:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Commit** your changes with a clear message:
   ```bash
   git commit -m "feat: add new JavaScript ES6 category"
   ```
4. **Push** your branch to your fork:
   ```bash
   git push origin feature/your-feature-name
   ```
5. **Open a Pull Request** against the `main` branch of this repository and describe your changes

When adding new quiz questions, follow the existing structure in `data/questions.json` — each question must include `question`, `options`, `answer` (zero-based index), and `explanation` fields.

---

## License

This project is licensed under the **MIT License**.

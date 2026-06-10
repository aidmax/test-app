# quiz-cli

> An interactive command-line quiz game for learning JavaScript and programming concepts.

quiz-cli helps developers and students test their knowledge of JavaScript, Node.js, and general programming through a fully interactive terminal experience. It provides immediate feedback on every answer, detailed explanations, and a performance summary at the end of each session — all without requiring a single external dependency.

**Key Features:**

- ✓ Three quiz categories: JavaScript Basics, Node.js Fundamentals, and General Programming
- ✓ 15 questions across categories with randomized order using the Fisher-Yates shuffle algorithm
- ✓ Flexible question count per session — choose all questions, 3, or 5
- ✓ Immediate answer validation with per-question explanations
- ✓ Visual progress bar rendered in the terminal during the quiz
- ✓ Final score summary with performance-based messages and a review of incorrect answers
- ✓ Fully colorized terminal output using pure ANSI escape codes — no external packages
- ✓ Play-again loop so you can practice multiple categories in one session

**Technology Stack:**

- Language: JavaScript (ES2022)
- Runtime: Node.js ≥ 18.0.0
- Module system: ES Modules (`import`/`export`)
- Dependencies: None — uses only Node.js built-in modules (`node:fs/promises`, `node:readline`, `node:url`, `node:path`)

---

## Setup Instructions

### Prerequisites

You need Node.js version 18.0.0 or higher installed on your machine. No other tools are required.

| Tool    | Minimum Version | Verify with          |
|---------|-----------------|----------------------|
| Node.js | 18.0.0          | `node --version`     |
| npm     | 8.0.0           | `npm --version`      |

```bash
node --version
# Expected output: v18.x.x or higher

npm --version
# Expected output: 8.x.x or higher
```

✅ **Verify:** Both commands return version numbers matching the requirements above before proceeding.

---

### Installation

1. **Clone the repository**

```bash
git clone https://github.com/aidmax/test-app.git
cd test-app
```

✅ **Verify:** You are inside the `test-app` directory and can see `index.js` and `package.json`.

```bash
ls
# Expected output: data  index.js  package.json  src
```

2. **Confirm no dependencies need to be installed**

This project uses only Node.js built-in modules. There is no `node_modules` directory to install.

```bash
cat package.json | grep dependencies
# Expected output: (no output — the project has zero external dependencies)
```

✅ **Verify:** The project is ready to run immediately after cloning.

3. **Run the tests**

```bash
npm test
```

✅ **Verify:** The test runner completes without errors.

---

## How to Run the Project

### Development / Standard Mode

Start the quiz application using the `start` script defined in `package.json`:

```bash
npm start
```

This executes `node index.js`. The terminal will clear and display the welcome banner:

```
  ╔═══════════════════════════════════════════╗
  ║                                           ║
  ║   📚 QUIZ CLI                             ║
  ║   Test your programming knowledge!        ║
  ║                                           ║
  ╚═══════════════════════════════════════════╝
```

You can also run the application directly with Node.js:

```bash
node index.js
```

> **Note:** There is no Docker configuration in this project. No `Dockerfile` or `docker-compose.yml` is present.

---

## Usage Examples

### Example 1 — Selecting a Category and Answering a Question

When the application starts, you are presented with a numbered category menu. Enter the number corresponding to your choice and press **Enter**.

```
Choose a category:

  1. JavaScript Basics
  2. Node.js Fundamentals
  3. General Programming

Your choice (enter number): 1
```

You are then asked how many questions you want:

```
How many questions?

  1. All questions
  2. 3 questions
  3. 5 questions

Your choice (enter number): 2
```

Each question is displayed with a progress bar and numbered answer options:

```
[██████░░░░░░░░░░░░░░░░░░░░░░░░] 20%
Question 2 of 3

What does '===' check for?

  1. Value only
  2. Type only
  3. Value and type
  4. Reference

Your choice (enter number): 3

✓ Correct!
💡 The strict equality operator (===) checks both value and type without coercion.
```

---

### Example 2 — Incorrect Answer with Feedback

If you select a wrong answer, the CLI immediately shows the correct option and the explanation:

```
Your choice (enter number): 1

✗ Incorrect!
The correct answer was: Value and type
💡 The strict equality operator (===) checks both value and type without coercion.
```

---

### Example 3 — Final Results and Review

After all questions are answered, the quiz displays your score, a performance message, and a review of any questions you answered incorrectly:

```
══════════════════════════════════════════════════
  📊 QUIZ RESULTS
══════════════════════════════════════════════════

  Category: JavaScript Basics
  Score: 4/5 (80%)

  🌟 Great job! Well done!

══════════════════════════════════════════════════

📝 Review these questions:

1. What is the output of: typeof null?
   Your answer:  'null'
   Correct:      'object'
```

At the end of each session you are asked:

```
Would you like to play again? (y/n):
```

Enter `y` to return to the category menu or `n` to exit.

---

## File Structure

```
test-app/
│
├── index.js                  # Main entry point — orchestrates game flow, loads questions,
│                             #   displays the welcome banner, and manages the play-again loop
│
├── package.json              # Project manifest — name, version, scripts, engine requirements
│
├── src/                      # Application source modules
│   ├── colors.js             # ANSI terminal color utilities — colorize(), red(), green(),
│   │                         #   success(), error(), highlight(), and more
│   ├── input.js              # User input layer — Promise-based wrappers around Node.js
│   │                         #   readline: prompt(), select(), confirm(), pressEnter()
│   └── quiz.js               # Core quiz engine — Quiz class with question shuffling,
│                             #   answer tracking, progress bar rendering, and results display
│
└── data/
    └── questions.json        # Quiz content database — 15 questions across 3 categories
                              #   (JavaScript Basics, Node.js Fundamentals, General Programming)
```

**Logical Layers:**

| Layer           | Files                  | Responsibility                                      |
|-----------------|------------------------|-----------------------------------------------------|
| Entry / Control | `index.js`             | Application bootstrap, game loop, error handling    |
| Game Logic      | `src/quiz.js`          | Quiz class, scoring, shuffling, results rendering   |
| I/O             | `src/input.js`         | All user input via Promise-wrapped readline         |
| Presentation    | `src/colors.js`        | ANSI styling utilities for terminal output          |
| Data            | `data/questions.json`  | Static question bank organized by category          |

---

## Contributing

Contributions are welcome! Follow these steps to propose a change:

1. **Fork** the repository on GitHub
2. **Create a feature branch** from `main`:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Commit** your changes with a clear message:
   ```bash
   git commit -m "feat: add new quiz category for TypeScript"
   ```
4. **Push** the branch to your fork:
   ```bash
   git push origin feature/your-feature-name
   ```
5. **Open a Pull Request** against the `main` branch and describe what you changed and why.

When adding new questions, follow the existing schema in `data/questions.json` — each question requires a `question` string, an `options` array of four strings, a zero-based `answer` index, and an `explanation` string.

---

## License

This project is licensed under the **MIT License**.

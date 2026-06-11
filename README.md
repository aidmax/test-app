# quiz-cli

> An interactive command-line quiz game for learning JavaScript and Node.js concepts.

Test your knowledge of JavaScript, Node.js, and general programming through a fully terminal-based quiz experience. quiz-cli helps beginner and intermediate developers reinforce core concepts with instant feedback, answer explanations, and performance scoring — all with zero external dependencies.

## Key Features

- ✓ 15 curated questions across 3 categories: JavaScript Basics, Node.js Fundamentals, and General Programming
- ✓ Selectable difficulty modes: answer all questions, or quick rounds of 3 or 5
- ✓ Randomized question order using the Fisher-Yates shuffle algorithm
- ✓ Visual progress bar to track quiz advancement in real time
- ✓ Post-quiz answer review with detailed explanations for every question
- ✓ Performance-based feedback with dynamic scoring messages
- ✓ Colorized terminal output for an enhanced CLI experience
- ✓ Zero external dependencies — powered entirely by Node.js built-in modules

**Technology Stack:** JavaScript (ES6 Modules) · Node.js ≥ 18.0.0 · MIT License

---

## Setup Instructions

### Prerequisites

You need Node.js version 18.0.0 or higher installed on your machine. No package manager beyond npm (bundled with Node.js) is required.

| Tool    | Minimum Version | Check Command         |
|---------|-----------------|-----------------------|
| Node.js | 18.0.0          | `node --version`      |
| npm     | 8.0.0           | `npm --version`       |

### Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/aidmax/test-app.git
   cd test-app/quiz-cli
   ```

   ✅ **Verify:** You are inside the `quiz-cli` directory and can see `index.js` and `package.json`.

2. **Confirm no dependencies need installation**

   quiz-cli uses only Node.js built-in modules. There is nothing to install via npm. You can optionally run the following to confirm the project is recognized correctly:

   ```bash
   npm run test
   ```

   ✅ **Verify:** The command exits without errors. If no test files are found, Node.js will report `0 tests` — this is expected.

---

## How to Run the Project

### Development / Standard Mode

Start the quiz application with the following command from inside the `quiz-cli` directory:

```bash
npm start
```

This runs `node index.js` as defined in `package.json`.

**Expected output:**

```
╔══════════════════════════════════════╗
║        Welcome to Quiz CLI!          ║
║   Test your JavaScript knowledge     ║
╚══════════════════════════════════════╝

Select a category:
1. JavaScript Basics
2. Node.js Fundamentals
3. General Programming
4. All Categories
```

The application will guide you through category selection, difficulty mode, and the quiz loop. After each completed quiz, you will be prompted to play again.

---

## Usage Examples

### Example 1 — Starting a Quiz Session

Launch the quiz and navigate the category menu using numeric input:

```bash
npm start
```

```
Select a category:
1. JavaScript Basics
2. Node.js Fundamentals
3. General Programming
> 1

Select number of questions:
1. All questions (5)
2. Quick round (3)
3. Short round (5)
> 2
```

### Example 2 — Answering a Question

Each question displays multiple-choice options. Enter the number of your chosen answer:

```
Question 3/3  [████████████░░░░░░░░] 60%

What does the === operator check in JavaScript?
1. Value only
2. Value and type
3. Type only
4. Reference equality

> 2

✅ Correct! The strict equality operator (===) checks both value AND type,
   unlike == which performs type coercion before comparing.
```

### Example 3 — Viewing Quiz Results

After completing all questions, the results screen displays your score, performance message, and a full answer review:

```
══════════════════════════════════════
            Quiz Complete!
══════════════════════════════════════
  Score: 4 / 5  (80%)
  🎉 Great job! You really know your stuff!

Review:
  ✅ Q1 — What keyword declares a block-scoped variable?
  ✅ Q2 — Which method adds an element to the end of an array?
  ✅ Q3 — What does === check?
  ❌ Q4 — What is the typeof null in JavaScript?
        Your answer : object (primitive)
        Correct     : "object" — this is a known JavaScript quirk
  ✅ Q5 — What are JavaScript's primitive data types?

Play again? (y/n) >
```

---

## File Structure

```
quiz-cli/
│
├── index.js                  # Main entry point — bootstraps the app, manages game loop,
│                             #   handles category/difficulty selection and play-again flow
│
├── package.json              # Project metadata, scripts, Node.js engine requirement
│
├── src/                      # Application source modules
│   ├── colors.js             # ANSI terminal color utilities — colorize(), success(),
│   │                         #   error(), warning(), info(), highlight() and raw color helpers
│   ├── input.js              # Readline wrapper — Promise-based prompt(), select(),
│   │                         #   confirm(), and pressEnter() functions
│   └── quiz.js               # Core quiz engine — Quiz class with askQuestion(),
│                             #   showResults(), renderProgressBar(), score tracking,
│                             #   Fisher-Yates shuffle, and performance feedback
│
└── data/
    └── questions.json        # Quiz question database — 15 questions across 3 categories,
                              #   each with options array, answer index, and explanation
```

**Logical layers at a glance:**

| Layer           | Files                        | Responsibility                                    |
|-----------------|------------------------------|---------------------------------------------------|
| Entry / Control | `index.js`                   | App startup, menu flow, game loop orchestration   |
| Game Logic      | `src/quiz.js`                | Question handling, scoring, progress, feedback    |
| I/O Utilities   | `src/input.js`               | All user input via readline (prompts, menus)      |
| UI Utilities    | `src/colors.js`              | Terminal styling via ANSI escape codes            |
| Data            | `data/questions.json`        | Static question bank with answers and explanations|

---

## Contributing

Contributions are welcome! To add new questions, fix bugs, or extend features, follow this workflow:

1. Fork the repository on GitHub
2. Create a new feature branch:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. Make your changes and commit with a descriptive message:
   ```bash
   git commit -m "feat: add ES2022 questions to JavaScript category"
   ```
4. Push your branch and open a pull request against `main`:
   ```bash
   git push origin feature/your-feature-name
   ```
5. Describe your changes clearly in the pull request body and reference any related issues

Please keep pull requests focused on a single change to make review straightforward.

---

## License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.

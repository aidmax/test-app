# quiz-cli

> An interactive command-line quiz game for learning JavaScript and programming concepts.

![Node.js](https://img.shields.io/badge/Node.js-%3E%3D18.0.0-339933?logo=node.js&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-ES2022-F7DF1E?logo=javascript&logoColor=black)
![License](https://img.shields.io/badge/License-MIT-blue.svg)
![Dependencies](https://img.shields.io/badge/Dependencies-None-brightgreen)

quiz-cli is a zero-dependency, fully interactive terminal quiz application built with Node.js. It helps developers and students reinforce their knowledge of JavaScript, Node.js, and general programming concepts directly from the command line — no browser, no frameworks, no installs beyond Node itself.

The app challenges you with multiple-choice questions, gives immediate per-answer feedback with explanations, tracks your score with a visual progress bar, and presents a detailed results summary at the end of every session.

### Key Features

- ✓ **Three quiz categories** — JavaScript Basics, Node.js Fundamentals, and General Programming
- ✓ **15 curated questions** with randomized order via the Fisher-Yates shuffle algorithm
- ✓ **Flexible session length** — choose all questions, 3, or 5 per round
- ✓ **Instant answer feedback** with per-question explanations after every response
- ✓ **Visual progress bar** rendered live in the terminal as you advance
- ✓ **Score summary** with performance-tier messages (🏆 Perfect → 💪 Keep practicing)
- ✓ **Incorrect answer review** — missed questions are listed with correct answers at the end
- ✓ **Colorized terminal output** using pure ANSI escape codes — no external packages
- ✓ **Play-again loop** to practice multiple categories in a single session

### Technology Stack

| Layer          | Technology                                                        |
|----------------|-------------------------------------------------------------------|
| Language       | JavaScript (ES2022)                                               |
| Runtime        | Node.js ≥ 18.0.0                                                  |
| Module System  | ES Modules (`import` / `export`)                                  |
| Dependencies   | None — only Node.js built-ins (`fs`, `readline`, `url`, `path`)   |

---

## Setup Instructions

### Prerequisites

You need Node.js 18.0.0 or higher installed on your machine. No other tools or package installations are required.

| Tool    | Minimum Version | Verify with      |
|---------|-----------------|------------------|
| Node.js | 18.0.0          | `node --version` |
| npm     | 8.0.0           | `npm --version`  |

```bash
node --version
# Expected: v18.x.x or higher

npm --version
# Expected: 8.x.x or higher
```

✅ **Verify:** Both commands return version numbers that satisfy the requirements above.

---

### Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/aidmax/test-app.git
   cd test-app
   ```

   ✅ **Verify:** You are inside the `test-app` directory and can see `index.js`, `package.json`, and the `src/` and `data/` directories.

   ```bash
   ls
   # Expected: data  index.js  package.json  src
   ```

2. **Confirm there are no dependencies to install**

   This project uses only Node.js built-in modules. There is no `node_modules` folder and nothing to install.

   ```bash
   cat package.json
   # Expected: no "dependencies" or "devDependencies" keys in the output
   ```

   ✅ **Verify:** The project is ready to run immediately after cloning — no `npm install` needed.

---

## How to Run the Project

### Standard Mode

Start the application using the `start` script defined in `package.json`:

```bash
npm start
```

This runs `node index.js`. The terminal clears and displays the welcome banner:

```
  ╔═══════════════════════════════════════════╗
  ║                                           ║
  ║   📚 QUIZ CLI                             ║
  ║   Test your programming knowledge!        ║
  ║                                           ║
  ╚═══════════════════════════════════════════╝
```

You can also invoke the entry point directly:

```bash
node index.js
```

Both commands produce identical results. Visit your terminal — no browser or port is involved.

> **Note:** This project does not include a `Dockerfile` or `docker-compose.yml`. Docker is not required or supported.

---

## Usage Examples

### Example 1 — Choosing a Category and Session Length

After the banner, you select a quiz category by entering its number and pressing **Enter**:

```
Choose a category:

  1. JavaScript Basics
  2. Node.js Fundamentals
  3. General Programming

Your choice (enter number): 1
```

Next, choose how many questions to answer:

```
How many questions?

  1. All questions
  2. 3 questions
  3. 5 questions

Your choice (enter number): 2
```

---

### Example 2 — Answering Questions with Live Feedback

Each question displays a progress bar, a question counter, and four numbered options:

```
[██████░░░░░░░░░░░░░░░░░░░░░░░░] 33%
Question 1 of 3

What does '===' check for?

  1. Value only
  2. Type only
  3. Value and type
  4. Reference

Your choice (enter number): 3

✓ Correct!
💡 The strict equality operator (===) checks both value and type without coercion.
```

If you select a wrong answer, the CLI immediately reveals the correct option:

```
Your choice (enter number): 1

✗ Incorrect!
The correct answer was: Value and type
💡 The strict equality operator (===) checks both value and type without coercion.
```

---

### Example 3 — Results Summary and Incorrect Answer Review

After all questions are answered, quiz-cli displays your score, a performance message, and a full review of any questions you got wrong:

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

Performance tiers are determined by your percentage score:

| Score     | Emoji | Message                          |
|-----------|-------|----------------------------------|
| 100%      | 🏆    | Perfect score! Amazing!          |
| 80–99%    | 🌟    | Great job! Well done!            |
| 60–79%    | 👍    | Good effort! Keep learning!      |
| 40–59%    | 📚    | Not bad! Room for improvement.   |
| 0–39%     | 💪    | Keep practicing! You'll get better! |

At the end of each round you are asked:

```
Would you like to play again? (y/n):
```

Enter `y` to return to the category menu or `n` to exit gracefully.

---

## File Structure

```
test-app/
│
├── index.js                 # Entry point — banner, category selection, session loop,
│                            #   question iteration, play-again prompt, error handling
│
├── package.json             # Project manifest — name, version, scripts (start, test),
│                            #   engine constraint (Node.js ≥ 18), MIT license declaration
│
├── src/                     # Core application modules
│   │
│   ├── quiz.js              # Quiz class — Fisher-Yates shuffle, askQuestion(),
│   │                        #   renderProgressBar(), showResults(), score tracking,
│   │                        #   isComplete / progress / currentQuestion getters
│   │
│   ├── input.js             # I/O utilities — Promise-wrapped readline: prompt(),
│   │                        #   select() (numbered menu), confirm() (y/n), pressEnter()
│   │
│   └── colors.js            # ANSI color helpers — colorize(), red(), green(), cyan(),
│                            #   bold(), dim(), success(), error(), warning(), highlight()
│
└── data/
    └── questions.json       # Static question bank — 15 questions in 3 categories:
                             #   javascript, nodejs, general (each with options,
                             #   zero-based answer index, and explanation string)
```

**Logical Layers:**

| Layer           | File(s)                | Responsibility                                           |
|-----------------|------------------------|----------------------------------------------------------|
| Entry / Control | `index.js`             | App bootstrap, game loop, file loading, error handling   |
| Game Logic      | `src/quiz.js`          | Quiz class, answer scoring, shuffle, results rendering   |
| I/O             | `src/input.js`         | All user input via Promise-wrapped Node.js readline      |
| Presentation    | `src/colors.js`        | Zero-dependency ANSI terminal styling utilities          |
| Data            | `data/questions.json`  | Static question bank organized by category               |

---

## Contributing

Contributions are welcome! To propose a change, follow this workflow:

1. **Fork** the repository on GitHub.
2. **Create a feature branch** from `main`:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Make your changes** and commit them with a descriptive message:
   ```bash
   git commit -m "feat: add TypeScript quiz category"
   ```
4. **Push** your branch to your fork:
   ```bash
   git push origin feature/your-feature-name
   ```
5. **Open a Pull Request** against the `main` branch. Describe what you changed, why, and include any relevant context or screenshots.

**Adding new questions:** Follow the existing schema in `data/questions.json`. Each question object requires:

```json
{
  "question": "Your question text here?",
  "options": ["Option A", "Option B", "Option C", "Option D"],
  "answer": 0,
  "explanation": "Why the correct answer is correct."
}
```

The `answer` field is a **zero-based index** into the `options` array.

---

## License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.

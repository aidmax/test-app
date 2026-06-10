# quiz-cli

An interactive command-line quiz game for learning JavaScript and Node.js — no dependencies, no install step, just Node.js 18+ and your terminal.

## Table of Contents

1. [Project Overview](#project-overview)
2. [Setup Instructions](#setup-instructions)
3. [How to Run](#how-to-run)
4. [Usage Examples](#usage-examples)
5. [File Structure](#file-structure)

## Project Overview

**quiz-cli** is a fully interactive, terminal-based quiz game built with pure Node.js. It was created as an educational tool to help developers reinforce their knowledge of JavaScript and Node.js through hands-on, multiple-choice quizzes delivered directly in the terminal.

### Key Features

- 15 curated questions across three categories: JavaScript Basics, Node.js Fundamentals, and General Programming
- Randomised question order using the Fisher-Yates algorithm on every run
- Coloured terminal output via ANSI colour codes implemented in src/colors.js (zero dependencies)
- Live progress bar that updates after every question
- Immediate feedback with correct/incorrect verdict plus a full explanation after each answer
- Performance messages on the result screen that adapt to your final score
- Play-again loop to restart or change category without re-launching the process
- Robust input handling — invalid entries prompt a retry rather than crashing

### Technology Stack

- Runtime: Node.js 18.0.0 or higher
- Language: JavaScript (ES Modules)
- Dependencies: None — only Node.js built-ins
- Built-in modules: node:fs/promises, node:readline, node:url, node:path
- License: MIT

## Setup Instructions

### Prerequisites

You need Node.js 18.0.0 or higher.

```bash
node --version
```

### Installation

Clone the repository:

```bash
git clone https://github.com/aidmax/test-app.git
cd test-app
```

This project has zero external dependencies, so no npm install step is required.

Run the built-in tests (optional):

```bash
npm test
```

## How to Run

```bash
npm start
```

This executes `node index.js` as defined in package.json. After a welcome banner, you will be prompted to select a quiz category and the number of questions.

## Usage Examples

### Selecting a Category

```
Select a category:
  1) JavaScript Basics
  2) Node.js Fundamentals
  3) General Programming
  4) All categories

Your choice: 2
How many questions? (1-15): 5
```

### Answering a Question

```
Question 3 / 5  [████████░░░░░░░░░░░░] 40%

Which method reads a file asynchronously in Node.js?
  1) fs.readFileSync()
  2) fs.readFile()
  3) fs.open()
  4) fs.read()

Your answer: 2

Correct!
fs.readFile() is the non-blocking, callback-based method for asynchronous file reads.
```

### Results Screen

```
Score: 4 / 5  (80%)

Great job! You know your stuff!

Play again? (y/n):
```

## File Structure

```
test-app/
├── index.js              # Application entry point
├── package.json          # Project metadata and scripts
├── src/
│   ├── colors.js         # ANSI colour utilities
│   ├── input.js          # Promise-based readline wrappers
│   └── quiz.js           # Quiz class — scoring, progress bar, results
└── data/
    └── questions.json    # Question bank — 15 questions with explanations
```

## License

MIT

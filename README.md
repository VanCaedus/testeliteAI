# Quiz CLI 🚀

> An interactive, dependency-free command-line quiz game for practicing JavaScript, Node.js, and general programming fundamentals.

[![Node.js](https://img.shields.io/badge/Node.js-18%2B-339933?logo=node.js&logoColor=white)](https://nodejs.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![ES Modules](https://img.shields.io/badge/JavaScript-ES%20Modules-f7df1e?logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules)

## 📖 Table of Contents

- [About](#-about)
- [Features](#-features)
- [Project Structure](#-project-structure)
- [Prerequisites](#-prerequisites)
- [Getting Started](#-getting-started)
- [Usage](#-usage)
- [Adding Questions](#-adding-questions)
- [How It Works](#-how-it-works)
- [Testing](#-testing)
- [Troubleshooting](#-troubleshooting)
- [Contributing](#-contributing)
- [License](#-license)

## 🌟 About

Quiz CLI is a terminal-based learning game built with modern, dependency-free Node.js. It lets players choose a quiz category, select the number of questions, answer multiple-choice questions, and review incorrect answers with explanations.

The project is also a compact example of common JavaScript and Node.js concepts, including ES modules, asynchronous programming, file-system access, classes, array methods, destructuring, terminal input, and error handling.

## ✨ Features

- Three built-in categories:
  - JavaScript Basics
  - Node.js Fundamentals
  - General Programming
- Multiple-choice questions with input validation.
- Randomized question order using the Fisher–Yates shuffle algorithm.
- Configurable quiz length: all questions, three questions, or five questions when available.
- Colored terminal output using native ANSI escape codes—no external packages required.
- Progress bar, score percentage, performance feedback, and incorrect-answer review.
- Replay support without restarting the application.
- Question explanations displayed after every answer.

## 🗂️ Project Structure

```text
.
├── index.js        # Application entry point and main game loop
├── quiz.js         # Quiz class, scoring, shuffling, and result display
├── input.js        # Readline-based prompts and input validation
├── colors.js       # ANSI color and terminal-style helpers
├── questions.json  # Quiz categories, questions, answers, and explanations
├── package.json    # Project metadata and npm scripts
├── README.md       # Project documentation
└── download        # Binary/encoded repository artifact
```

> **Note:** The current `index.js` imports modules from `src/` and loads questions from `data/questions.json`, while the repository currently stores those files at the root. To run the application, either update those paths in `index.js` to `./input.js`, `./quiz.js`, `./colors.js`, and `questions.json`, or move the files into the referenced `src/` and `data/` directories.

## ⚙️ Prerequisites

- [Node.js](https://nodejs.org/) 18.0.0 or later
- npm, included with Node.js
- A terminal that supports standard ANSI escape codes
- Git, if cloning the repository

No third-party runtime dependencies are required.

## 🚀 Getting Started

Clone the repository and enter the project directory:

```bash
git clone https://github.com/VanCaedus/testeliteAI.git
cd testeliteAI
```

Install the project metadata and prepare npm scripts:

```bash
npm install
```

If you are using the repository exactly as currently structured, fix the import/data paths described in the note above before starting the game. Then run:

```bash
npm start
```

Alternatively, after making the path correction, the executable entry point can be run directly:

```bash
node index.js
```

## 🎮 Usage

1. Choose a category from the numbered list.
2. Select the number of questions.
3. Press **Enter** to begin.
4. Enter the number corresponding to your answer.
5. Review the explanation and continue through the quiz.
6. View your score and incorrect answers.
7. Choose whether to play again.

Example session flow:

```text
Choose a category:
  1. JavaScript Basics
  2. Node.js Fundamentals
  3. General Programming

Your choice (enter number): 1
```

Invalid selections are rejected until a valid option number is entered. At the end of a quiz, results include the category, score, percentage, performance message, and answer review.

## 📝 Adding Questions

Questions are stored in `questions.json`. Add a category under `categories`, then provide a display `name` and a `questions` array. Each question uses this shape:

```json
{
  "question": "What does JSON stand for?",
  "options": [
    "JavaScript Object Notation",
    "Java Standard Object Notation",
    "JavaScript Online Notation",
    "Java Serialized Object Notation"
  ],
  "answer": 0,
  "explanation": "JSON stands for JavaScript Object Notation."
}
```

The `answer` value is a zero-based index into `options`. For example, `0` selects the first option and `2` selects the third option.

## 🧠 How It Works

- `index.js` loads the question data, renders the menu, and controls the application loop.
- `input.js` wraps Node.js `readline` APIs in Promise-based helpers for selections, confirmations, and pauses.
- `quiz.js` manages the quiz state, shuffles questions, evaluates answers, tracks progress, and renders results.
- `colors.js` provides reusable ANSI terminal styling functions.
- `questions.json` acts as the content source and can be edited without changing quiz logic.

The project uses native Node.js modules such as `node:fs/promises`, `node:path`, `node:url`, and `node:readline`.

## 🧪 Testing

The package defines a Node.js test command:

```bash
npm test
```

At present, the repository does not contain dedicated test files. The command uses Node’s built-in test runner and should be expanded with tests for question loading, input validation, scoring, shuffling, and result calculations as the project grows.

## 🔧 Troubleshooting

### `ERR_MODULE_NOT_FOUND`

Confirm that the import paths in `index.js` match the actual repository layout. The current source files are in the root, but the imports refer to `src/` and `data/` directories. See [Getting Started](#-getting-started).

### Colors do not display correctly

Run the application in a terminal with ANSI color support. Some older Windows terminals may require Windows Terminal or another modern terminal emulator.

### The quiz exits with a JSON error

Validate `questions.json` using a JSON-aware editor or a command such as:

```bash
node -e "JSON.parse(require('fs').readFileSync('questions.json', 'utf8')); console.log('Valid JSON')"
```

## 🤝 Contributing

Contributions are welcome:

1. Fork the repository.
2. Create a feature branch: `git checkout -b feature/my-improvement`.
3. Make focused changes and update the documentation when needed.
4. Run `npm test` and manually verify the CLI with `npm start`.
5. Commit your changes and open a pull request.

When adding questions, keep wording clear, use plausible distractors, preserve the zero-based answer index, and include an explanation where helpful.

## 📜 License

This project is distributed under the [MIT License](https://opensource.org/licenses/MIT). See `package.json` for the declared license.
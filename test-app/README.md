# 📚 Quiz CLI

![Node.js](https://img.shields.io/badge/Node.js-18+-green)
![License](https://img.shields.io/badge/license-MIT-blue)
![Type](https://img.shields.io/badge/type-module-orange)
![Version](https://img.shields.io/badge/version-1.0.0-brightgreen)

An interactive command-line quiz game built with **pure Node.js** — no external dependencies. Test your knowledge across JavaScript, Node.js, and general programming topics right from your terminal.

---

## ✨ Features

- **🗂️ Multiple Categories** — Choose from JavaScript Basics, Node.js Fundamentals, and General Programming
- **🔀 Shuffled Questions** — Questions are randomized each session using the Fisher-Yates algorithm
- **🎯 Flexible Question Count** — Play with 3, 5, or all available questions per category
- **📊 Progress Bar** — Visual progress tracker displayed during the quiz
- **💡 Explanations** — Each question includes a detailed explanation of the correct answer
- **📝 Answer Review** — Missed questions are listed at the end for easy review
- **🎨 Colorized Output** — Rich terminal UI using ANSI escape codes (zero dependencies)
- **🔁 Play Again Loop** — Replay immediately without restarting the process
- **⚡ Zero Dependencies** — Built entirely with Node.js built-in modules

---

## 🖥️ Demo

```
  ╔═══════════════════════════════════════════╗
  ║                                           ║
  ║   📚 QUIZ CLI                             ║
  ║   Test your programming knowledge!        ║
  ║                                           ║
  ╚═══════════════════════════════════════════╝

Choose a category:

  1. JavaScript Basics
  2. Node.js Fundamentals
  3. General Programming

Your choice (enter number): 1

How many questions?

  1. All questions
  2. 3 questions
  3. 5 questions

Your choice (enter number): 2

[██████████░░░░░░░░░░░░░░░░░░░░] 33%
Question 1 of 3

What keyword is used to declare a constant in JavaScript?

  1. var
  2. let
  3. const
  4. define

Your choice (enter number): 3

✓ Correct!
💡 The 'const' keyword declares a block-scoped constant that cannot be reassigned.

══════════════════════════════════════════════════
  📊 QUIZ RESULTS
══════════════════════════════════════════════════

  Category: JavaScript Basics
  Score: 3/3 (100%)

  🏆 Perfect score! Amazing!

══════════════════════════════════════════════════

Would you like to play again? (y/n):
```

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| **Node.js 18+** | JavaScript runtime |
| **ES Modules** (`import`/`export`) | Module system |
| **`node:fs/promises`** | Async file reading |
| **`node:readline`** | Interactive terminal input |
| **`node:path`** / **`node:url`** | Path resolution for ES modules |
| **ANSI Escape Codes** | Terminal colorization (no libs needed) |
| **JSON** | Question data storage |

---

## 📁 Project Structure

```
test-app/
├── data/
│   └── questions.json     # Quiz questions, options, answers & explanations (3 categories, 15 questions)
├── src/
│   ├── colors.js          # ANSI terminal color utilities (zero dependencies)
│   ├── input.js           # User input helpers: prompt, select, confirm, pressEnter
│   └── quiz.js            # Quiz class: game logic, scoring, progress bar, results display
├── index.js               # Entry point: app loop, banner, category/question selection
├── package.json           # Project manifest, scripts, engine requirements
└── README.md              # This file
```

---

## ✅ Prerequisites

- **Node.js** >= `18.0.0`
- **npm** >= `8.0.0` _(comes bundled with Node.js 18)_

> This project uses **zero external dependencies** — no `npm install` needed!

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/romamatvej/EliteA_Test.git
cd EliteA_Test/test-app
```

### 2. Run the application

```bash
npm start
```

Or directly with Node:

```bash
node index.js
```

> ✅ No `npm install` required — the project has no external dependencies!

---

## 🎮 Usage

Once started, the application guides you interactively:

1. **Select a category** — enter the number for your chosen topic
2. **Choose question count** — pick 3, 5, or all questions
3. **Answer questions** — enter the number of your chosen answer
4. **Review results** — see your score, performance message, and missed questions
5. **Play again** — type `y` to restart or `n` to exit

### Available Categories

| Category | Description | Questions |
|---|---|---|
| **JavaScript Basics** | Variables, types, array methods, operators | 5 |
| **Node.js Fundamentals** | Modules, event loop, CLI, ES6 imports | 5 |
| **General Programming** | APIs, recursion, JSON, callbacks, version control | 5 |

---

## ⚙️ Configuration

### Adding New Questions

Edit `data/questions.json` to add your own questions. Follow this schema:

```json
{
  "categories": {
    "your_category_id": {
      "name": "Display Name",
      "questions": [
        {
          "question": "Your question text?",
          "options": ["Option A", "Option B", "Option C", "Option D"],
          "answer": 0,
          "explanation": "Why this answer is correct."
        }
      ]
    }
  }
}
```

> **Note:** `"answer"` is the **zero-based index** of the correct option in the `"options"` array.

### Adding New Categories

Simply add a new key under `"categories"` in `questions.json` — the app dynamically reads all categories at startup.

---

## ⚙️ How It Works

```
index.js (Entry Point)
    │
    ├── loadQuestions()       Reads & parses data/questions.json via fs/promises
    ├── showBanner()          Renders the ANSI welcome banner
    │
    └── main() loop
          │
          ├── input.js → select()    User picks a category
          ├── input.js → select()    User picks question count
          │
          ├── quiz.js → new Quiz()   Instantiates quiz with shuffled questions
          │     ├── shuffle()        Fisher-Yates randomization
          │     ├── askQuestion()    Displays question, captures answer, shows feedback
          │     ├── renderProgressBar()  Visual [████░░░░] progress display
          │     └── showResults()    Final score, performance message, review of missed answers
          │
          └── input.js → confirm()   "Play again?" loop
```

**Flow Summary:**
1. `index.js` loads questions from `data/questions.json` using the async `fs/promises` API
2. The user navigates menus via `src/input.js` (built on `node:readline`)
3. A `Quiz` instance from `src/quiz.js` manages game state, scoring, and display
4. All terminal styling is handled by `src/colors.js` using raw ANSI codes

---

## 🧠 Key Concepts Demonstrated

This project is an educational exercise showcasing core Node.js and JavaScript patterns:

| Concept | Where Used |
|---|---|
| **ES Modules** (`import`/`export`) | All source files |
| **Async/Await & Promises** | `loadQuestions()`, `askQuestion()`, all input helpers |
| **Classes & OOP** | `Quiz` class in `src/quiz.js` |
| **Getters** | `currentQuestion`, `isComplete`, `progress`, `totalQuestions` |
| **Array Methods** (`map`, `filter`, `forEach`, `find`) | `index.js`, `quiz.js` |
| **Destructuring** | Answer swapping in `shuffle()`, return values from `select()` |
| **Template Literals** | Throughout all display logic |
| **Error Handling** (`try/catch/finally`) | `main()` in `index.js` |
| **Fisher-Yates Shuffle** | `shuffle()` in `quiz.js` |
| **ANSI Escape Codes** | `src/colors.js` |
| **`__dirname` in ES Modules** | `fileURLToPath` + `dirname` in `index.js` |
| **Readline / Interactive CLI** | `src/input.js` |

---

## 🤝 Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a new branch: `git checkout -b feature/your-feature-name`
3. Make your changes and commit: `git commit -m 'Add some feature'`
4. Push to the branch: `git push origin feature/your-feature-name`
5. Open a Pull Request

Feel free to open an issue for bug reports, feature requests, or new question suggestions!

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

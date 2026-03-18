# Quiz CLI (EliteA_Test)

An interactive command-line quiz game implemented in Node.js. This lightweight project is designed as a small educational demo that showcases modern JavaScript/Node.js features and provides a fun way to test programming knowledge.

Key features:
- Multiple categories of questions (JavaScript, Node.js, General programming)
- Interactive command-line interface
- Progress display, score tracking, and review of incorrect answers
- No external dependencies — uses built-in Node.js modules and simple utilities

Project structure:

- test-app/
  - data/questions.json        — Quiz questions and categories
  - index.js                  — CLI entry point
  - package.json              — Project metadata & scripts
  - src/
    - colors.js               — Small ANSI color utilities
    - input.js                — Readline-based input helpers
    - quiz.js                 — Quiz game logic (Quiz class)

Getting started

Prerequisites
- Node.js 18 or newer (package.json specifies node >= 18)

Run locally

1. Clone the repository:

   git clone https://github.com/romamatvej/EliteA_Test.git
   cd EliteA_Test/test-app

2. Install (no external dependencies required, but good practice):

   npm install

3. Run the quiz:

   npm start

Usage
- Select a category.
- Choose how many questions you'd like to answer.
- Enter the number corresponding to your selected option for each question.
- After the quiz, your score and review of incorrect answers will be displayed.

Adding or editing questions
- Questions are stored in test-app/data/questions.json.
- Each category has a name and an array of questions. Each question object includes:
  - question: string
  - options: array of strings
  - answer: index of correct option (0-based)
  - explanation: optional string to show after answering

Development notes
- The project uses ES modules (import/export) and the built-in readline module for user input.
- Colors are implemented via simple ANSI escape sequences in src/colors.js.
- Quiz logic is encapsulated in the Quiz class (src/quiz.js) and demonstrates array methods, destructuring, and basic OOP patterns.

Testing
- The repo includes a test script (node --test), but no tests are provided by default. You can add Node.js tests per your preferred framework or using the built-in Node test runner.

Contributing
- Contributions are welcome! Suggested workflow:
  1. Fork the repository.
  2. Create a feature branch (e.g., feature/add-question).
  3. Make changes and open a pull request.

License
- MIT

Acknowledgements
- This repository is a compact educational example for building CLI tools with Node.js.

---
Created on branch: feature/add-readme

If you want this README adjusted (format, extra sections, badges), tell me what to include and I will update it.
# Quiz CLI

An interactive Node.js command-line quiz game for learning JavaScript, Node.js, and general programming concepts.

## Features

- Interactive terminal-based quiz flow
- Quiz categories:
  - JavaScript Basics
  - Node.js Fundamentals
  - General Programming
- Choose all questions or a three- or five-question quiz
- Randomized question order using the Fisher–Yates algorithm
- Numbered answer selection with input validation
- Immediate correctness feedback and explanations
- Progress bar during the quiz
- Final score and percentage
- Review of incorrectly answered questions
- ANSI terminal colors without external dependencies
- Option to start another quiz after completing one

## Requirements

- Node.js 18 or newer
- npm, included with Node.js
- A terminal that supports standard ANSI color escape codes

The project uses native ES modules and has no external npm dependencies.

## Installation

Clone the repository and enter the project directory:

```bash
git clone https://github.com/HarshithaEpam/test-app.git
cd test-app
```

Install the project metadata and prepare the local npm environment:

```bash
npm install
```

There are currently no external dependencies to install.

## Repository Layout

The source files currently exposed in the repository are located at the project root:

```text
.
├── colors.js
├── index.js
├── input.js
├── package.json
├── questions.json
└── quiz.js
```

- `index.js` — application entry point and main quiz loop
- `input.js` — readline-based input and selection helpers
- `quiz.js` — quiz flow, scoring, progress, and results
- `colors.js` — ANSI terminal-color utilities
- `questions.json` — quiz categories and question data
- `package.json` — project metadata and npm scripts

The `._*` and `.DS_Store` files are macOS metadata artifacts and are not part of the application.

## Important Path Note

The current `index.js` references files using these paths:

```js
./src/input.js
./src/quiz.js
./src/colors.js
data/questions.json
```

However, the repository listing contains the corresponding files at the project root:

```text
input.js
quiz.js
colors.js
questions.json
```

The `src/` directory and `data/questions.json` path were not available in the inspected repository. As a result, the application may fail with module- or file-not-found errors when started from this checkout.

Before running the application, ensure that the paths used by `index.js` match the files in the repository. Either:

- Update the imports and question-data path in `index.js` to use the root-level files, or
- Organize the files into the `src/` and `data/` directories expected by `index.js`.

## Running the Application

The declared start command is:

```bash
npm start
```

This runs:

```bash
node index.js
```

When the referenced files are available at the paths expected by `index.js`, the application:

1. Displays a welcome banner.
2. Prompts for a quiz category.
3. Prompts for the number of questions.
4. Runs the selected quiz.
5. Shows the final score and incorrect-answer review.
6. Offers to start another quiz.

## Question Data Format

Quiz content is stored in `questions.json`. Each category contains question objects with this structure:

```json
{
  "question": "Question text",
  "options": [
    "Option 1",
    "Option 2",
    "Option 3",
    "Option 4"
  ],
  "answer": 0,
  "explanation": "Explanation shown after answering."
}
```

The `answer` property is a zero-based index into the `options` array:

- `0` selects the first option
- `1` selects the second option
- `2` selects the third option
- `3` selects the fourth option

The current data defines three categories with five questions each.

## npm Scripts

### Start the quiz

```bash
npm start
```

Runs the application with Node.js.

### Run tests

```bash
npm test
```

Runs Node.js's built-in test runner:

```bash
node --test
```

No test files were present in the inspected repository, so this command may complete without running tests.

## Configuration

The application does not document any environment variables, external services, databases, or configuration files beyond `questions.json`.

To change the quiz content, edit the category and question data in `questions.json` while preserving the documented data structure.

## License

This project is licensed under the MIT License, as specified in `package.json`.

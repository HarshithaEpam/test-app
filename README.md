# Quiz CLI

An interactive command-line quiz game for learning JavaScript, Node.js, and general programming concepts. The application runs in a terminal, lets users choose a quiz category and question count, provides immediate feedback and explanations, and displays a final score.

## Project Status

The project is currently an incomplete or inconsistent checkout.

`index.js` expects application modules and quiz data at these paths:

```text
src/input.js
src/quiz.js
src/colors.js
data/questions.json
```

However, the `main` branch currently contains the corresponding files at the repository root:

```text
input.js
quiz.js
colors.js
questions.json
```

Because of this path mismatch, `npm start` is expected to fail until the imports and data path are aligned with the checked-in file locations, or the files are moved into the directories expected by `index.js`.

No README, test files, dependency lockfile, CI workflow, Dockerfile, or deployment configuration is currently present.

## Features

- Interactive terminal-based quiz experience
- Category selection
- Configurable number of questions
- Multiple-choice questions
- Randomized question order using the Fisher–Yates algorithm
- Immediate correct and incorrect answer feedback
- Explanations for quiz answers
- Progress tracking
- Final percentage score
- Performance messages based on the score
- Review of incorrectly answered questions
- Option to play multiple rounds
- ANSI terminal colors and formatting without external dependencies

## Quiz Categories

The included quiz data defines three categories:

| Category | Description |
|---|---|
| `javascript` | JavaScript Basics |
| `nodejs` | Node.js Fundamentals |
| `general` | General Programming |

Each category contains five multiple-choice questions. Every question includes:

- The question text
- A list of answer options
- The correct answer
- An explanation

Topics include JavaScript constants, arrays, strict equality, primitive values, `typeof null`, Node.js file systems, the event loop, `npm init`, `process.argv`, ES modules, APIs, recursion, JSON, callbacks, and version control.

## Requirements

- Node.js `18.0.0` or newer
- npm, included with Node.js
- A terminal that supports standard ANSI escape sequences for colored output

The project does not declare external npm dependencies.

## Installation

Clone the repository and enter the project directory:

```bash
git clone https://github.com/HarshithaEpam/test-app.git
cd test-app
```

The project has no declared runtime dependencies, so there is currently no dependency installation step beyond installing Node.js. If dependencies are added in the future, run:

```bash
npm install
```

## Resolving the Current File Layout

Before starting the application, the paths used by `index.js` must match the files in the repository.

Currently, `index.js` imports:

```js
./src/input.js
./src/quiz.js
./src/colors.js
```

and reads:

```text
data/questions.json
```

The checked-in files are instead located at:

```text
input.js
quiz.js
colors.js
questions.json
```

The application can be made consistent by either:

1. Updating `index.js` to use the root-level files and data file, or
2. Moving the application modules into `src/` and the question data into `data/`.

This repository does not currently include those directories, so the exact preferred layout is not defined by the available project files.

## Running the Application

The package defines the following start command:

```bash
npm start
```

This runs:

```bash
node index.js
```

When the file paths are corrected, the application is expected to:

1. Create a terminal readline interface.
2. Load the quiz questions.
3. Display a colored welcome banner.
4. Prompt for a quiz category.
5. Prompt for the number of questions.
6. Run the quiz.
7. Display feedback and explanations.
8. Show the final result.
9. Ask whether to start another quiz.
10. Close the readline interface when finished.

You can also run the entry point directly:

```bash
node index.js
```

With the repository in its current state, both commands are expected to fail because the paths referenced by `index.js` do not exist.

## Project Structure

```text
.
├── colors.js        # ANSI color and terminal formatting helpers
├── index.js         # CLI entry point and application loop
├── input.js         # Readline-based input utilities
├── package.json      # Node.js package metadata and scripts
├── questions.json    # Quiz categories and questions
└── quiz.js           # Quiz class and quiz execution logic
```

The repository also contains macOS metadata and resource-fork files such as `.DS_Store` and `._*` files. These are not part of the application logic and should not be used as source files.

## Application Modules

### `index.js`

The main command-line entry point. It coordinates the application lifecycle, including loading quiz data, prompting the user, running quizzes, displaying results, handling errors, and closing the readline interface.

### `input.js`

Provides interactive input helpers built on Node.js's built-in `readline` module:

- `createInterface()`
- `prompt(rl, question)`
- `select(rl, question, options)`
- `confirm(rl, question)`
- `pressEnter(rl, message)`

The `select` helper displays numbered options and continues prompting until the user enters a valid selection.

### `quiz.js`

Exports the `Quiz` class. The class manages question randomization, quiz progress, scoring, answer tracking, feedback, explanations, and final results.

Important properties and getters include:

```text
questions
categoryName
currentIndex
score
answers
currentQuestion
totalQuestions
isComplete
progress
```

### `colors.js`

Provides terminal color and style functions using ANSI escape codes. It does not require an external color library.

Available formatting helpers include:

```text
red
green
yellow
blue
cyan
magenta
bold
dim
success
error
warning
info
highlight
```

The central helper is:

```js
colorize(text, ...styles)
```

### `questions.json`

Stores the quiz categories and question definitions. Each question has the following structure:

```json
{
  "question": "Question text",
  "options": ["Option A", "Option B", "Option C"],
  "answer": "Correct answer",
  "explanation": "Explanation of the answer"
}
```

## Configuration

No environment variables or external configuration files are documented.

Quiz content is stored in `questions.json`. To update the available questions, preserve the existing category and question structure:

- Each category should have a category identifier.
- Each category should provide a display name.
- Each question should include `question`, `options`, `answer`, and `explanation`.

The data file path must also match the path used by `index.js`.

## npm Scripts

| Command | Description |
|---|---|
| `npm start` | Runs the CLI with `node index.js` |
| `npm test` | Runs Node.js's built-in test runner with `node --test` |

## Testing

The package defines a test command:

```bash
npm test
```

This executes:

```bash
node --test
```

No test files are currently visible in the repository, so the command may complete without running tests or may require test files to be added.

## Development Notes

The project uses ECMAScript modules, enabled by the following setting in `package.json`:

```json
{
  "type": "module"
}
```

Source files use `import` and `export` syntax. Node.js 18 or newer is required according to the package engines declaration.

The application uses only Node.js built-in modules and local project modules. No third-party dependencies are declared.

## Contributing

Before contributing:

1. Confirm that the application file layout and import paths are consistent.
2. Keep quiz data compatible with the structure used by `questions.json`.
3. Add tests for new quiz behavior where appropriate.
4. Run the available npm scripts before submitting changes:

   ```bash
   npm test
   npm start
   ```

5. Avoid committing generated files or macOS metadata such as `.DS_Store` and `._*` files.

## License

No license file or license declaration was found in the repository. Licensing information should be added before distributing the project.

# quiz-cli

A terminal-based quiz application built with Node.js. It lets users choose a quiz category, select the number of questions, answer interactively, and review their results with explanations for incorrect answers.

The project contains quiz categories covering JavaScript, Node.js, and general programming concepts.

## Requirements

- Node.js 18 or later
- npm, included with Node.js
- A terminal that supports ANSI color escape sequences

The project has no external runtime dependencies.

## Installation

Clone the repository and install the project:

```bash
git clone https://github.com/HarshithaEpam/test-app.git
cd test-app
npm install
```

Because the project does not declare external dependencies, `npm install` primarily initializes the local Node.js project environment.

## Running the Application

Start the quiz CLI with:

```bash
npm start
```

The application is intended to:

1. Display a colored welcome banner.
2. Prompt you to select a quiz category.
3. Prompt you to select the number of questions.
4. Present questions and answer choices interactively.
5. Display feedback and explanations after each answer.
6. Show your final score and percentage.
7. List incorrect answers for review.
8. Offer the option to play again.

## Important Repository Layout Note

The current repository listing contains the application files and quiz data at the repository root:

```text
test-app/
├── colors.js
├── index.js
├── input.js
├── package.json
├── questions.json
└── quiz.js
```

However, `index.js` currently imports application modules from a `src/` directory and loads quiz data from a `data/` directory:

```js
./src/input.js
./src/quiz.js
./src/colors.js
```

```js
data/questions.json
```

The listed repository contents do not include those paths. As a result, `npm start` may fail with a module or file-not-found error unless the missing directories exist outside the returned repository listing or the files are moved/references are updated.

To run the application successfully, the paths referenced by `index.js` must match the files committed to the repository. In the current visible layout, the corresponding files are:

```text
input.js
quiz.js
colors.js
questions.json
```

## Available Commands

| Command | Description |
|---|---|
| `npm start` | Starts the quiz application with `node index.js` |
| `npm test` | Runs Node.js’s built-in test runner |

The repository does not contain automated test files, so `npm test` may complete without running tests or may report that no tests were found, depending on the Node.js version and test-runner behavior.

## Quiz Categories

The quiz data is stored in `questions.json`. The available categories are:

- **JavaScript Basics**
- **Node.js Fundamentals**
- **General Programming**

Each category contains five questions in the current data set.

Topics include:

- JavaScript variable declarations
- Arrays
- Strict equality
- Node.js modules
- The Node.js event loop
- npm
- Command-line arguments
- APIs
- Recursion
- JSON
- Callbacks
- Version control

## Quiz Data Format

Quiz data is represented as JSON with a `categories` object:

```json
{
  "categories": {
    "javascript": {
      "name": "JavaScript Basics",
      "questions": [
        {
          "question": "What keyword is used to declare a constant in JavaScript?",
          "options": [
            "var",
            "let",
            "const",
            "define"
          ],
          "answer": 2,
          "explanation": "The 'const' keyword declares a block-scoped constant that cannot be reassigned."
        }
      ]
    }
  }
}
```

Each question contains:

| Property | Description |
|---|---|
| `question` | The question text |
| `options` | An array of possible answers |
| `answer` | The correct answer index |
| `explanation` | Explanation displayed after answering |

The current example uses zero-based answer indexes, so `2` refers to the third option.

## Features

### Interactive Terminal Input

`input.js` provides reusable helpers based on Node.js’s built-in `readline` module:

- `createInterface()`
- `prompt()`
- `select()`
- `confirm()`
- `pressEnter()`

The `select()` helper displays numbered choices and continues prompting until a valid option number is entered.

### Quiz Management

`quiz.js` exports the `Quiz` class, which:

- Shuffles questions using the Fisher–Yates algorithm
- Tracks the current question
- Tracks the current score
- Records submitted answers
- Reports quiz progress
- Detects when the quiz is complete
- Displays feedback and explanations
- Shows incorrect answers during result review

The class exposes the following getters:

- `currentQuestion`
- `totalQuestions`
- `isComplete`
- `progress`

### Terminal Colors

`colors.js` provides ANSI color helpers without an external package.

Available generic and basic styles include:

- `colorize(text, ...styles)`
- `red`
- `green`
- `yellow`
- `blue`
- `cyan`
- `magenta`
- `bold`
- `dim`

Semantic styles include:

- `success`
- `error`
- `warning`
- `info`
- `highlight`

## Project Structure

```text
.
├── colors.js       # ANSI terminal color helpers
├── index.js        # CLI application entry point
├── input.js        # Interactive readline input helpers
├── package.json     # Project metadata and npm scripts
├── questions.json   # Quiz categories and questions
├── quiz.js         # Quiz class and quiz behavior
├── .DS_Store       # macOS filesystem metadata
└── ._*             # macOS AppleDouble metadata artifacts
```

The `.DS_Store` and `._*` files are operating-system metadata artifacts and are not required by the quiz application.

## Testing

Run the configured test command with:

```bash
npm test
```

The command invokes Node.js’s built-in test runner:

```bash
node --test
```

No test files are currently included in the repository.

## Configuration

Project configuration is defined in `package.json`:

```json
{
  "type": "module",
  "engines": {
    "node": ">=18.0.0"
  }
}
```

The project uses ECMAScript modules, so JavaScript files use `import` and `export` syntax.

There are no documented environment variables, external services, databases, or configuration files.

## Dependencies

No external npm dependencies are declared. The application uses built-in Node.js functionality, including:

- `fs`
- `path`
- `url`
- `readline`
- Node.js’s built-in test runner

## Deployment

No deployment configuration, Dockerfile, hosting configuration, or CI workflow is included. The application is designed to run locally from a terminal using Node.js.

## License

No license file or license declaration was found in the repository.

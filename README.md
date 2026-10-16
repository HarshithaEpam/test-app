# Quiz CLI

A Node.js ES module command-line quiz application. The app presents questions by category, lets users choose the number of questions, tracks progress and scoring, provides answer feedback and explanations, reviews incorrect answers, and supports replaying the quiz.

## Prerequisites

- Node.js 18 or later
- npm, included with Node.js

The project uses native Node.js modules and has no third-party dependencies.

## Project Status

> **Important:** `index.js` currently imports the following files from `src`:
>
> - `./src/input.js`
> - `./src/quiz.js`
> - `./src/colors.js`
>
> It also loads quiz data from `data/questions.json`.
>
> On the inspected main branch, these files are stored at the repository root:
>
> - `input.js`
> - `quiz.js`
> - `colors.js`
> - `questions.json`
>
> Therefore, `npm start` is expected to fail until the import and data paths or the repository layout are corrected.

## Installation

Clone the repository and enter its directory:

```bash
git clone https://github.com/HarshithaEpam/test-app.git
cd test-app
```

There are no dependencies to install. The project does not contain a lockfile or third-party packages.

Although `npm install` is unnecessary, it can be run if npm metadata needs to be initialized locally:

```bash
npm install
```

## Running the Application

The declared start command is:

```bash
npm start
```

This runs:

```bash
node index.js
```

Because of the current source/layout mismatch described above, the command is expected to fail until the referenced `src/` and `data/` paths are made consistent with the files present in the repository.

## Quiz Workflow

When the application is functioning with corrected paths, `index.js` is designed to:

1. Create a Node.js readline interface.
2. Load quiz questions.
3. Allow the user to select a category.
4. Allow the user to select the number of questions.
5. Run the quiz.
6. Display progress, feedback, and results.
7. Review incorrect answers.
8. Ask whether the user wants to replay.
9. Handle errors and close the readline interface.

## Question Format

Questions are stored as JSON objects grouped in `questions.json`. Each question uses the following fields:

| Field | Description |
| --- | --- |
| `question` | The question text |
| `options` | The available answer choices |
| `answer` | The zero-based index of the correct option |
| `explanation` | An explanation shown as part of answer feedback or review |

The current question data includes these categories:

- JavaScript Basics
- Node.js Fundamentals
- General Programming

Each category currently contains five questions.

A representative question structure is:

```json
{
  "question": "Question text",
  "options": [
    "First option",
    "Second option",
    "Third option"
  ],
  "answer": 1,
  "explanation": "Explanation of the correct answer."
}
```

The `answer` value is zero-based: `0` refers to the first option, `1` to the second option, and so on.

## Implementation Details

### `index.js`

The application entry point:

- Creates the readline interface.
- Loads question data using Node.js file and path utilities.
- Presents category and question-count selection.
- Instantiates and runs the `Quiz` class.
- Displays results and supports replay.
- Includes error handling.
- Imports `node:fs/promises`, `node:url`, and `node:path`.

The current imports reference `src/` and `data/` paths that do not match the inspected main-branch layout.

### `input.js`

Provides readline-based input helpers:

- `createInterface`
- `prompt`
- `select`
- `confirm`
- `pressEnter`

### `quiz.js`

Implements the `Quiz` class, including:

- Fisher–Yates question randomization
- Score tracking
- Progress display
- Answer feedback
- Explanations
- A progress bar
- Results presentation
- Incorrect-answer review

### `colors.js`

Provides ANSI terminal styling without using third-party libraries.

## Project Structure

The inspected main branch contains the following relevant files:

```text
.
├── colors.js
├── index.js
├── input.js
├── package.json
├── questions.json
└── quiz.js
```

The repository also contains `.DS_Store` and macOS `._*` metadata files.

The paths currently referenced by `index.js`—`src/` and `data/`—are not present in the inspected root-level layout.

## Available npm Scripts

| Command | Description |
| --- | --- |
| `npm start` | Runs `node index.js` |
| `npm test` | Runs `node --test` |

## Testing

Run the declared test command with:

```bash
npm test
```

This executes:

```bash
node --test
```

No test files were found in the inspected repository, so there are currently no repository tests to run.

The project also has no configured linting, build, or type-checking commands.

## Configuration

No environment variables or configuration files are documented or required by the repository.

Quiz content is stored in:

```text
questions.json
```

The application currently expects the data file at:

```text
data/questions.json
```

This expected path does not match the inspected main-branch layout.

## Deployment

No deployment configuration or deployment workflow was found. The project is currently structured as a local Node.js command-line application.

## Known Limitations

- The declared start command is expected to fail because `index.js` references files under `src/` and `data/`, while the inspected main branch stores the modules and question data at the repository root.
- No automated test files were found.
- No linting, build, or type-checking configuration is provided.
- No CI workflow is configured.
- No deployment configuration is provided.
- The project has no declared license file.
- The repository includes macOS metadata files such as `.DS_Store` and `._*`.

## License

No license file was found in the repository.

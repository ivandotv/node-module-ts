# Typescript Node Module Template

Opinionated template repository for starting new node modules with typescript.
Since node module is a bulding block of larger applications you can easily extend this template repository to do much more.

## Getting Started

1. Run `npx npm-check-updates` to see if any packages need upgrading or `npm outdated` from minor updates.
2. Run `npm install`

## What's Inside

- Typescript is set to `strict` configuration with source map generation.
- ESLint is set up to use [standardJS configuration](https://standardjs.com/index.html#typescript) for typescript.
- with a few overrides which I think are common sense. You can see the overrides inside the [.eslintrc.js](.eslintrc.js) file.
- Unit testing is done via [Jest](https://jestjs.io/) in combination with [ts-jest](https://kulshekhar.github.io/ts-jest)
- [Prettier](https://prettier.io/) with a [few custom rules](.prettier.rc).
- Code coverage.

### Tasks

- `prepublishOnly`: run before publishing the module to npm.
- `build`: build typescript.
- `build:watch`: build and watch typescript for changes.
- `test`: run all tests and generate code coverage.
- `test:watch`: run and watch tests for changes (with [typeahead](https://www.npmjs.com/package/jest-watch-typeahead) feature)
- `ci:test` task that is executed by CI (runs tests and uploads code coverage).
- `format`: format all files with [prettier](https://prettier.io) (`tests` and `src` directories).

- `fix:src`: run ESLint on `src` directory with `--fix` flag.
- `fix:tests`: run ESLint on `tests` directory with `--fix` flag.
- `fix`: run `fix:src` and `fix:tests` task in paralll.
- `docs`: generate typescript documentation via [typedoc](https://typedoc.org)

### Continous Integration

[CircleCI](https://circleci.com/) is used for continous integration.

Tests are run for node versions 8, 10 and 12.

CircleCI is also set up to upload code coverage to [codecov.io](https://codecov.io) however you can also use [coveralls](https://coveralls.io) for code coverage ( it's currently commented out).

### Git Hooks

There is one git hook setup via [husky](https://www.npmjs.com/package/husky) package in combination with [lint-staged](https://www.npmjs.com/package/lint-staged). Before committing the files all staged files will be run through ESLint and Prettier.

### Debugging

If you are using VS Code as your editor,
there is one debug configuration which is set up to debug currently focused test file inside the editor.

### Typescript Documentation Generator

Typescript documentation is generated via [typedoc](https://typedoc.org).
Currently, it is set up to go into `docs/api` directory and it is generated in markdown so it can be displayed on Github.

- Private members are excluded.
- Only exported properties are documented.

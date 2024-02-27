# Project Guidelines

## JavaScript

### Files

The code must be divided in simple pieces, using import and export to connect the pieces of code. Try to avoid the usage of export default, always import declaring wich elements your'e using from the source code.

#### File names

File names must be all lowercase and may include underscores (_), but no additional punctuation.

### Formatting

#### Blocks

Braces are required for all control structures (i.e. if, else, for, do, while, as well as any others), even if the body contains only a single statement.

* No line break before the opening brace.
* Line break after the opening brace.
* Line break before the closing brace.
* Line break after the closing brace.
* Allways add one identation tab inside the block

For empty blocks the braces open and close at the same line.

##### Example

```JavaScript
class InnerClass {
  constructor() {}

  method(foo) {
    if (condition(foo)) {
      try {
        something();
      }
      catch (err) {
        recover();
      }
    }
  }
}
```

#### Block itentation: 2 spaces

Each time a new block or block-like construct is opened, the indent increases by two spaces. When the block ends, the indent returns to the previous indent level. The indent level applies to both code and comments throughout the block.

#### Statements

##### One statement per line

Each statement is followed by a line-break.

##### Semicolons are required

Every statement must be terminated with a semicolon.

#### Line-wrapping

Line wrapping is breaking a chunk of code into multiple lines to obey column limit (80 columns), where the chunk could otherwise legally fit in a single line.

There is no comprehensive, deterministic formula showing exactly how to line-wrap in every situation. Very often there are several valid ways to line-wrap the same piece of code.

Note: While the typical reason for line-wrapping is to avoid overflowing the column limit, even code that would in fact fit within the column limit may be line-wrapped at the author's discretion.

##### Where to break

The prime directive of line-wrapping is: prefer to break at a higher syntactic level.

Preferred:

```JavaScript
currentEstimate =
    calc(currentEstimate + x * currentEstimate) /
    2.0;
```

Avoid:

```JavaScript
currentEstimate = calc(currentEstimate + x *
    currentEstimate) / 2.0;
```

##### Indent continuation

Add 4 spaces of identation from the original line, keep this identation level until the end of the line.

##### Function arguments

Prefer to put all function arguments on the same line as the function name. If doing so would exceed the 80-column limit, the arguments must be line-wrapped in a readable way.You may put each argument on its own line to enhance readability. Indentation should be four spaces.

###### Example

```JavaScript
// Four-space, one argument per line.  Works with long function names,
// survives renaming, and emphasizes each argument.
function doSomething(
    veryDescriptiveArgumentNumberOne,
    veryDescriptiveArgumentTwo,
    tableModelEventHandlerProxy,
    artichokeDescriptorAdapterIterator) {
  // …
}
```

### Comments

Block comments are indented at the same level as the surrounding code. They may be in /* … \*/ or //-style. For multi-line /* … */ comments, subsequent lines must start with * aligned with the * on the previous line, to make comments obvious with no extra context.

```JavaScript
/*
 * This is
 * okay.
 */

// And so
// is this.

/* This is fine, too. */
```

### Languaje features

#### Local variable declarations

##### Use const and let

Declare all local variables with either const or let. Use const by default, unless a variable needs to be reassigned. The var keyword must not be used.

##### One variable per declaration

Every local variable declaration declares only one variable: declarations such as

```JavaScript
let a = 1, b = 2;
```

are not used.

##### Declared when needed, initialized as soon as possible

Local variables are not habitually declared at the start of their containing block or block-like construct. Instead, local variables are declared close to the point they are first used (within reason), to minimize their scope.

### Naming Conventions

#### General Rules for Identifiers

* Use only ASCII letters, digits, underscores in some cases.
* Names should be descriptive and avoid abbreviations unless they are widely understood.
* Avoid abbreviations that could be ambiguous or unfamiliar outside your project.
* Examples of good names: `errorCount`, `dnsConnectionIndex`, `referrerUrl`, `customerId`.
* Examples of bad names: `n`, `nErr`, `nCompConns`, `wgcConnections`, `pcReader`, `cstmrId`, `kSecondsPerDay`.

#### Specific Naming Rules

##### Package Names

* Use lowerCamelCase.
* Example: `my.exampleCode.deepSpace`.

##### Class Names

* Use UpperCamelCase for classes, interfaces, records, and typedefs.
* Names are typically nouns or noun phrases.
* Examples: `Request`, `ImmutableList`, `VisibilityMode`.

##### Method Names

* Use lowerCamelCase.
* Private methods should end with an underscore.
* Names are typically verbs or verb phrases.
* Example: `sendMessage`, `stop_`.

##### Enum Names

* Use UpperCamelCase for enums and CONSTANT_CASE for individual items.
* Enums should generally be singular nouns.
* Example: `enum Color { RED, GREEN, BLUE }`.

##### Constant Names

* Use CONSTANT_CASE.
* Consider the immutability of the value before naming it as a constant.
* Example: `const NUMBER = 5;`.

##### Non-constant Field Names

* Use lowerCamelCase with a trailing underscore for private fields.
* Example: `computedValues`, `index_`.

##### Parameter Names

* Use lowerCamelCase.
* Avoid one-character names in public methods.
* Exception: Names may begin with a `$` when required by third-party frameworks.

##### Local Variable Names

* Use snake_case.
* Constants in function scopes are still named in lowerCamelCase.

##### Template Parameter Names

* Be concise and use all-caps, such as `TYPE` or `THIS`.

##### Module-local Names

* Names that are not exported are implicitly private and do not end in an underscore.

#### Camel Case Definition

* Convert the phrase to ASCII, remove any apostrophes, divide into words, and apply camel case rules.
* Lowercase everything, then uppercase the first character of each word for UpperCamelCase, or each word except the first for lowerCamelCase.
* Example: `XmlHttpRequest`, `newCustomerId`.

### Examples and Practices

#### Good Practices

* Use descriptive names and avoid unnecessary abbreviations.
* Follow the specific rules for different types of identifiers to maintain consistency and readability.

#### Avoid

* Using ambiguous or unfamiliar abbreviations.
* Deleting letters within a word for the sake of abbreviation.
* Ignoring naming conventions for package, class, method, enum, constant, field, parameter, local variable, and template parameter names.

## Project Structure

### React

* **React Projects:** Organize by feature or route, with components, hooks, and context in their respective directories. Use index files for export barrels to simplify imports.

```bash
src/
├── components/
│   ├── Header/
│   │   ├── index.js // Export barrel for Header
│   │   └── Header.js
│   └── Footer/
│       ├── index.js // Export barrel for Footer
│       └── Footer.js
├── hooks/
│   └── useAuth.js
├── pages/
│   ├── Home/
│   │   ├── index.js // Export barrel for Home page
│   │   └── Home.js
│   └── About/
│       ├── index.js // Export barrel for About page
│       └── About.js
└── App.js
```

### Nodejs

* **Node.js Projects:** Organize by functionality (e.g., `routes`, `controllers`, `models`), and use index files for export barrels to group exports together.

```bash
src/
├── models/
│   ├── User.js
│   └── index.js // Export barrel for models
├── controllers/
│   ├── userController.js
│   └── index.js // Export barrel for controllers
├── routes/
│   ├── userRoutes.js
│   └── index.js // Export barrel for routes
└── app.js
```

### Files

* Divide code into simple pieces, using `import` and `export` to connect code fragments.
* Use export barrels (`index.js`) to aggregate module exports, facilitating cleaner imports.

#### File Names

* All lowercase, may include underscores (_), avoiding additional punctuation.

## TypeScript

### General TypeScript Practices

* **Strict Typing**: Enable strict mode in `tsconfig.json` to leverage TypeScript's full capabilities for catching errors at compile time and encouraging safer coding practices.

* **Interfaces and Types**: Define interfaces and types for component props, API responses, and complex data structures to enhance code readability and maintainability, while utilizing TypeScript's type system to prevent common errors.

* **Path Aliases**: Configure path aliases in `tsconfig.json` to simplify imports and avoid complex relative paths in large projects, improving code clarity and maintainability.

* **Linting and Formatting**: Integrate tools like ESLint and Prettier with TypeScript-specific configurations to ensure code follows best practices and maintains consistency across the project.

### React-Specific Practices

* **Custom Hooks**: Encourage the creation of custom hooks to encapsulate business logic and reuse behaviors across functional components, taking advantage of modern React features and improving code reusability.

* **Functional Components and Hooks**: Prefer functional components and hooks over class components to align with current React recommendations and better leverage TypeScript's capabilities for typing props, state, and contexts.

* **Lazy Loading and Code Splitting**: Use `React.lazy` and `Suspense` for lazy loading components and splitting code into smaller bundles to improve application performance, especially in large applications.

### Node.js-Specific Practices

* **Typed Middleware**: For frameworks like Express, define interfaces for request and response objects in custom middleware to enhance type safety and facilitate integration with other services.

* **Async Error Handling**: Use `async/await` for asynchronous operations and ensure proper error handling with `try/catch` blocks or error-handling middleware in Express.

* **ORM TypeScript Support**: Choose an ORM(such as TypeORM or Sequelize) that has native support for TypeScript to simplify database operations and ensure type safety.

## Git Guidelines

For this project, we adopt the `GitFlow` workflow strategy. Development efforts are managed through a `develop` branch, ensuring that only tested and stable changes are merged into the `main` branch. It is crucial to delete `features/[feature]` branches after their changes have been integrated into the `develop` branch to maintain a clean repository structure.

### Commit message structure

```bash
[code]: [explanation]
```

### Commit message codes

* **fix:** When fixing a bug
* **plus:** When adding a new feature
* **refactor:** When reorganizing or restructuring existent code
* **docs:** When adding documentation
* **style:** When changing code format

### GitFlow Basics Guide

GitFlow is a workflow model for Git that defines a strict set of rules for creating branches and releases, making it easier to manage software development. This model focuses primarily on improving collaboration and standardising the development process.

#### Main Branches with GitFlow

With GitFlow, there are two main branches that exist throughout the project lifecycle:

- `main` (formerly known as `master`): Contains the code in production.
- `develop`: Serves as an integration branch for new features.

#### Developing New Features

New features are developed in `feature` branches, which are derived from `develop` and merged back into `develop` once completed.

##### 1. Create a Feature Branch

To start working on a new feature, create a `feature` branch based on `develop`:

```bash
git checkout develop
git pull
git checkout -b feature/nombre-caracteristica
```

Replace feature-name with a descriptive name for your feature.

##### 2. Develop the Feature
Make all necessary changes to this branch. Report your progress regularly:

```bash
git add .
git commit -m "Descripción del cambio"
```

##### 3. Finalise a Feature

Once the feature is complete and ready to be integrated, you must merge it back into develop:

```bash
git checkout develop
git pull
git merge feature/nombre-caracteristica
git push origin develop
```

After merging the feature branch into develop, the feature/name-feature branch can be deleted if desired:

```bash
git branch -d feature/nombre-caracteristica
```

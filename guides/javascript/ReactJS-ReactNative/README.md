# ReactJS Code and Commit Lint Configurations

## Intro

Hello everyone! R u okay?
In the tutorial below, I show my code and commit lint configurations for a ReactJS project! I hope to help u a little...

---

# Editor

- VSCode

### Installation

The VSCode is available for the most operational systems.
[Download](https://code.visualstudio.com/download)

### Mandatory Extensions

#### [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

#### [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)

#### [EditorConfig for VSCode](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig)

---

# Commit lint

## Git

#### [Git Download](https://git-scm.com/downloads)

---

## Commitzen

[Commitizen](https://github.com/commitizen/cz-cli) is a CLI to automate your commit with the correct prefix and message. With Commitzen we'll follow the conventional commit pattern.

### Installations

Install Commitizen globally in your OS.

**NPM:**

`npm install -g commitizen`

`npm install -g cz-conventional-changelog`

In the directory of the project, run `npm init` to generate `package.json`, then execute:

`commitizen init cz-conventional-changelog --save --save-exact`

Now, commitizen must be working on. To test the magic and use, just execute:

`git cz`

---

## Commit Lint

The configurations below are used to deny any nonstandard commit.

To force a pattern on commit, we use two tools: [husky](https://github.com/typicode/husky) and [commitlint](https://github.com/marionebl/commitlint)

In the directory of your project, execute:

**YARN:**
`yarn add -D husky @commitlint/cli @commitlint/config-conventional`
**or**
**NPM:**
`npm install --save-dev husky @commitlint/cli @commitlint/config-conventional`

Now, in the root of your project create the file `commitlint.config.js` and write:

```javascript
module.exports = {
  extends: ["@commitlint/config-conventional"],
};
```

Now, inside of your `package.json` write:

```javascript
{
  ...,
  "husky": {
    "hooks": {
      "commit-msg": "commitlint -E HUSKY_GIT_PARAMS"
     }
  }
}
```

And that's it! Now your commit messages will be linted and they will follow the conventional commit specification :smiley:

---

# Code lint

First of all, check if you installed the extensions I sad above in your VSCode.
Now we have to delete the older configurations. If your project has these files, delete them: `.prettierrc` and `.eslintrc.json` or `.eslintrc.js`

## ESLint

ESLint is used to standardize and point out errors in your code.

### Installation

In the root of your project, execute:

**YARN:**
`yarn add eslint -D`
**or**
**NPM:**
`npm install eslint --dev`

Now, let's init eslint. For this, in the root of your project execute:

**YARN:**
`yarn eslint --init`
**or:**
**NPM:**
`npx eslint --init`

Answer the questions following this:

> ? How would you like to use ESLint?
>
> - [ ] To check syntax only
> - [ ] To check syntax and find problem
> - [x] To check syntax, find problems, and enforce code style

> ? What type of modules does you project use?
>
> - [x] Javascript modules (import/export)
> - [] CommonJS (require/exports)
> - [] None of these

> ? Which framework does your project use? (Use arrow keys)
>
> - [x] React
> - [] Vue.js
> - [] None of these

> Does your project use TypeScript? (y/N) : N

> ? Where does your code run?
>
> - ◯ Browser -> Mark this one
> - ◯ Node -> Unmark this one

> ? How would you like to define a style for your project? (Use arrow keys)
>
> - [x] Use a popular style guide
> - [] Answer questions about your style
> - [] Inspect your JavaScript file(s)

> ? Which style guide do you want to follow? (Use arrow keys)
>
> - [x] Airbnb (https://github.com/airbnb/javascript)
> - [] Standard (https://github.com/standard/standard)
> - [] Google (https://github.com/google/eslint-config-google)

> ? What format do you want your config file to be in? (Use arrow keys)
>
> - [x] JavaScript
> - [] YAML
> - [] JSON

> ? Would you like to install them now with npm? (Y/n) : Y

### Others ESLint dependencies

**YARN:**
`yarn add -D prettier eslint-config-prettier eslint-plugin-prettier eslint-plugin-react-hooks babel-eslint`
**or:**
**NPM:**
`npm install prettier eslint-config-prettier eslint-plugin-prettier eslint-plugin-react-hooks babel-eslint --dev`

Now open your new file `.eslintrc.js` and replace all the file with this:

```javascript
module.exports = {
  env: {
    browser: true,
    es2020: true,
  },
  extends: ["plugin:react/recommended", "airbnb", "prettier", "prettier/react"],
  parser: "babel-eslint",
  parserOptions: {
    ecmaFeatures: {
      jsx: true,
    },
    ecmaVersion: 11,
    sourceType: "module",
  },
  plugins: ["react", "prettier", "react-hooks"],
  rules: {
    "prettier/prettier": "error",
    "react/jsx-filename-extension": [
      "warn",
      {
        extensions: [".jsx", ".js"],
      },
    ],
    "import/prefer-default-export": "off",
    "react/state-in-constructor": "off",
    "react/static-property-placement": "off",
    "react/jsx-props-no-spreading": "off",
    "react/prefer-stateless-function": "off",
    "react/prop-types": "off",
    "no-param-reassign": "off",
    camelcase: "off",
    "no-console": "off",
    "react-hooks/rules-of-hooks": "error",
    "react-hooks/exhaustive-deps": "warn",
  },
};
```

---

## Prettier

Now let's add Prettier to the project! We gonna use Prettier to auto-format the code, following the ESLint rules.

In the root of your project create the file `.prettierrc` and write:

```json
{
  "singleQuote": true,
  "trailingComma": "es5"
}
```

---

## EditorConfig

Now let's add EditorConfig to the project! We gonna use EditorConfig to standardize the editors of all the members of the project.

Now, in the root of your project create the file `.editorconfig` (or click with the right button at the root of the project outside any file, then click in generate .editorconfig) and write:

```

root = true

[*]
indent_style = space
indent_size = 2
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true
end_of_line = lf
# editorconfig-tools is unable to ignore longs strings or urls
max_line_length = off

[CHANGELOG.md]
indent_size = false
```

---

Now we have the code lint installed on the project babies!! To help you to format all the created files, execute:

`yarn eslint --fix src --ext .js`

![That's all Folks](../../../assets/finalMessage.jpg)

Help us to do this tutorial better! Open a PR <3

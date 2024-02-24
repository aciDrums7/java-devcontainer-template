# Prettier Java

See original documentation [here](https://github.com/jhipster/prettier-java).

## Install

### Pre-requirements

- [Node version](https://nodejs.org/en/download/releases/) 10+
- [Prettier](https://github.com/prettier/prettier)

### Install Prettier and Prettier-Java plugin

```bash
# Local installation
npm install prettier-plugin-java --save-dev

# Or globally
npm install -g prettier prettier-plugin-java
```

or with yarn:

```bash
# Local installation
yarn add prettier-plugin-java --dev

# Or globally
yarn global add prettier prettier-plugin-java
```

Note: If you want to install the prettier-plugin-java globally, you should also install the prettier package globally.

### Install lint-staged

Use Case: Useful for when you want to use other code quality tools along with Prettier (e.g. ESLint, Stylelint, etc.) or if you need support for partially staged files (git add --patch).

Make sure Prettier is installed and is in your devDependencies before you proceed.

```bash
npx mrm@2 lint-staged
```

## Config Files

To reformat all your Java files, you first need to create `.prettierrc (or .prettierrc.yaml)` with following content (this is a modifed configuration):

```yaml
plugins:
  - prettier-plugin-java

overrides:
  - files:
      - "*.java"
    options:
      printWidth: 140
      tabWidth: 4
      useTabs: false
      trailingComma: none

  - files:
      - "**/*.json"
    options:
      tabWidth: 2
      semi: false

  - files:
      - "**/*.md"
    options:
      proseWrap: "always"
      singleQuote: false

  - files:
      - "**/*.yaml"
      - "**/*.yml"
    options:
      singleQuote: true
      tabWidth: 2
```

and a `.prettierignore` to avoid reformatting unwanted files (like `node_modules`):

```json
HELP.md
target/
!.mvn/wrapper/maven-wrapper.jar
!**/src/main/**/target/
!**/src/test/**/target/

### STS ###
.apt_generated
.classpath
.factorypath
.project
.settings
.springBeans
.sts4-cache

### IntelliJ IDEA ###
.idea
*.iws
*.iml
*.ipr

### NetBeans ###
/nbproject/private/
/nbbuild/
/dist/
/nbdist/
/.nb-gradle/
build/
!**/src/main/**/build/
!**/src/test/**/build/

### VS Code ###
.vscode/settings.json

### Environment ###
.env

### Node ###
node_modules
```

### Usage

With this setup, we have 2 ways of triggering the auto formatting:

- whenever a commit is made, the code will be automatically be formatted
- using the VS Code or Intellij `Prettier` extension

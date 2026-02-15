# @ctrl/oxlint-config [![NPM](https://img.shields.io/npm/v/@ctrl/oxlint-config)](https://www.npmjs.com/package/@ctrl/oxlint-config)

A shareable oxlint config for myself

## Getting Started

Install and pin dev dependencies:

```sh
pnpm add -D oxlint oxfmt @ctrl/oxlint-config
```

## Usage

In your project's `.oxlintrc.json` file, add the following:

```json
{
  "$schema": "./node_modules/oxlint/configuration_schema.json",
  "env": {
    "node": true
  },
  "plugins": ["react", "unicorn", "typescript", "oxc", "import"],
  "extends": ["./node_modules/@ctrl/oxlint-config/.oxlintrc.json"]
}
```

Add a `.oxfmtrc.json` config

```json
{
  "$schema": "./node_modules/oxfmt/configuration_schema.json",
  "printWidth": 100,
  "singleQuote": true,
  "arrowParens": "avoid",
  "experimentalSortImports": {
    "groups": [
      ["side-effect-style", "side-effect"],
      "builtin",
      "external",
      "internal",
      "parent",
      "index",
      "sibling"
    ],
    "newlinesBetween": true
  },
  "experimentalSortPackageJson": true,
  "experimentalTailwindcss": {
    "classOrder": "shadcn"
  }
}
```

Add scripts to your `package.json`

```json
{
  "scripts": {
    "lint": "oxfmt --check && oxlint .",
    "lint:fix": "oxfmt && oxlint . --fix"
  }
}
```

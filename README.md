# @ctrl/oxlint-config 

[![NPM](https://img.shields.io/npm/v/@ctrl/oxlint-config)](https://www.npmjs.com/package/@ctrl/oxlint-config)

A shareable oxlint for my projects.

## Getting Started

```sh
pnpm add -D oxlint @ctrl/oxlint-config prettier @trivago/prettier-plugin-sort-imports
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
  "extends": ["@ctrl/oxlint-config"]
}
```

Add a prettier config to your `package.json`:

```json
{
  "prettier": {
    "singleQuote": true,
    "trailingComma": "all",
    "arrowParens": "avoid",
    "semi": true,
    "printWidth": 100,
    "plugins": ["@trivago/prettier-plugin-sort-imports"],
    "importOrder": [
      "^node:.*$",
      "<THIRD_PARTY_MODULES>",
      "^(@ctrl)(/.*|$)",
      "^\\.\\./(?!.*\\.css$)",
      "^\\./(?!.*\\.css$)(?=.*/)",
      "^\\./(?!.*\\.css$)(?!.*/)"
    ],
    "importOrderSeparation": true,
    "importOrderSortSpecifiers": false
  }
}
```

## Current Import Order Rules

1. **`^node:.*$`** - Node.js built-in modules
2. **`<THIRD_PARTY_MODULES>`** - Third-party modules
3. **`^(@ctrl)(/.*|$)`** - @ctrl packages
4. **`^\\.\\./(?!.*\\.css$)`** - Relative imports from parent folders
5. **`^\\./(?!.*\\.css$)(?=.*/)`** - Relative imports from subfolders
6. **`^\\./(?!.*\\.css$)(?!.*/)`** - Relative imports from same folder

**Note**: CSS files (`.css` extensions) are excluded from all relative import patterns and maintain their original positions

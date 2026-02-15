# @ctrl/oxlint-config [![NPM](https://img.shields.io/npm/v/@ctrl/oxlint-config)](https://www.npmjs.com/package/@ctrl/oxlint-config)

A shareable oxlint config for myself

## Getting Started

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

## Current Import Order Rules

1. **`^node:.*$`** - Node.js built-in modules
2. **`<THIRD_PARTY_MODULES>`** - Third-party modules
3. **`^(@ctrl)(/.*|$)`** - @ctrl packages
4. **`^\\.\\./(?!.*\\.css$)`** - Relative imports from parent folders
5. **`^\\./(?!.*\\.css$)(?=.*/)`** - Relative imports from subfolders
6. **`^\\./(?!.*\\.css$)(?!.*/)`** - Relative imports from same folder

**Note**: CSS files (`.css` extensions) are excluded from all relative import patterns and maintain their original positions

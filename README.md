# @ctrl/oxlint-config

A shareable oxlint for my projects.

## Getting Started

```sh
pnpm add -D oxlint @ctrl/oxlint-config
```

## Usage

In your project's `.oxlintrc.json` file, add the following:

```json
{
  "$schema": "./node_modules/oxlint/configuration_schema.json",
  "env": {
    "node": true
  },
  "extends": ["@ctrl/oxlint-config"]
}
```


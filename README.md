# vue-tsc-files

A tiny tool to run `vue-tsc` on specific files without ignoring `tsconfig.json`.

## Installation

```sh
npm i -D @aki77/vue-tsc-files
```

```sh
yarn add -D @aki77/vue-tsc-files
```

## Why

I wanted to type-check **only the staged files** with [lint-staged](https://github.com/okonet/lint-staged).

Unfortunately passing specific files like `vue-tsc --noEmit file1.ts file2.ts` will cause TypeScript to simply ignore your `tsconfig.json`.

There's already an open issue in the TypeScript repo to support this use case — you may want to give a 👍 there: https://github.com/microsoft/TypeScript/issues/27379

## Usage

With lint-staged:

```json
{
  "lint-staged": {
    "*.{ts,vue}": "vue-tsc-files --noEmit"
  }
}
```

## How it works

For the most part, it just forwards all arguments to `vue-tsc` with one exception: the specified files will not be forwarded — instead, they will be put at the `files` property of a temporary config that will be generated next to your original `tsconfig.json`. Other than that, just read `vue-tsc --help`.

## License

Released under the [MIT License](./LICENSE.md).

# tsconfig

My tsconfig base files, extending [`@tsconfig/strictest`](https://github.com/tsconfig/bases).

## Installation

```sh
npm i -D @agilgur5/tsconfig
```

## Usage

`tsconfig.json`:

```json5
{
  // https://github.com/agilgur5/tsconfig
  "extends": "@agilgur5/tsconfig/library",
  // exclude node_modules (the default), dist dir, coverage dir
  "exclude": ["node_modules/", "dist/", "coverage/"],
  // see https://www.typescriptlang.org/tsconfig to better understand tsconfigs
  "compilerOptions": {
    // output to dist/ dir
    "outDir": "dist/",
  },
}
```

Please see the [`package.json#exports`](package.json) for how to import the different base files found here.

**NOTE**: Due to [microsoft/TypeScript#29172](https://github.com/microsoft/TypeScript/issues/29172), we repeat some configurations (`files`, `include`, `exclude`, `outDir`) from the base config as relative paths are currently resolved _within_ `node_modules`.

## Directory

The configs here do not change any of the _type-checking_ from the `@tsconfig/strictest` base. They only _add_ a handful more simple, common configurations:

- [`base`](src/tsconfig.json) adds to `@tsconfig/strictest` config around resolution (`moduleResolution`, `resolveJsonFile`) and emit (`sourceMap`, `jsx`, and `noEmit`)
- [`library`](src/tsconfig.library.json) adds to `base` config for libraries (`declaration`, `declarationMap`)
- [`library-build`](src/tsconfig.library-build.json) adds to `library` config used if you compile to JS with a separate tool (e.g. Rollup, Babel), but use `tsc` to output declarations (`emitDeclarationOnly`)

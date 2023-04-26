# TypeScript Fluent Translation List

Rapidly support Fluent Translation Lists in your web application. This uses the NPM package `@fluent/bundle` under the hood.

## Getting Started

Example TypeScript:

```
import { FTL } from 'com.hydroper.ftl';

const ftl = new FTL({
    supportedLocales: ['en'],
    fallbacks: {},
    defaultLocale: 'en',

    assetSource: 'res/lang',
    assetFiles: [
        '_', // res/lang/LANG/_.ftl
    ],

    cleanUnusedAssets: true,

    // specify either 'http' or 'fileSystem' as load method
    loadMethod: 'fileSystem',
});

async function main() {
    if (!(await ftl.load())) {
        // failed to load
        return;
    }

    console.log(ftl.getMessage('hello-to', { to: 'Jessica' }));
}

main();
```

Example FTL at `res/lang/en/_.ftl`:

```
hello-to = Hello, { $to }!

```

## Server Usage

Usually, for server applications, set the `cleanUnusedAssets` option to `false` and clone the `FTL` object when necessary by invoking `ftl.clone();`.
# TypeScript Fluent Translation List

Rapidly support Fluent Translation Lists in your web application. This uses the NPM package [`@fluent/bundle`](https://www.npmjs.com/package/@fluent/bundle).

Both client-side and server-side applications are supported.

## Getting Started

Example TypeScript:

```ts
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

    console.log(ftl.getMessage('hello', { to: 'Jessica' }));
}

main();
```

Example FTL at `res/lang/en/_.ftl`:

```
hello = Hello, { $to }!
```

## Server Usage

Usually, for server applications, set the `cleanUnusedAssets` option to `false` and clone the `FTL` object when necessary by invoking `ftl.clone();` to change the current locale.

## API

Currently no TypeDocs generated, but you can consult the API at: [index.d.ts](src/index.d.ts).
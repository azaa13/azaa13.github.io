---
layout: post
title:  "Vuejs+Typescript: What is a tsconfig.json file under /src?"
date:   2020-02-28 21:21:00 +0900
categories: typescript tsconfig config
---

If you using VueJs with Typescript, must have wondered `tsconfig.json` file under root dir of the project. Well, that is a configuration file for transpiling and compiling Typescript files.

## More about tsconfig.json file

Basically `tsconfig.json` indicates that the project is using Typescript and pass those ts files ready to be compiled or run.

As seen from the config, it is a json file which sets some compiler options and many other setting which developers want to set.

Let's look at sample file.

```json
// tsconfig.json
{
    "compilerOptions": {
        "module": "esnext",
        "noImplicitAny": true,
        "removeComments": true,
        "preserveConstEnums": true,
        "outFile": "../../built/local/tsc.js",
        "sourceMap": true
    },
    "include": [
        "src/**/*"
    ],
    "exclude": [
        "node_modules",
        "**/*.spec.ts"
    ]
}
```

As we can see, there are numerous properties can be set. `compilerOptions` tell that what compiler should execute or follow based on the our setups. Generally if we not extend the config for `compilerOptions`, it sets default config during compile. To specify your config, you can overwrite it by adding properties.
Other properties are `include`, `exclude`, `files` where the specific files are given to be added for running. If those prop are given, the compiler will include to run those files as well.
By default, compiler exclude to run "node_modules", any "out_dir", some packages and so on. Additionally, we can add some `"*.spec.t|js"` files for `exclude`.

If want to know more about and detailed way, please visit <https://www.typescriptlang.org/docs/handbook/tsconfig-json.html>.

As mentioned earlier, default ts config is set in [here](https://www.typescriptlang.org/docs/handbook/compiler-options.html).

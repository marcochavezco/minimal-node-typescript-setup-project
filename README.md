# Minimal Node TypeScript Setup Project

The first step is to initialize our Nodejs project running the command:

```bash
npm init -y
```

Now we want to use ESModules instead of commonjs by adding `"type": "module"` to the `package.json` file. Also, since we are going to work with TypeScript is good idea to add a build script to compile the code.

`package.json`
```json
{
	"name": "form-sender",
	"version": "1.0.0",
	"description": "",
	"main": "index.js",
	"type": "module",
	"scripts": {
		"build": "tsc",
		"test": "echo \"Error: no test specified\" && exit 1"
	},
	"keywords": [],
	"author": "",
	"license": "ISC"
}
```

To install TypeScript run:

```bash
npm i -D typescript
```

Now let's setup TypeScript. For this, we want to organize a little bit by creating a `src` directory. Following by changing the extension of the index file to `.ts` and add it to the created folder. We should end with a project like this:

```
> node_modules
v src
	index.ts
package-lock.json
package.json
```

After that, we need to create a `tsconfig.json` to configure the behavior of the TypeScript compiler. For this project I am going to use a simple config, but you are free to setup this with as many rules as you want.

`tsconfig.json`
```json
{
"compilerOptions": {
"module": "NodeNext",
"moduleResolution": "NodeNext",
"target": "ES6",
"sourceMap": true,
"outDir": "dist",
},
"include": ["src/**/*"],
}
```

To check what `NodeNext` is go to the [TypeScript Documentation](https://www.typescriptlang.org/tsconfig/#node16nodenext).

To test the project setup modify the `index.ts` file and then run the `build` command:

`index.ts`
```ts
import { randomUUID } from "node:crypto";

console.log(randomUUID());
```

> Tip: You might want to install the node types to avoid errors related with type definitions by running `npm i -D @types/node`.

Now add a `start` script in the `package.json`:

```json
...
"scripts": {
"start": "node dist/index.js",
"build": "tsc",
"test": "echo \"Error: no test specified\" && exit 1"
},
...
```

Followed by the commands:

```bash
npm run build
npm run start
```



# Minimal Node TypeScript Setup Project

The first step is to initialize our Node.js project by running the following command:

```
npm init -y
```

Now, we want to use ESModules instead of CommonJS by adding `"type": "module"` to the `package.json` file. Also, since we are working with TypeScript, it's also a good idea to add a build script to compile the code.

```json
{
	"name": "minimal-node-typescript-setup-project",
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

To install TypeScript, run:

```bash
npm i -D typescript
```

Now let's set up TypeScript. To keep things organized, let's create a `src` directory. Then, change the extension of the `index.js` file to `index.ts` and move it to the new folder. We should end up with a project structure like this:

```
. 
├── node_modules
├── src/ 
│   └── index.ts 
├── package-lock.json 
└── package.json
```

Next, we need to create a `tsconfig.json` to configure how the TypeScript compiler behaves. For this project, I'll use a simple configuration, but feel free to customize it with as many rules as you need.

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

To check what `NodeNext` is, head over to the [TypeScript Documentation](https://www.typescriptlang.org/tsconfig/#node16nodenext).

To test the project setup, modify the `index.ts` file:

```ts
import { randomUUID } from "node:crypto";

console.log(randomUUID());
```

> Tip: You might want to install the Node.js types to avoid type definitions errors by running `npm i -D @types/node`.

Finally, add a `start` script to the `package.json`:

```json
"scripts": {
	"start": "node dist/index.js",
	"build": "tsc",
	"test": "echo \"Error: no test specified\" && exit 1"
},
```

Run the following commands:

```bash
npm run build
npm run start
```

Everything should be running smoothly, and this gives you a solid foundation for future TypeScript projects. You can bootstrap the Minimal Node TypeScript Setup Project from this [GitHub Repository Template](https://github.com/marcochavezco/minimal-node-typescript-setup-project)
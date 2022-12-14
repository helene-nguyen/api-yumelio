# How to start creating the API ?

## Initialization

First of all, you need to initialize the folder

```sh
npm init
```

And than, install all the packages needed

```sh
 npm i dotenv pg express-session helmet ajv bcrypt jsonwebtoken swagger-jsdoc swagger-ui-express nodemailer
```

And dev dependencies

```sh
npm i -D typescript debug jest supertest ts-jest concurrently eslint @types/bcrypt @types/debug @types/express @types/jest @types/supertest @types/express-session @types/pg @types/swagger-jsdoc @types/swagger-ui-express @types/jsonwebtoken @faker-js/faker @types/nodemailer
```

Without the @types/express, @types/debug packages etc.., there is no way for TypeScript to know about the types of these classes.

And config eslint

```sh
npm init @eslint/config
```

This will ask you a series of questions

    How would you like to use ESLint? · To check syntax and find problems
    √ What type of modules does your project use? · JavaScript modules (import/export)
    √ Which framework does your project use? · None of these
    √ Does your project use TypeScript? · Yes
    √ Where does your code run? · node
    √ What format do you want your config file to be in? · JavaScript

And it will install dependencies to use it :

```
The config that you've selected requires the following dependencies:

@typescript-eslint/eslint-plugin@latest @typescript-eslint/parser@latest
√ Would you like to install them now? · No / Yes
√ Which package manager do you want to use? · npm
Installing @typescript-eslint/eslint-plugin@latest, @typescript-eslint/parser@latest

added 12 packages, and audited 644 packages in 3s

69 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
Successfully created .eslintrc.js file in C:\Users\Gamer\Desktop\api-yumelio
```

## Configure package.json

- Add description
- Add `"type":"module"`
- Change main into `"dist/index.js` (once compiled, we tell Node to get this file as main entry point)
- Configure `"script"`
- Add "concurrently" to launch compiler and your server

Complete code

```js
{
  "type": "module",
  "name": "api-yumelio",
  "version": "1.0.0",
  "description": "Make an API portfolio, personnal file in which experiences and formation can be shown",
  "main": "dist/index.js",
  "scripts": {
    "start": "node dist/index.js",
    "dev:build_🏡": "tsc -w",
    "dev:run_🚀": "nodemon dist/index.js",
    "dev:lint_💥": "eslint . --ext .ts",
    "dev": "concurrently \"npm:dev:*\" -c green.bold,yellow.bold,blue.bold",
    "test": "node --experimental-vm-modules node_modules/jest/bin/jest.js --watchAll"
  },
  "keywords": [],
  "author": "Yumicode & Megafredo",
  "license": "MIT",
  "dependencies": {
    "ajv": "^8.11.0",
    "bcrypt": "^5.0.1",
    "dotenv": "^16.0.2",
    "express-session": "^1.17.3",
    "helmet": "^6.0.0",
    "jsonwebtoken": "^8.5.1",
    "nodemailer": "^6.7.8",
    "pg": "^8.8.0",
    "swagger-jsdoc": "^6.2.5",
    "swagger-ui-express": "^4.5.0"
  },
  "devDependencies": {
    "@faker-js/faker": "^7.5.0",
    "@types/bcrypt": "^5.0.0",
    "@types/debug": "^4.1.7",
    "@types/express": "^4.17.13",
    "@types/express-session": "^1.17.5",
    "@types/jest": "^29.0.0",
    "@types/jsonwebtoken": "^8.5.9",
    "@types/nodemailer": "^6.4.5",
    "@types/pg": "^8.6.5",
    "@types/supertest": "^2.0.12",
    "@types/swagger-jsdoc": "^6.0.1",
    "@types/swagger-ui-express": "^4.1.3",
    "@typescript-eslint/eslint-plugin": "^5.36.1",
    "@typescript-eslint/parser": "^5.36.1",
    "concurrently": "^7.3.0",
    "debug": "^4.3.4",
    "eslint": "^8.23.0",
    "jest": "^28.1.3",
    "supertest": "^6.2.4",
    "ts-jest": "^28.0.8",
    "typescript": "^4.8.2"
  },
  "jest": {
    "forceExit": true,
    "collectCoverage": false,
    "verbose": true,
    "detectOpenHandles": false
  }
}

```

## tsconfig.json file

Configure the `tsconfig.json` file

```sh
{
  "compilerOptions": {
    "module": "ES6",
    "esModuleInterop": true,
    "target": "es6",
    "moduleResolution": "node",
    "sourceMap": true,
    "outDir": "dist"
  },
  "lib": ["es2015"],
  "compileOnSave": true
}

```

I use ESM and i want to compile Typescript on save so add `compileOnSave` on true.

The `outDir` can specify where the file will be save once compiled.

---

[Home](../README.md) | [Next](./01_folder.md)

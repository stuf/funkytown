---
wip: true
---

# Chapter 1

## Contents

  - [Create a new project](#create-a-new-project)

Where do all projects start from? By making a directory for it and creating a new Git repository there! Where your project will live, that's where.

## Create a new project

Come up with a name for your project and create a folder with that name. You can always change it later on, so whatever name you come up is fine; `toolbelt`, `toolchain`, `hammerkit`, etc. For the purposes of this book, I'll call it `funkytown`.

```sh
$ mkdir -p ~/Projects/funkytown
$ cd ~/Projects/funkytown
```

Go to your new project folder and first, initialize a Git repository in it.

```sh
$ git init
```

```
Initialized empty Git repository in /Users/stefan.rimaila/Projects/funkytown-impl/.git/
```

After that, initialize the directory as a Node package as well. You can use the defaults for all questions asked.

```sh
npm init
```

---

Output:

```
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help json` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg>` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
package name: (funkytown-impl)
version: (1.0.0)
description:
entry point: (index.js)
test command:
git repository:
keywords:
license: (ISC)
About to write to /Users/stefan.rimaila/Projects/funkytown-impl/package.json:

{
  "name": "funkytown-impl",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Stefan Rimaila <stefan@rimaila.fi> (https://stuf.github.io)",
  "license": "ISC"
}


Is this OK? (yes)
```

---

You should now have a directory that's a Git repository, and also contain a `package.json` file:

---

Output:

```
total 8
-rw-r--r--  1 stefan.rimaila  328764342   269B 13 Mar 21:38 package.json
```

---

## Base project structure

There are no hard rules when it comes to how to structure your project. However there are some best practices or conventions that people use that have proven to be useful when it comes to structuring your project.

  - `<project>/src` - where your project's source code (implementation) is
  - `<project>/test` - where your project's tests files are located (more on this later)

We will be covering tests in a later chapter, as they're not important right now getting up to speed. What we want to do, is to write some code and have it run. It can't be difficult, now can it?

## The Elephant in the Room

Let's get the boring stuff out of the way first. We're creating a library that should be possible to be used in the browser. Getting JavaScript to run in the browser in itself is easy, but if you've used something like `create-react-app`, you might be more familiar to importing code from modules.

```js
import { function } from './file';
```

Up until some time ago, browsers have not supported using JavaScript in modules, and using them through imports. Even though we have native support for that now, it's not always desirable to do so, because we end up importing a lot of redundant stuff that we're not using at all! Browsers currently are unable to perform techniques such as _tree shaking_—where what you end up using in your application only contains used code, and all the unused code is removed. Even while internet connection speeds are fast, we're still limited to data plans or sluggish Internet speeds when on mobile. So saving up on that precious bandwidth is still important.

We'll tackle this problem head-first and get it out of the way so we can concentrate on the more important things after that.

## Solve your problems right away

Create a new file, `src/index.js` and open the file in your editor. Add the following code in it.

```js
import url from 'url';
console.log({ url });
```

Now, save and try to run it in your terminal.

```sh
node src/index.js
```

---

Output:

```
/Users/stefan.rimaila/Projects/funkytown-impl/src/index.js:1
(function (exports, require, module, __filename, __dirname) { import url from 'url';
                                                                     ^^^

SyntaxError: Unexpected identifier
    at new Script (vm.js:73:7)
    at createScript (vm.js:245:10)
    at Object.runInThisContext (vm.js:297:10)
    at Module._compile (internal/modules/cjs/loader.js:657:28)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:700:10)
    at Module.load (internal/modules/cjs/loader.js:599:32)
    at tryModuleLoad (internal/modules/cjs/loader.js:538:12)
    at Function.Module._load (internal/modules/cjs/loader.js:530:3)
    at Function.Module.runMain (internal/modules/cjs/loader.js:742:12)
    at startup (internal/bootstrap/node.js:266:19)
```

  - use ES imports
  - save into `src/index.js`
  - try to run
  - fail
  - why?

## Set up Webpack

  - `npm install webpack webpack --save-dev`
  - run `webpack src/index.js dist/index.js`
  - run the resulting bundle; `node dist/index.js`
  - it works!
  - add `dist/` to your `.gitignore` file




## tl;dr

  1. Create a new project
    - Initialize NPM package
    - Initialize Git repository
    - Add common `.gitignore`s
    - Add `.editorconfig`
    - Set up your editor
  1. Base project structure
  1. Create test code stub, run and fail

  1. Set up `webpack`
  1. Commit your work
  1. Lore
    - JavaScript and modules
    - Task runners and bundlers
    - Babel and a short history on transpiling code

## Create a new project

  - find a suitable spot to plop your beginning

## First lines of code

## Setting up code compilation

## Re: First lines of code

## Commit!

## Lore


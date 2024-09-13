# Tailwind CSS basic learning

- [Tailwind CSS basic learning](#tailwind-css-basic-learning)
  - [Installation](#installation)
  - [Folder Directories](#folder-directories)
  - [Extention for VS code Studio](#extention-for-vs-code-studio)
  - [Use NPM for auto script `--watch`](#use-npm-for-auto-script---watch)

## Installation

for basic intallation you can visit at [Tailwindcss.com](https://tailwindcss.com). but in this documentation i use tutorial from youtube [Dave Gray](https://www.youtube.com/watch?v=lCxcTsOHrjo&list=PPSV). maybe soon i will update documentation from other resource.
for easiest way, i use `Live Server` extention from Visual Studio Code, and enable `Full Reload`. and you can install `tailwindconfog.js` use this command.

```bash
npx tailwindcss init
```

after that you can make directory `build` and `src` in root directory. this is folder structure is

```html
_root
|__/build
|____/index.html
|__/src
|____/input.css
|__tailwindcss.config.json
```

on `tailwind.config.js` file set the content setting

```javascript
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    './build/*.html'
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

and on `./src/input.css` add this code

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

and for compile tailwind css you can use this command

```bash
npx tailwindcss -i ./src/input.css -o ./build/css/style.css
```

and if you want to compile during writing a code you can use

```bash
npx tailwindcss -i ./src/input.css -o ./build/css/style.css --watch
```

## Folder Directories

```html
_root
|__/build
|____/index.html
|__/src
|____/input.css
|__tailwindcss.config.json
```

## Extention for VS code Studio

- `Live Server` for browser
- `Tailwind CSS Intellisense` for tailwind css type class
- `inline fold` for folding class, it make easier to maintain tailwind code
- `prettier-plugin tailwind` for resturctured tailwind code

you can isntall with npm

```npm
npm install --save-dev prettier
```

and then make a file `.prettierrc` and paste this code

```json
{
  "semi": false,
  "singleQuote": true,
  "trailingComma": "es5",
  "arrowParens": "avoid",
  "printWidth": 80
}
```

and integration with VS code with isntall plugin `Prettier - Code Formatter`. for manual formatter you can run

```npm
npx prettier --write <file or folder>"
```

example

```npm
npx prettier --write "./build/*.html
```

## Use NPM for auto script `--watch`

you can use NPM for automated compile, if you always type `npx tailwindcss` its too wasted times for using auto compile. you can NPM to manage it

```npm
npm init -y
```

now you can setting in `package.json` file this code

```json
"scripts": {
    "watch": "npx tailwindcss -i ./src/input.css -o ./build/css/style.css --watch"
  },
```

if you run `npm run watch` this also run script in `watch`

### Second generation

- Webpack
- Parcel
- Rollup

Note:

- Give a quick summary of what they are
- We'll dive into the details later

---

### Webpack

<img src="img/webpack.png" alt="Webpack logo" width="200" />

Static module bundler

---

### Webpack

- Very powerful tool
- Both module bundler / loader
- Extensible with plugins / loaders
- Works with almost resource types
- Powerful bundle splitting
- Development server for incremental compilation and hot reloading

Note:

- Has anyone used this?
- Configuration is not as hard as some say
  - For simple cases you don't need any config
  - Easier to configure than Grunt
- When making a dev / production build and run on server / client can get confusing
- All resources includes html, images, css, fonts and icons
- Dev server:
  - Only load the changed files
  - Quicker than including everything always

vvv

## Getting started with webpack

```
mkdir training-webpack
cd training-webpack
npm init -y
npm install --save-dev webpack http-server
```

vvv

### Getting started with webpack

index.html

```html
<html>
  <head>
    <title>Hello Webpack</title>
  </head>
  <body>
    <div id="app"></div>
    <script src="dist/main.js"></script>
  </body>
</html>
```

vvv

### Getting started with webpack

index.js

```javascript
var render = require("./render.js");

document.getElementById("app").innerHTML = render();
```

render.js

```javascript
module.exports = function () {
  var heading = "<h1>Hello from renderer</h1>";
  var paragraph = "<p>This is a paragraph</p>";
  return heading + paragraph;
};
```

vvv

### Running the code

```sh

# generates dist/main.js on file change
npx webpack watch ./index.js --mode=development


# or minified build
npx webpack watch ./index.js --mode=production

# serves the current directory and opens a browser
npx http-server -o
```

vvv

### Things to try

- Edit a JS file and reload
- Look at the contents of bundle.js
- Import a module from npm like jQuery / lodash

```javascript
var $ = require("jquery");
var _template = require("lodash/template");
```

---

### Parcel

<img src="img/parcel.png" alt="Parcel logo" width="200" />

The Zero configuration build tool

---

### Parcel

- Supports a lot of diferent resources
- Almost no configuration required
- Can be customized if needed

Note:

- Very useful tool for building a quick standalone webapp
- Does image compression, minification, transpilation
- support React out of the box and Vue via a plugin
- Written in Rust

vvv

## Getting started with Parcel

```sh
mkdir training-parcel
cd training-parcel
npm init -y
# manually remove main: "index.js" from the generated package.json
npm install --save-dev parcel
```

vvv

## getting started with Parcel

index.html

```html
<html>
  <head>
    <title>My First Parcel App</title>
  </head>
  <body>
    <div id="app"></div>
    <script src="index.js" type="module"></script>
  </body>
</html>
```

vvv

## getting started with Parcel

index.js

```javascript
var render = require("./render.js");

document.getElementById("app").innerHTML = render();
```

render.js

```javascript
module.exports = function () {
  var heading = "<h1>Hello from renderer</h1>";
  var paragraph = "<p>This is a paragraph</p>";
  return heading + paragraph;
};
```

vvv

### Running the code

```sh

# start dev server and open browser
npx parcel index.html --open

# Produce a minified build
npx parcel build

```

---

### Current generation

- Esbuild
- Vite

Note:

- Transition from javascript based tooling to "native" (Rust, Go etc) tooling

---

### Esbuild

<img src="img/esbuild.png" alt="ESBuild logo" width="200" />

An extremely fast javascript bundler

Note:

- Up to 100x faster than webpack 5
- Foundational tool for current generation of fast bundlers
- More a utility than an end user tool
- Written in Go

---

### Vite

<img src="img/vite.png" alt="Vite logo" width="200" />

Next generation frontend tooling

---

### Vite

- Uses esbuild for module transformation
- Uses Rollup for production bundling
- Highly pluggable architecture following Rollup's plugin architecture
- Still very much in flux so not everything may be supported yet

Note:

- Written in Go
- Bundling still faster due to waterfall of imports and minification

vvv

### Getting started with Vite

```sh
npm create vite@latest training-vite -- --template react-ts
cd training-vite
npm install
```

vvv

### Running the code

```sh

# run the dev server
npm run dev

# Create a production build
npm run build

# Serve the generated production build
npm run preview

```

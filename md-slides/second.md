### Second generation

- Webpack
- Parcel
- Rollup

Note:

- Give a quick summary of what they are
- We'll dive into the details later

### Webpack: The flexible module bundle

![What is webpack](img/what-is-webpack.png)

---

### Webpack: The flexible module bundle

- Most powerful tool
- Both module bundler / loader
- Webpack itself does many things
- Extensible with plugins / loaders
- Works with all resources
- Powerful bundle splitting
- Development server for incremental compilation

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

---

### Current generation

- Esbuild
- Vite

---

### Esbuild

![ESBuild logo](img/esbuild.png)

An extremely fast javascript bundler

Note:

- Up to 100x faster than webpack 5
- Foundational tool for current generation of fast bundlers
- More a utility than an end user tool

---

### Vite

![Vite logo](img/vite.png)

Next generation frontend tooling

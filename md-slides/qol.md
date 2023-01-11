### Quality of life

- Prettier
- Eslint

Note:

- Describe what we mean by quality of life

---

### Prettier

![Prettier optionated code formatter](img/prettier-logo.png)

Opinionated code formatter

Note:

- Ever experienced the tab versus spaces debate?

---

### Prettier

- Automatically formats most of your frontend files
- Sane defaults
- Plugins for most popular IDEs

vvv

### Prettier

- Ensure you have prettier installed in your IDE
- Create a new component in your react app (a Button with a label and onClick handler for example)
- Try to write it in a single line
- Save the file
- 🪄!

---

### Eslint

<img src="img/ESLint.png" alt="ESlint logo" width="200" />

Find and fix problems in your Javascript code

Note:

- Very useful to prevent common coding mistakes
- Use it wisely, with great power comes great responsibility

vvv

### Eslint in practice

- Ensure your IDE supports Eslint
- Open app.tsx in your project and type something like the following in your function body

```js
if ("" == 0) {
  return;
}
```

Note:

- What would be good to lint?
- What wouldn't?

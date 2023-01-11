### Documentation tooling

- Storybook
- Styleguidist
- Vitebook

Note:

- Storybook more workshop vs Styleguidist more store front
- Vitebook still beta

---

### Storybook

![Storybok logo](img/storybook.png)

Build UIs without the grunt work

---

### Storybook

- Build your components in an isolated environment
- Generate documentation about your components
- Build a living style/component guide

Note:

- Tell the story of Norbert an Gert
- Storybook application still webpack based. Components can be loaded using vite

vvv

### Your first story

From your project directory:

```sh
npm install --save-dev @nrwl/storybook
nx g @nrwl/storybook:configuration  <your app name>
```

- Select `@storybook/react`
- Select `N` when asked to run cypress against a storybook instance
- Select `vite` as storybook builder

vvv

### Your first story

From your project directory

```sh
nx g component-story --componentPath app/<your component>.tsx --project <your app name>
```

To scaffold a new story for your component

Run the following to open your server

```sh
nx run <your app name>:storybook
```

vvv

### Your first story

Add automatic action handlers in the preview.js file of your storybook folder

```js
// .storybook/preview.js

export const parameters = {
  actions: { argTypesRegex: "^on.*" },
};
```

Restart your storybook server

vvv

### Your first story

Using the modern CSF 3 format:

```ts
import type { ComponentMeta, ComponentStoryObj } from "@storybook/react";
import Button from "./Button";

const Story: ComponentMeta<typeof Button> = {
  component: Button,
};
export default Story;

export const Primary: ComponentStoryObj<typeof Button> = {
  args: {
    title: "hello",
  },
};
```

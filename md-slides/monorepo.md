### Monorepo tooling

- Nx
- Turborepo
- (Lerna)
- Gradle

Note:

- Explain main differences in tools and people behind it (nrwl.io vs vercel vs gradle inc)
- Explain Lerna now based on Nx

---

### NX

![NX logo](img/nx.webp)

The smart, fast extensible build system

Note:

- Who knows this
- Monorepo tool for larger software projects
- By Narwhal (Victor Savkin and Jeff Cross of Angular fame)

---

### NX

- Allows you to decompose your project in apps and service
- Enforces project-wide conventions
- Highly pluggable system to support a wide range of usecases
- Broad variety of frameworks supported
- Efficient (re-)builds by only building "affected"

Note:

- Ease of reuse by moving logic into services
- Project wide conventions by generators
- Plugins both by nrwl and community

vvv

### Your first NX project

```sh
npm i -g nx
npx create-nx-workspace@latest
```

- Create a `integrated monorepo`
- Select `React`
- Give your project a nice name
- Give the app in the project a nice name
- Choose `css` as your stylesheet format
- Opt out of distributed builds
- Run `npm start` in the generated folder

vvv

### Your first NX project

- Open your new project in your favourite editor.
- Explore the project a bit to see what got generated
- Commit the current state of your project to git (do this after every step to make life easier)
- Run `nx g @nrwl/react:app <name of second app> --bundler=vite` to generate a vite based react app
- Run `nx g lib app-data`
- Select `Workspace library`
- Select `vite` as bundler
- Select `Vitest` as testrunner

vvv

### Your first NX project

Change the generated `app-data.ts` file to this:

```ts
export async function appData(): Promise<string> {
  const response = await fetch("https://swapi.dev/api/people/1");
  if (!response.ok) {
    throw new Error("Failed to fetch");
  }
  const person = await response.json();
  return person.name;
}
```

vvv

### Add the following to your app.tsx

```tsx[5,6,9-12,16]
// eslint-disable-next-line @typescript-eslint/no-unused-vars
import styles from './app.module.css';

import { Route, Routes, Link } from 'react-router-dom';
import { useEffect, useState } from 'react';
import { appData } from '@sample/app-data';

export function App() {
  const [name, setName] = useState('');
  useEffect(() => {
    appData().then(fetchedName => setName(fetchedName))
  }, []);

  return (
    <>
      <h1>{name}</h1>
      ...
```

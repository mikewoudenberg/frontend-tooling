### Other useful libraries

- PostCSS
- Tanstack query

Note:

- Make a lot of common web development tasks a lot easier
- Not limited to this list

---

### Postcss

<img src="img/logo-postcss.svg" alt="PostCSS logo" width="200" />

A tool for transforming CSS with JavaScript

---

### PostCSS

- Transform modern CSS into compatible CSS
- Purge unused styles
- Lint your styles

---

### Tanstack query

![Tanstack query logo](img/tanstackquery.png)

Powerful asynchronous state management

Note:

- Evolved from React-query
- Inspired by Apollo-Client
- By Tanner Linsey
- Ideal solution for server side state management

### Tanstack query

- Simplifies server side state management
- Has provisions for handling most cases for you
- Supports React, Vue, Solid and Svelte

vvv

### Improving your code by using tanstack query

run `npm i @tanstack/react-query`

add the following to `app.tsx`

```ts
import {
  useQuery,
  QueryClient,
  QueryClientProvider,
} from "@tanstack/react-query";
//...

const queryClient = new QueryClient();

export function App() {
  return (
    <QueryClientProvider client={queryClient}>
      <OriginalApp />
    </QueryClientProvider>
  );
}
```

vvv

Rename the original App function to OriginalApp and insert this at the start

```ts
const { data, error } = useQuery(["nameQuery"], appData);
if (error) {
  return <div>Failed to load</div>;
}
```

vvv
Render the data with

```tsx
<div>{data}</div>
```

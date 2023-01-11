## Testing

- Jest
- Testing library
- Cypress

---

### Jest

<img src="img/jest.jpg" alt="Jest logo" width="200"/>

Test library by Facebook

Note:

- Combines an assertion library, test runner and test framework
- Faster alternative to karma, mocha
- Originated as React specific, but can be used for any type of testing
- since 2014

vvv

### Jest

Writing your first jest test

- Use `describe(...` to state what component you are testing
- Use `it ('should ...` to describe what behaviour you are asserting in the test
- (Optionally)

---

### Testing library

![Testing library logo](img/octopus.png)

Helper library to write better tests by Kent C. Dodds.

Note:

- A set of utilities that enforces good practices
- Explain a bit of background from Kent c. Dodds (of NG-NL fame)

---

### Testing library

<blockquote>The more your tests resemble the way your software is used, the more confidence they can give you.</blockquote>

- Key helpers:
  - `render`
  - `screen`
  - `userEvent`

Note:

- Describe what the key helpers do

vvv

### Testing library

- Open your project
- run `npm install --save-dev @testing-library/react @testing-library/user-event`
- Create a test for the component we made earlier using testing library
  - Simulate clicking on the button
  - Assert that the text in the textbox changed

---

### Mock Service Worker

![MSW logo](img/msw.jpeg)

Api mocking of the next generation

Note:

- Tool to mock backend servers
- For Unit tests, but also for storybook or cypress

vvv

### Mock Service Worker

- Run `npm install --save-dev msw`
- Create the file `src/mocks/handlers.js`
- Fill it with:

```js
export const handlers = [
  rest.post("/login", (req, res, ctx) => {
    return res(
      // Respond with a 200 status code
      ctx.status(200)
    );
  }),
];
```

vvv

### Mock Service Worker

---

### Cypress

<img src="img/cypress.jpeg" alt="Cypress logo" width="200"/>

End to end testing library

Note:

- Briefly compare to Selenium based tools

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
- Key helpers: `render`, `screen` and `userEvent`

Note:

- Describe what the key helpers do

---

### Testing library

- Open your project
- run `npm install --save-dev @testing-library/react @testing-library/user-event`
- Create a test for the component we made earlier using testing library
  - Simulate clicking on the button
  - Assert that the text in the textbox changed

---

### Mock Service Worker

![MSW logo](img/msw.jpeg)

Helper library for simulating backend servers

---

### Cypress

<img src="img/cypress.jpeg" alt="Cypress logo" width="200"/>

End to end testing library

Note:

- Briefly compare to Selenium based tools

# Saucedemo Login Test Suite

## How AI helped

I used an AI tool to help draft the five test cases based on the login requirements for saucedemo.com. I described the feature and the known user accounts, and the AI suggested a set of scenarios covering the happy path and common edge cases. I then reviewed those suggestions, adjusted a few things, and wrote the actual automation code myself -- the page object, the test file, and the project setup.

## Project structure

```
.
├── pages/
│   └── LoginPage.js       # Page object for the login page
├── tests/
│   └── login.spec.js      # Test file with all 5 test cases
├── package.json
├── playwright.config.js
└── README.md
```

## Test cases

1. Successful login with valid credentials (`standard_user`)
2. Locked-out user cannot log in (`locked_out_user`)
3. Login fails with a wrong password
4. Login fails when both username and password are empty
5. Login fails when the password field is left blank

## How to install and run

**Requirements:** Node.js 18 or later.

```bash
npm install
npx playwright install chromium
npm test
```

The tests run against `https://www.saucedemo.com` in headless Chromium. Results are printed in the terminal. If you want to see the browser, open `playwright.config.js` and set `headless: false`.

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

**TC-01 — Successful login with valid credentials**

Steps:
1. Go to https://www.saucedemo.com
2. Enter `standard_user` in the username field
3. Enter `secret_sauce` in the password field
4. Click the Login button

Expected result: The user is redirected to the inventory page (`/inventory.html`) and the page title "Products" is visible.

---

**TC-02 — Locked-out user cannot log in**

Steps:
1. Go to https://www.saucedemo.com
2. Enter `locked_out_user` in the username field
3. Enter `secret_sauce` in the password field
4. Click the Login button

Expected result: An error message appears saying the user has been locked out. The user stays on the login page.

---

**TC-03 — Login fails with a wrong password**

Steps:
1. Go to https://www.saucedemo.com
2. Enter `standard_user` in the username field
3. Enter an incorrect password (e.g. `wrong_password`)
4. Click the Login button

Expected result: An error message appears saying the username and password do not match. The user stays on the login page.

---

**TC-04 — Login fails when both fields are empty**

Steps:
1. Go to https://www.saucedemo.com
2. Leave the username and password fields empty
3. Click the Login button

Expected result: An error message appears saying the username is required. The user stays on the login page.

---

**TC-05 — Login fails when the password field is left blank**

Steps:
1. Go to https://www.saucedemo.com
2. Enter `standard_user` in the username field
3. Leave the password field empty
4. Click the Login button

Expected result: An error message appears saying the password is required. The user stays on the login page.

## How to install and run

**Requirements:** Node.js 18 or later.

```bash
npm install
npx playwright install chromium
npm test
```

The tests run against `https://www.saucedemo.com` in headless Chromium. Results are printed in the terminal. If you want to see the browser, open `playwright.config.js` and set `headless: false`.

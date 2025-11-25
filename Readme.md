# Playwright E2E Tests – GitHub Actions Demo

This project is a simple setup to test **GitHub Actions** using [Playwright](https://playwright.dev/) for end-to-end (E2E) testing.

## 📘 Overview

The project uses **Playwright Test** to run browser-based tests against [https://loginxp.vercel.app/](https://loginxp.vercel.app/).

The configuration file [`playwright.config.ts`](./playwright.config.ts) defines:

-   Test directory: `./e2e`
-   Parallel test execution
-   Automatic retries on CI
-   HTML reporter output
-   Tracing and video recording on retries
-   Base URL for tests
-   Support for multiple browsers (only Chromium enabled by default)

## 🧰 Requirements

-   Node.js 18 or later
-   npm or yarn

## ⚙️ Installation

```bash
git clone https://github.com/dotch3/playwright-github-actions playwright-actions
cd playwright-actions
npm install
```

## ▶️ Running Tests Locally

```bash
npx playwright test
```

To view the generated HTML report:

```bash
npx playwright show-report
```

## 🧪 Running in GitHub Actions

The workflow file [`playwright.yml`](.github/workflows/playwright.yml) runs Playwright tests automatically on every push and pull request to the `main` branch.

```yaml
name: Playwright Tests
on:
    push:
        branches: [main]
    pull_request:
        branches: [main]
jobs:
    test:
        runs-on: ubuntu-latest
        steps:
            - uses: actions/checkout@v4
            - uses: actions/setup-node@v4
              with:
                  node-version: 20
            - run: npm ci
            - run: npx playwright install --with-deps
            - run: npx playwright test
```

## 📁 Project Structure

```
.
├── e2e/                    # E2E test files
├── playwright.config.ts    # Playwright configuration
├── package.json
├── .github/workflows/      # GitHub Actions workflows
└── README.md
```

## 🧾 License

This project is for demonstration and testing purposes only.  
Feel free to modify and reuse it for your CI/CD experiments.

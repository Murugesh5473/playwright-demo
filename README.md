# Playwright E2E Test Automation Framework

A end-to-end test automation framework built with **Playwright** and **TypeScript**, covering both UI and API test scenarios using the Page Object Model (POM) pattern.

## Tech Stack

- [Playwright](https://playwright.dev/) v1.51.1
- TypeScript
- Node.js v18+
- GitHub Actions (CI/CD)

## Project Structure

```
Project_1/
├── .github/
│   └── workflows/
│       └── playwright.yml          # GitHub Actions CI/CD pipeline
├── e2e/
│   ├── framework/
│   │   ├── apiRequests/
│   │   │   └── CommonApiRequest.ts # API request wrapper (POST, GET, PUT)
│   │   ├── apiWaits/
│   │   │   └── CommonApiWaits.ts   # API response wait helpers
│   │   ├── utilities/
│   │   │   ├── Login.ts            # Login page object
│   │   │   └── Books.ts            # Books page object
│   │   └── configs/
│   │       └── demoQa.json         # Test credentials and base URL
│   └── integration/
│       ├── api/
│       │   └── verifyApiCases.spec.ts  # API tests (create, get, update user)
│       └── ui/
│           └── verifyBook.spec.ts      # UI tests (login, search book)
├── playwright.config.ts            # Playwright configuration
└── package.json
```

## What's Being Tested

### UI Tests — [demoqa.com](https://demoqa.com)
- User login to Book Store
- Book search and detail extraction

### API Tests — [reqres.in](https://reqres.in)
- Create user (POST)
- Get user (GET)
- Update user (PUT)

## Getting Started

### Prerequisites

- Node.js v18+
- npm or yarn

### Install Dependencies

```bash
npm install
```

### Install Playwright Browsers

```bash
npx playwright install --with-deps
```

## Running Tests

```bash
# Run all tests
npx playwright test

# Run UI tests only
npx playwright test e2e/integration/ui/

# Run API tests only
npx playwright test e2e/integration/api/

# Run in headed mode (see the browser)
npx playwright test --headed

# Run in debug mode
npx playwright test --debug

# Run with Playwright UI mode
npx playwright test --ui
```

## View Test Report

```bash
npx playwright show-report
```

## Configuration

| Setting | Value |
|---|---|
| Test timeout | 120 seconds |
| Browsers | Chromium, Firefox, WebKit |
| Retries (CI) | 2 |
| Reporter | HTML |
| Trace | On first retry |

Config file: [playwright.config.ts](playwright.config.ts)

## CI/CD

Tests run automatically via **GitHub Actions** on:
- Push to `main` / `master`
- Pull requests

The pipeline installs dependencies, installs browsers, runs all tests, and uploads the HTML report as an artifact (retained for 30 days).

See: [.github/workflows/playwright.yml](.github/workflows/playwright.yml)

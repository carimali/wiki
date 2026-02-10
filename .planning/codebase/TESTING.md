# Testing Patterns

**Analysis Date:** 2026-02-10

## Test Framework

**Runner:**
- ESLint for linting only (static analysis)
- No unit test framework detected (Jest, Vitest, Mocha, etc. not configured)
- Testing limited to lint checks

**Assertion Library:**
- None (no test execution framework)

**Run Commands:**
```bash
npm run lint                 # Run ESLint with fixes
npm test                     # Runs: npm run lint (current test script)
```

## Test File Organization

**Location:**
- No test files found in codebase (`*.test.js`, `*.spec.js`)
- Only ESLint configuration for static analysis
- Test dependency: `eslint-validator` and `eslint-config-xo-space`

**Naming:**
- N/A - no test files present

**Structure:**
- N/A - testing limited to linting

## Test Structure

**Current Testing Approach:**
- Static analysis only via ESLint
- No runtime test execution
- Linting validates code style, naming, and basic patterns
- Build-time validation through `npm test` which runs `npm run lint`

**ESLint Configuration:**
```json
{
  "extends": "xo-space/browser",
  "rules": {
    "semi": [2, "never"],
    "no-return-assign": "off",
    "no-unused-expressions": "off",
    "no-new-func": "off",
    "no-multi-assign": "off",
    "no-mixed-operators": "off",
    "max-params": "off",
    "no-script-url": "off",
    "camelcase": "off",
    "no-warning-comments": "off"
  },
  "globals": {
    "Docsify": true,
    "$docsify": true,
    "process": true
  }
}
```

**Validated patterns:**
- Semicolon usage (enforces no semicolons)
- camelCase naming (disabled for flexibility)
- Return statement patterns
- Function complexity
- Browser globals recognition
- Import/export statement structure

## Mocking

**Framework:** Not applicable - no test framework configured

**Patterns:**
- Global mocks in browser context: `window.$docsify`, `window.Docsify`, `window.Vue`
- Conditional feature detection: `typeof window.Vue !== 'undefined'`
- SSR detection: `process.env.SSR` in conditional compilation

**Example from `src/core/render/compiler.js`:**
```javascript
if (process.env.SSR ? '' : this.contentBase, ...)
```

**DOM Mocking approach:**
- In-browser testing context only (no Node.js test framework)
- Uses real DOM methods: `document.createElement()`, `document.addEventListener()`
- Cache for DOM queries: `cacheNode` object in `src/core/util/dom.js`

## Fixtures and Factories

**Test Data:**
- No test fixtures found
- Integration testing approach preferred (using real DOM)
- Static configuration in `src/core/config.js` serves as default fixtures

**Configuration defaults from `src/core/config.js`:**
```javascript
const config = merge(
  {
    el: '#app',
    repo: '',
    maxLevel: 6,
    subMaxLevel: 0,
    loadSidebar: null,
    loadNavbar: null,
    homepage: 'README.md',
    coverpage: '',
    basePath: '',
    auto2top: false,
    name: '',
    themeColor: '',
    nameLink: window.location.pathname,
    autoHeader: false,
    executeScript: null,
    noEmoji: false,
    ga: '',
    ext: '.md',
    mergeNavbar: false,
    formatUpdated: '',
    externalLinkTarget: '_blank',
    routerMode: 'hash',
    noCompileLinks: []
  },
  window.$docsify
)
```

**Location:**
- N/A - no separate fixture directory

## Coverage

**Requirements:** None enforced

**View Coverage:**
- No coverage tool configured
- Build process includes all source files in `/src` directory
- Rollup bundles output to `/lib`

## Test Types

**Unit Tests:**
- Not implemented
- Could target individual utility functions in `src/core/util/`
- Example candidates: `cached()`, `hyphenate()`, `isPrimitive()`, `isFn()`

**Integration Tests:**
- Not formally implemented
- Browser-based integration implicit through manual testing
- Real DOM required: `src/core/util/dom.js` uses actual document/window APIs

**E2E Tests:**
- Not implemented
- Would need headless browser (Puppeteer, Playwright)
- Currently relies on manual testing and user feedback

## Testing Recommendations

**Current State:**
- This is a browser-based documentation generator (Docsify)
- No automated test suite configured
- Quality assurance through:
  1. ESLint static analysis
  2. Manual testing during development (`npm run dev`)
  3. Live server testing with real documentation

**Testing gaps:**
1. No unit tests for utility functions
2. No integration tests for core features
3. No E2E tests for user workflows
4. No regression test coverage

**Mock pattern from existing code:**

Promise-like mock in `src/core/fetch/ajax.js`:
```javascript
export function get(url, hasBar = false, headers = {}) {
  // ... xhr setup ...
  return {
    then: function (success, error = noop) {
      // ... event listeners ...
    },
    abort: _ => xhr.readyState !== 4 && xhr.abort()
  }
}
```

This manual promise-like implementation could be wrapped in tests.

## Build-Time Validation

**Lint command:**
```bash
npm run lint              # eslint {src,packages} --fix
```

**Build targets checked:**
- `src/` directory - main source code
- `packages/` directory - monorepo packages

**Pre-commit hooks:** None detected (no husky or simple-git-hooks configured)

---

*Testing analysis: 2026-02-10*

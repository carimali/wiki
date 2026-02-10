# Coding Conventions

**Analysis Date:** 2026-02-10

## Naming Patterns

**Files:**
- Lowercase with hyphens for separators: `compiler.js`, `gen-tree.js`, `sidebar.js`
- Grouped by feature in subdirectories: `src/core/render/`, `src/core/fetch/`, `src/core/router/`
- History variants: `history/hash.js`, `history/html5.js`, `history/base.js`

**Functions:**
- camelCase for regular functions: `initMixin`, `fetchMixin`, `renderMixin`, `getAndRemoveConfig`, `getNode`
- Private methods prefixed with underscore: `_initRenderer`, `_matchNotCompileLink`, `_renderTo`, `_renderSidebar`, `_fetch`, `_fetch404`
- Arrow functions for callbacks and simple expressions: `fn => isFn(fn) && fn(vm._lifecycle, vm)`

**Variables:**
- camelCase: `lastRoute`, `cacheNode`, `cacheTree`, `currentPath`, `linkTarget`
- Constants in UPPERCASE: `CONFIG`, `cachedLinks`
- Acronyms lowercase after first letter: `vm` (view model), `xhr` (XMLHttpRequest), `el` (element)
- Single letter for loop indices: `i`, `m`, `n`

**Types/Classes:**
- PascalCase for constructors: `Docsify()`, `Compiler`, `HashHistory`, `HTML5History`
- Factory patterns with `new`: `new Compiler(config, router)`, `new HTML5History(config)`

**Exports:**
- Named exports for utility functions: `export function cached(fn)`, `export function isFn(obj)`
- Default export for module initializers: `export default function()` in `config.js`, `global-api.js`
- Barrel file exports (`src/core/util/index.js`): `export * from './core'`

## Code Style

**Formatting:**
- 2-space indentation
- No semicolons (ESLint rule: `"semi": [2, "never"]`)
- Single quotes for strings: `'string'` (inherited from xo-space base)
- Multi-line object literals: properties on separate lines

**Example formatting:**
```javascript
const proto = Docsify.prototype

initMixin(proto)
routerMixin(proto)
renderMixin(proto)
fetchMixin(proto)
eventMixin(proto)
```

**Linting:**
- ESLint with `xo-space/browser` configuration
- Custom rule overrides in `.eslintrc`:
  - `semi: never` - No semicolons required
  - `camelcase: off` - Allow snake_case when needed
  - `no-warning-comments: off` - Allow TODO/FIXME comments
  - `no-script-url: off` - Allow `javascript:void(0)` URLs
  - `no-new-func: off` - Allow `new Function()` for dynamic code
  - `no-multi-assign: off` - Allow `a = b = c` assignments
  - `max-params: off` - No function parameter limit
- Global variables defined: `Docsify`, `$docsify`, `process`

## Import Organization

**Order:**
1. External dependencies (`import marked from 'marked'`, `import Prism from 'prismjs'`)
2. Relative imports from parent directories (`import {initMixin} from './init'`)
3. Relative imports from same/child directories (`import {isFn, merge, cached, isPrimitive} from '../util/core'`)

**Example from `src/core/render/compiler.js`:**
```javascript
import marked from 'marked'
import Prism from 'prismjs'
import {helper as helperTpl, tree as treeTpl} from './tpl'
import {genTree} from './gen-tree'
import {slugify} from './slugify'
import {emojify} from './emojify'
import {isAbsolutePath, getPath, getParentPath} from '../router/util'
import {isFn, merge, cached, isPrimitive} from '../util/core'
```

**Import aliases:**
- Namespace imports for utility modules: `import * as dom from '../util/dom'`, `import * as util from './util'`
- Destructured imports for specific exports: `import {isMobile} from '../util/env'`
- Renamed imports when needed: `import {helper as helperTpl, tree as treeTpl} from './tpl'`

## Error Handling

**Patterns:**
- Promise-style `.then(success, error)` callbacks:
  ```javascript
  get(url, hasBar, requestHeaders).then(next, _ => loadNested(path, qs, file, next, vm))
  ```
- Error parameter as underscore `_` when unused
- Fallback chains with nested error handlers:
  ```javascript
  req.then(
    (text, opt) => this._renderMain(text, opt, fn),
    _ => {
      this._fetchFallbackPage(file, qs, cb) || this._fetch404(file, qs, cb)
    }
  )
  ```
- Default parameter patterns: `proto._fetch = function (cb = noop)`
- Status code checking: `if (target.status >= 400) { error(target) }`

## Logging

**Framework:** Not used - `console` is available globally in browser context

**Patterns:**
- Direct global access in browser: `window.__EXECUTE_RESULT__`, `window.__current_docsify_compiler__`
- No structured logging framework
- Limited logging needs for browser-based documentation generator

## Comments

**When to Comment:**
- Algorithm explanations for complex logic
- References to external sources or issues
- JSDoc for public API functions and complex parameters
- Non-obvious regex patterns

**Examples from codebase:**
```javascript
/**
 * Fork https://github.com/bendrucker/document-ready/blob/master/index.js
 */
function ready(callback) { ... }

/**
 * Create a cached version of a pure function.
 */
export function cached(fn) { ... }

/**
 * Get Node
 * @param  {String|Element} el
 * @param  {Boolean} noCache
 * @return {Element}
 */
export function getNode(el, noCache = false) { ... }
```

**JSDoc/TSDoc:**
- Parameter docs with `@param {Type} name description`
- Return type with `@return {Type}`
- Examples in comments: `@example find('nav') => document.querySelector('nav')`
- Used selectively for public APIs, not every function

## Function Design

**Size:**
- Utility functions: 5-15 lines (e.g., `hyphenate`, `isPrimitive`)
- Feature functions: 20-40 lines (e.g., `getAndRemoveConfig`)
- Complex logic: 50+ lines (e.g., `_renderMain`, `_initRenderer`)
- Nested helper functions within larger methods common

**Parameters:**
- 1-3 parameters typical
- Options objects used for configuration (`{noCache = false}`)
- Default parameters: `function (cb = noop)`, `function (lang = '')`
- Destructuring for object parameters: `const {maxLevel, subMaxLevel, loadSidebar} = this.config`

**Return Values:**
- Early returns for guard clauses: `if (!path) { return }`
- Promise-like objects with `.then()` and `.abort()` methods
- HTML strings from render functions
- Objects with configuration: `return {str, config}`

**Pattern - Mixin functions:**
```javascript
export function renderMixin(proto) {
  proto._renderTo = function (el, content, replace) { ... }
  proto._renderSidebar = function (text) { ... }
  proto._bindEventOnRendered = function (activeEl) { ... }
}
```

## Module Design

**Exports:**
- Mixins pattern: Functions that attach methods to prototype
  ```javascript
  export function renderMixin(proto) {
    proto._renderTo = function () { ... }
  }
  ```
- Utility modules: Multiple named exports
  ```javascript
  export function getNode(el, noCache = false) { ... }
  export const $ = inBrowser && document
  export function find(el, node) { ... }
  ```
- Single default export for initialization
  ```javascript
  export default function () {
    const config = merge({ ... }, window.$docsify)
    return config
  }
  ```

**Barrel Files:**
- Re-export pattern in `src/core/util/index.js`:
  ```javascript
  export * from './core'
  export * from './env'
  export * from '../router/util'
  ```
- Allows `import {isFn, isPrimitive} from '../util'` instead of `'../util/core'`

**Module lifecycle:**
- Constructor mixins: `initMixin`, `routerMixin`, `renderMixin`, `fetchMixin`, `eventMixin`
- Initialization functions: `initRouter`, `initRender`, `initEvent`, `initFetch`, `initLifecycle`
- Plugin pattern: Functions called with `(hook, vm)` parameters

---

*Convention analysis: 2026-02-10*

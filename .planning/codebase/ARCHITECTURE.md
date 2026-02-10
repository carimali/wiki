# Architecture

**Analysis Date:** 2026-02-10

## Pattern Overview

**Overall:** Single Page Application (SPA) with Mixin-based Modular Architecture

**Key Characteristics:**
- Mixins inject functionality into a central `Docsify` prototype
- Event-driven lifecycle with hooks (init, mounted, beforeEach, afterEach, doneEach, ready)
- Document-centric rendering (Markdown compilation to HTML)
- Router-based navigation with client-side history management
- Plugin system for extending functionality without modifying core

## Layers

**Core Engine (`src/core/`):**
- Purpose: Main application logic and lifecycle management
- Location: `src/core/index.js` - Entry point; `src/core/init/index.js` - Initialization mixin
- Contains: Prototype definition, mixin composition, lifecycle hooks
- Depends on: No internal dependencies, bootstraps other layers
- Used by: Everything else (all features attached to `Docsify.prototype`)

**Initialization Layer (`src/core/init/`):**
- Purpose: Setup configuration, initialize subsystems in correct order, manage hook lifecycle
- Location: `src/core/init/index.js` (initMixin), `src/core/init/lifecycle.js` (hook system)
- Contains: Mixin registration, plugin loading, lifecycle callback management
- Depends on: config, all init functions (router, render, fetch, event)
- Used by: Core Docsify class during instantiation

**Router Layer (`src/core/router/`):**
- Purpose: URL/hash parsing, navigation history, path resolution
- Location: `src/core/router/index.js` (mixins), `src/core/router/history/` (implementations)
- Contains: Hash mode (HashHistory), HTML5 mode (HTML5History), path utilities
- Depends on: Configuration, util/env for feature detection
- Used by: Renderer (path resolution), fetcher (file location), event system

**Fetch Layer (`src/core/fetch/`):**
- Purpose: Load markdown/HTML files, handle fallbacks, 404 pages, nested sidebar/navbar loading
- Location: `src/core/fetch/index.js`, `src/core/fetch/ajax.js`
- Contains: XHR request management, nested resource loading, language fallback handling
- Depends on: Router (for file paths), config (for request headers)
- Used by: Initialization (initial page load), router change callbacks

**Render Layer (`src/core/render/`):**
- Purpose: Compile markdown to HTML, manage DOM updates, handle templates
- Location: `src/core/render/index.js`, `src/core/render/compiler.js`, `src/core/render/tpl.js`
- Contains: Markdown compiler (via marked), syntax highlighting (Prismjs), DOM injection, template generation
- Depends on: marked, Prismjs, util/dom, router utilities
- Used by: Fetch layer (renders loaded content), Initialization (initial HTML setup)

**Event Layer (`src/core/event/`):**
- Purpose: DOM event binding, scroll handling, sidebar/navbar interaction
- Location: `src/core/event/index.js`, `src/core/event/sidebar.js`, `src/core/event/scroll.js`
- Contains: Event listeners, scroll activation, sidebar toggle/collapse logic
- Depends on: util/dom, router
- Used by: Render layer (event binding after render), Initialization (early event setup)

**Utilities (`src/core/util/`):**
- Purpose: DOM manipulation, type checking, environment detection, polyfills
- Location: `src/core/util/core.js`, `src/core/util/dom.js`, `src/core/util/env.js`
- Contains: Re-exported from `index.js`, DOM selectors/manipulation, type predicates
- Depends on: Browser APIs only
- Used by: All layers

## Data Flow

**Initial Page Load:**
1. HTML page loaded, `Docsify()` instantiated in `ready()` callback
2. `_init()` creates config from `window.$docsify` and script data attributes
3. `initLifecycle(vm)` registers hook management
4. `initPlugin(vm)` loads user plugins via hook system
5. `callHook(vm, 'init')` - plugins execute initialization
6. `initRouter(vm)` - establishes current route from URL/hash
7. `initRender(vm)` - creates base DOM structure, Compiler instance
8. `initEvent(vm)` - binds sidebar/scroll events
9. `initFetch(vm)` - loads initial page content or SSR handling
10. `$fetch()` - loads markdown, renders it, calls `$resetEvents()`
11. `callHook(vm, 'mounted')` - plugins execute post-render
12. `callHook(vm, 'doneEach')` - page-specific plugins finish
13. `callHook(vm, 'ready')` - app fully initialized

**Navigation Flow:**
1. Route change detected (hash/popstate)
2. `router.onchange()` callback fires
3. `updateRender(vm)` parses new route
4. `vm._updateRender()` updates name link
5. If path same, call `vm.$resetEvents()` only
6. If path different, call `vm.$fetch()` - loads markdown, renders, resets events
7. Lifecycle: `beforeEach` → render → `afterEach` → `doneEach` → `ready`

**Document Rendering Flow:**
1. Fetch loads markdown text
2. `callHook(vm, 'beforeEach', text)` - plugins modify markdown
3. `Compiler.compile(tokens)` - marked parses markdown, Prismjs highlights code
4. `_renderMain(html)` injects into `.markdown-section`
5. `_renderSidebar()` generates TOC if configured
6. `_bindEventOnRendered()` - scroll activation, auto headers, auto-scroll
7. `callHook(vm, 'afterEach', html)` - plugins modify DOM
8. `executeScript()` - runs Vue/custom scripts if configured

**State Management:**
- Global: `window.$docsify` (config), `window.__current_docsify_compiler__` (compiler instance)
- Instance: `vm.route` (current location), `vm.compiler` (Compiler instance), `vm.router` (Router instance)
- Cache: `Compiler.cacheTree` (TOC tree), `Compiler.cacheTOC` (links), `Compiler.toc` (current page TOC)
- Last Route: Tracked to avoid re-rendering same page

## Key Abstractions

**Compiler:**
- Purpose: Converts markdown to HTML, manages syntax highlighting, generates sidebars/TOC
- Examples: `src/core/render/compiler.js` exports `Compiler` class
- Pattern: Class with methods (compile, sidebar, subSidebar), uses `marked` and custom token processors

**Router (Abstract/Hash/HTML5):**
- Purpose: Encapsulates routing mode behavior
- Examples: `src/core/router/history/base.js`, `src/core/router/history/hash.js`, `src/core/router/history/html5.js`
- Pattern: Base class with subclass override (strategy pattern), `onchange(callback)` method

**Hooks System:**
- Purpose: Plugin integration points (beforeEach, afterEach, doneEach, mounted, ready, init)
- Examples: `src/core/init/lifecycle.js`
- Pattern: Hook registry with `callHook(vm, name, ...args)` executor

**Plugins:**
- Purpose: Extend Docsify without core modifications
- Examples: `src/plugins/search/index.js`, `src/plugins/emoji.js`
- Pattern: `install(hook, vm)` function that registers hooks

## Entry Points

**index.html:**
- Location: `/index.html`
- Triggers: Browser loads page
- Responsibilities: Sets `window.$docsify` config, loads CSS themes, loads `/lib/docsify.js`

**Docsify Constructor:**
- Location: `src/core/index.js` line 21-23
- Triggers: DOM ready (line 41: `ready(_ => new Docsify())`)
- Responsibilities: Calls `_init()` to bootstrap entire app

**`_init()` Mixin:**
- Location: `src/core/init/index.js` line 10-22
- Triggers: Constructor invocation
- Responsibilities: Initialize all subsystems in sequence

## Error Handling

**Strategy:** Graceful degradation with fallbacks

**Patterns:**
- Fetch errors trigger fallback language load (`_fetchFallbackPage`), then 404 page (`_fetch404`)
- Missing markdown renders 404 message (`<h1>404 - Not found</h1>`)
- Missing DOM elements checked before manipulation (e.g., `if (!el) return`)
- Script execution wrapped in try-catch via `setTimeout` (line 26-28 in render/index.js)
- Router supports multiple history modes; falls back to hash if HTML5 unsupported

## Cross-Cutting Concerns

**Logging:** No built-in logging; relies on browser console or custom plugins

**Validation:**
- Type checks via `isPrimitive()`, `isFn()` in `src/core/util/core.js`
- Path validation via regex (absolute vs relative) in `src/core/router/util.js`
- File extension validation for HTML detection

**Authentication:** No built-in auth; delegated to parent page via `window.$docsify` config

**Caching:**
- Markdown content cached implicitly by fetch layer (no explicit cache invalidation)
- Compiler caches trees and TOC trees
- Search plugin caches index with configurable TTL (`maxAge`)

---

*Architecture analysis: 2026-02-10*

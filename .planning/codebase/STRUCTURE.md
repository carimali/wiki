# Codebase Structure

**Analysis Date:** 2026-02-10

## Directory Layout

```
/c/work_aa/wiki/
├── src/                        # Source code
│   ├── core/                   # Core engine (mixins, lifecycle, layers)
│   │   ├── index.js            # Docsify class, mixin application
│   │   ├── config.js           # Configuration from window.$docsify and script attrs
│   │   ├── global-api.js       # Global API exposure
│   │   ├── init/               # Initialization mixin
│   │   │   ├── index.js        # initMixin - bootstrap subsystems
│   │   │   └── lifecycle.js    # Hook system (init, mounted, beforeEach, etc)
│   │   ├── router/             # Routing layer
│   │   │   ├── index.js        # routerMixin, initRouter
│   │   │   ├── util.js         # Path utilities (getPath, getParentPath, etc)
│   │   │   └── history/        # Router mode implementations
│   │   │       ├── base.js     # Base history class
│   │   │       ├── hash.js     # Hash-based routing (default)
│   │   │       ├── html5.js    # HTML5 pushState routing
│   │   │       └── abstract.js # Abstract base (minimal)
│   │   ├── fetch/              # Content fetching layer
│   │   │   ├── index.js        # fetchMixin - load markdown, sidebars, navbars
│   │   │   └── ajax.js         # XHR wrapper (get function)
│   │   ├── render/             # Markdown-to-HTML rendering layer
│   │   │   ├── index.js        # renderMixin, initRender - DOM updates
│   │   │   ├── compiler.js     # Compiler class - marked + custom processing
│   │   │   ├── tpl.js          # HTML templates (main, nav, sidebar, etc)
│   │   │   ├── gen-tree.js     # TOC tree generation
│   │   │   ├── embed.js        # Embed/include preprocessing
│   │   │   ├── slugify.js      # Heading ID generation
│   │   │   ├── emojify.js      # Emoji replacement
│   │   │   └── progressbar.js  # Loading progress indicator
│   │   ├── event/              # Event binding and handlers
│   │   │   ├── index.js        # eventMixin, initEvent
│   │   │   ├── sidebar.js      # Sidebar toggle, collapse, sticky, active marker
│   │   │   └── scroll.js       # Scroll-to-anchor, scroll-activate-nav
│   │   └── util/               # Utility functions
│   │       ├── index.js        # Re-exports from submodules
│   │       ├── core.js         # Type checking, object utilities
│   │       ├── env.js          # Browser detection, feature detection
│   │       └── polyfill/       # Browser compatibility
│   │           └── css-vars.js # CSS custom properties shim
│   └── plugins/                # Optional plugins
│       ├── search/             # Full-text search
│       │   ├── index.js        # Install function, config
│       │   ├── search.js       # Search index building, query logic
│       │   └── component.js    # Search UI/DOM
│       ├── front-matter/       # YAML front-matter parsing
│       │   ├── index.js        # Install function
│       │   ├── parser.js       # YAML parsing logic
│       │   └── yaml.js         # YAML tokenizer
│       ├── emoji.js            # Emoji shortcode replacement
│       ├── disqus.js           # Disqus comments integration
│       ├── gitalk.js           # Gitalk comments integration
│       ├── ga.js               # Google Analytics tracking
│       ├── external-script.js  # External script loading
│       └── zoom-image.js       # Image zoom/modal on click
├── src/themes/                 # CSS themes (Stylus source)
│   ├── basic/                  # Base theme styles
│   │   ├── _layout.styl        # Main layout structure
│   │   └── _coverpage.styl     # Cover page styles
│   ├── vue.styl                # Vue theme (default)
│   ├── dark.styl               # Dark theme
│   ├── buble.styl              # Buble theme
│   └── pure.styl               # Pure theme
├── build/                      # Build configuration and scripts
│   ├── build.js                # Rollup build orchestrator (watch + build modes)
│   ├── ssr.js                  # Server-side rendering build
│   ├── mincss.js               # CSS minification
│   ├── cover.js                # Cover page generation
│   └── release.sh              # Release/publish script
├── packages/                   # Monorepo packages (lerna)
│   └── docsify-server-renderer/ # SSR package
├── docs/                       # Documentation content (not source)
│   ├── docs-en/                # English docs
│   ├── docs-it/                # Italian docs
│   ├── docs-de/                # German docs
│   ├── docs-es/                # Spanish docs
│   ├── docs-ru/                # Russian docs
│   ├── docs-zh/                # Chinese docs
│   └── it/                     # Italian docs (alternate path)
├── index.html                  # Entry point - page load, config, script inject
├── package.json                # Dependencies, build scripts
├── lerna.json                  # Monorepo configuration
├── .eslintrc                   # Linting rules
└── .gitignore                  # Git exclusions
```

## Directory Purposes

**`src/core/`:**
- Purpose: Core Docsify engine with all subsystems (init, router, render, fetch, event)
- Contains: Mixins applied to `Docsify.prototype`, configuration, utilities
- Key files: `index.js` (entry), `config.js` (config loading)

**`src/core/init/`:**
- Purpose: Lifecycle and plugin initialization
- Contains: Hook system, plugin loader, initialization sequence
- Key files: `lifecycle.js` (hook registry and executor)

**`src/core/router/`:**
- Purpose: URL parsing and navigation management
- Contains: Hash vs HTML5 mode routing, path utilities
- Key files: `history/hash.js` (default), `util.js` (path resolution)

**`src/core/fetch/`:**
- Purpose: Load markdown/HTML documents and sidebar/navbar files
- Contains: XHR request logic, fallback handling, 404 page loading
- Key files: `index.js` (public methods), `ajax.js` (XHR wrapper)

**`src/core/render/`:**
- Purpose: Compile markdown and update DOM
- Contains: Markdown compiler (marked), syntax highlighting (Prismjs), templates
- Key files: `compiler.js` (Compiler class), `tpl.js` (HTML templates)

**`src/core/event/`:**
- Purpose: DOM event handling and interaction
- Contains: Scroll events, sidebar interaction, navigation activation
- Key files: `sidebar.js` (toggle/collapse/sticky logic)

**`src/core/util/`:**
- Purpose: Shared utilities used across layers
- Contains: DOM manipulation, type predicates, browser detection
- Key files: `core.js` (merge, isPrimitive), `dom.js` (DOM API)

**`src/plugins/`:**
- Purpose: Optional features that extend core via hook system
- Contains: Search, front-matter, emoji, comments, analytics, etc.
- Key files: Each plugin has `index.js` with `install(hook, vm)` function

**`src/themes/`:**
- Purpose: CSS styling (compiled to `/themes/` during build)
- Contains: Stylus source for multiple visual themes
- Key files: `basic/_layout.styl` (base layout), `vue.styl` (default theme)

**`build/`:**
- Purpose: Build orchestration and configuration
- Contains: Rollup setup, file watchers, minification, release scripts
- Key files: `build.js` (main orchestrator - core + plugins)

**`docs/`:**
- Purpose: Documentation content (markdown files, images, media)
- Contains: Multi-language site content (not executable code)
- Key files: README.md, _sidebar.md, _navbar.md in each language dir

## Key File Locations

**Entry Points:**
- `/index.html`: HTML entry point - loads config, themes, and `/lib/docsify.js`
- `src/core/index.js`: Docsify class definition - bootstraps app on DOM ready
- `src/core/init/index.js`: `_init()` - initialization sequence

**Configuration:**
- `index.html` (window.$docsify object in <script>)
- `src/core/config.js` - loads and validates config

**Core Logic:**
- `src/core/init/lifecycle.js` - Hook system
- `src/core/render/compiler.js` - Markdown compilation
- `src/core/router/history/hash.js` - Default routing
- `src/core/fetch/ajax.js` - HTTP requests

**Testing:**
- `.eslintrc` - Linting configuration (no unit tests)

## Naming Conventions

**Files:**
- Index files: `index.js` (for module entry or grouping)
- Mixins: Suffix `.js`, export as `function {Name}Mixin(proto)`
- Classes: `ClassName.js`, export as `export class ClassName`
- Utilities: `name.js`, export functions directly
- History modes: `base.js`, `hash.js`, `html5.js` in `router/history/`

**Directories:**
- Feature grouping: `src/core/{feature}/` for init, router, fetch, render, event
- Camel case: No hyphens in feature directories (hash-routing not hash-routing)
- Themes: Single file per theme (`vue.styl`, `dark.styl`), except `basic/` for shared base

**Variables/Functions:**
- Private methods: Prefix `_` (e.g., `_init()`, `_renderTo()`)
- Public methods: No prefix (e.g., `$fetch()`, `$resetEvents()`)
- Mixin names: `{Feature}Mixin` (e.g., `initMixin`, `routerMixin`)
- Hooks: Camel case without prefix (init, mounted, beforeEach, afterEach)

**Classes:**
- Compiler: `src/core/render/compiler.js` - Compiler class
- Router modes: `HashHistory`, `HTML5History` classes in `history/` subdir

## Where to Add New Code

**New Feature (Markdown extension, new hook behavior):**
- Core logic: `src/core/{layer}/` - Add new file or extend existing class
- Tests: No test directory; use ESLint
- Entry: Hook into initialization sequence in `src/core/init/index.js` if bootstrapping needed

**New Plugin (Search alternative, comments system, analytics):**
- Implementation: `src/plugins/{plugin-name}/index.js` (or directory if complex)
- Pattern: Export `install(hook, vm)` function
- Registration: Auto-loaded in build/build.js `buildAllPlugin()` if added to plugins array
- Build: Update `build/build.js` line 55-64 to include new plugin

**New Theme:**
- Style file: `src/themes/{name}.styl`
- Extends: Import `src/themes/basic/` for base layout
- Build: Auto-compiled during `npm run build:css`
- HTML: Add stylesheet link in `index.html` with title attribute for theme switching

**Utilities:**
- Shared helpers: `src/core/util/` (core.js for types, dom.js for DOM, env.js for detection)
- Feature-specific: Keep in feature directory if only used there

**Language/Documentation:**
- Content: Add markdown files to `docs/docs-{lang}/`
- Navigation: Update `_sidebar.md` and `_navbar.md` in language directory
- Alias: Configure in index.html `window.$docsify.alias` for URL routing

## Special Directories

**`lib/`:**
- Purpose: Compiled build output
- Generated: Yes (by `npm run build`)
- Committed: No (.gitignore excludes)
- Contents: `docsify.js`, `docsify.min.js`, `plugins/`, `themes/`

**`themes/`:**
- Purpose: Compiled CSS themes
- Generated: Yes (by `npm run build:css`)
- Committed: No (.gitignore excludes)
- Contents: `.css` files compiled from `src/themes/*.styl`

**`.claude/`:**
- Purpose: Agent-specific configuration and scripts (not part of core project)
- Generated: Yes (by agents)
- Committed: No

**`.planning/`:**
- Purpose: Analysis and planning documents for development
- Generated: Yes (by GSD commands)
- Committed: No (optional)

---

*Structure analysis: 2026-02-10*

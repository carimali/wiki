# Technology Stack

**Analysis Date:** 2026-02-10

## Languages

**Primary:**
- JavaScript (ES6) - All source code in `src/` uses ES6 module syntax with import/export
- Stylus - CSS preprocessor for theme styles in `src/themes/`
- HTML - Entry point and plugin templates

**Secondary:**
- Node.js scripts - Build automation and server utilities in `build/` and root

## Runtime

**Environment:**
- Node.js stable (no specific version pinned, see `.travis.yml`)
- Browser-based SPA execution with optional server-side rendering (SSR)

**Package Manager:**
- npm
- Lockfile: Not committed (npm-shrinkwrap or package-lock handled per environment)

## Frameworks

**Core:**
- Custom framework (Docsify) - Documentation generator built from scratch at `src/core/index.js`

**Build/Dev:**
- Rollup - Module bundler for production builds (v0.53.3)
  - Plugins: buble (transpilation), commonjs, node-resolve, uglify, replace
- Stylus - CSS preprocessor (v0.54.7)
- npm-run-all - Parallel task runner (v4.1.5)
- live-server - Development server (v1.2.1)
- Lerna - Monorepo package management (v3.20.2)

**Build Output:**
- Format: IIFE (Immediately Invoked Function Expression) at `lib/docsify.js` and `lib/docsify.min.js`
- Built CSS: `lib/themes/` and `themes/` directories
- Build command: `npm run build` produces minified and unminified versions

## Key Dependencies

**Critical:**
- `marked` (v4.0.10) - Markdown parser for rendering `.md` files as HTML
- `prismjs` (v1.18.0) - Syntax highlighting for code blocks
- `handlebars` (v4.5.3) - Template rendering engine

**Infrastructure:**
- `medium-zoom` (v0.4.0) - Image zoom functionality
- `tweezer.js` (v1.5.0) - Animation library for smooth scrolling
- `tinydate` (v1.2.0) - Date utility
- `conventional-changelog` (v3.1.19) - Changelog generation from commits

**Server-side (packages/docsify-server-renderer):**
- `node-fetch` (v2.6.1) - HTTP requests for SSR
- `resolve-pathname` (v2.1.0) - URL path resolution
- `debug` (v2.6.8) - Debug logging

## Configuration

**Environment:**
- `.travis.yml` - CI configuration using Travis CI with Node.js stable
- Build environment variable: `NODE_ENV=production` for minification
- SSR mode: `SSR=1` environment variable activates server-side rendering

**Build:**
- `build/build.js` - Main build orchestrator
  - Bundles `src/core/index.js` → `lib/docsify.js`
  - Bundles plugins from `src/plugins/` → `lib/docsify.*.js`
- `build/ssr.js` - Server-side renderer build
- `build/mincss.js` - CSS minification
- `build/cover.js` - Unknown purpose (likely coverage-related)
- `build/release.sh` - Release automation

**Linting:**
- `.eslintrc` - Extends `xo-space/browser` config at root level
  - Disables: return-assign, unused-expressions, new-func, multi-assign, mixed-operators, script-url, camelcase, warning-comments
  - Semicolons: disabled (no semicolons required)
  - Globals: `Docsify`, `$docsify`, `process`

## Platform Requirements

**Development:**
- Node.js (stable version)
- npm package manager
- Git (for Lerna monorepo)
- Requires: `npm run bootstrap` for initial setup (installs deps + lerna bootstrap + SSR build)

**Production:**
- Browser support: Modern browsers with ES5+ support (IIFE format compatible with older browsers)
- Deployment: Static file hosting or Node.js server for SSR variant
- Static assets: HTML entry point + built JS/CSS in `lib/` directory

## Build Commands

```bash
npm run bootstrap       # Initial setup with lerna
npm run dev            # Watch mode with live-server (port 3000)
npm run dev:ssr        # Dev mode with server-side rendering
npm run build          # Production build (JS + CSS + minified)
npm run lint           # ESLint check and fix
npm test               # Run linting only (no unit tests defined)
npm run serve          # Run live-server only
npm run serve:ssr      # Run with SSR middleware
```

**Build Output:**
- `lib/docsify.js` - Unminified bundle
- `lib/docsify.min.js` - Minified bundle
- `lib/themes/` - Compiled CSS themes
- `themes/` - Source theme compilations

## Module Structure

**Entry Point:** `src/core/index.js`
- Mixin pattern for modular initialization
- Executed on DOM ready via document ready hook

**Core Modules (src/core/):**
- `init/` - Lifecycle and initialization
- `router/` - Routing and path resolution
- `render/` - Compiler and template rendering
- `fetch/` - Document fetching via AJAX
- `event/` - Event handling (scroll, sidebar, mobile)
- `util/` - Shared utilities

**Plugins (src/plugins/):**
- Optional integrations compiled separately
- Located at `lib/docsify.*.js` (e.g., `docsify.emoji.js`)

---

*Stack analysis: 2026-02-10*

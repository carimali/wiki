# External Integrations

**Analysis Date:** 2026-02-10

## APIs & External Services

**Analytics:**
- Google Analytics (ga.js) - Page view tracking for documentation
  - SDK: Google Analytics script injected from `https://www.google-analytics.com/analytics.js`
  - Configuration: `$docsify.ga` config property
  - Plugin location: `src/plugins/ga.js`
  - Tracking: Page views triggered before each render via `hook.beforeEach()`

**Comments/Discussion:**
- Disqus - Comment section integration for documentation pages
  - SDK: CDN script from `https://{disqus-shortname}.disqus.com/embed.js`
  - Configuration: `vm.config.disqus` (shortname required)
  - Plugin location: `src/plugins/disqus.js`
  - Integration: Mounts comment thread div in page content, resets on navigation

**Community Engagement:**
- Gitalk - GitHub-based comment system alternative to Disqus
  - SDK: External gitalk library (loaded client-side)
  - Configuration: Requires GitHub app credentials (configured elsewhere)
  - Plugin location: `src/plugins/gitalk.js`
  - Integration: Mounts gitalk container, renders on page mount

## Data Storage

**Databases:**
- None - Purely static documentation generator
- Document source: Markdown files (.md) loaded via AJAX from filesystem or CDN

**File Storage:**
- Local filesystem (during development): `docs/` directory
- Remote URLs: Supports loading docs from GitHub raw content via alias mappings
  - Example: `/it/(.*)` aliases to `https://raw.githubusercontent.com/docsifyjs/docs-it/master/$1`
  - Configured in `index.html` via `$docsify.alias` property

**Caching:**
- Browser cache - Static assets cached by live-server in dev, HTTP headers in production
- No server-side caching layer

## Authentication & Identity

**Auth Provider:**
- None for documentation access
- Gitalk plugin supports GitHub OAuth (implicit, handled by Gitalk library)
- No explicit user authentication in core

## Monitoring & Observability

**Error Tracking:**
- None detected - No Sentry, LogRocket, or similar
- Console errors only

**Logs:**
- Development: live-server logs to stdout
- Browser console: Docsify logs component lifecycle via `console.log/error`
- Build logs: Rollup logs bundle output and errors to stdout

## CI/CD & Deployment

**Hosting:**
- Static hosting compatible (serves compiled `lib/` and `docs/` directories)
- Optional Node.js server via `npm run serve` or `npm run serve:ssr` for SSR variant
- Development server: live-server on port 3000 (configured in `server.js`)

**CI Pipeline:**
- Travis CI (`.travis.yml`)
  - Language: Node.js
  - Node version: stable
  - Only builds on commit; no automated deployment script configured
  - `npm test` runs ESLint only

**Deployment:**
- Manual deployment required (no automated push to hosting in config)
- Build artifacts: `lib/` directory + static docs
- Package publishing: Uses npm release process via `npm pub` and `npm pub:next`

## Environment Configuration

**Required env vars:**
- `NODE_ENV=production` - Enables minification in build process
- `SSR=1` - Enables server-side rendering mode (optional)
- `RELEASE_TAG` - For publishing (used in `build/release.sh`)
- `VERSION` - Override version in bundle (defaults to package.json version)

**Secrets location:**
- None detected - No API keys or secrets in codebase
- External service credentials would be configured in HTML config:
  - `$docsify.ga` - Google Analytics ID (public)
  - `vm.config.disqus` - Disqus shortname (public)
  - Gitalk - GitHub app credentials (must be configured client-side)

## Webhooks & Callbacks

**Incoming:**
- None - Static documentation, no server-side webhook endpoints

**Outgoing:**
- Analytics tracking - Google Analytics events sent from browser
- Comment sync - Disqus and Gitalk sync comments via their respective services (handled by external libraries)

## Plugin System

**Extensible Integrations:**

Located in `src/plugins/` with hook-based architecture:
- `hook.beforeEach()` - Fires before rendering each page
- `hook.mounted()` - Fires when DOM is mounted
- `hook.doneEach()` - Fires after each page render completes
- `hook.init()` - Fires on first initialization

**Available Plugins (compiled to lib/):**
- `emoji.js` - Emoji rendering (13KB, self-contained)
- `external-script.js` - Load and execute external scripts
- `ga.js` - Google Analytics integration
- `disqus.js` - Disqus comments
- `gitalk.js` - Gitalk comments
- `zoom-image.js` - Image zoom via medium-zoom library
- `search/` - Full-text search plugin (directory with multiple files)
- `front-matter/` - YAML front-matter parsing for metadata

## Content Aliasing & Routing

**Configuration in index.html:**
```javascript
alias: {
  '.*?/changelog': 'https://raw.githubusercontent.com/docsifyjs/docsify/master/CHANGELOG',
  '/.*?/_navbar.md': '/_navbar.md',
  '/it/(.*)': 'https://raw.githubusercontent.com/docsifyjs/docs-it/master/$1',
  '/zh-cn/(.*)': 'https://raw.githubusercontent.com/docsifyjs/docs-zh/master/$1',
  '/de-de/(.*)': 'https://raw.githubusercontent.com/docsifyjs/docs-de/master/$1',
  '/ru/(.*)': 'https://raw.githubusercontent.com/docsifyjs/docs-ru/master/$1',
  '/es/(.*)': 'https://raw.githubusercontent.com/docsifyjs/docs-es/master/$1'
}
```

**Used for:**
- Internationalization - Route language prefixes to separate GitHub repos
- Shared content - Load navbar/sidebar from centralized location
- External content - Pull changelog from main repo

## Build Dependencies (Not Runtime)

**Build-only integrations:**
- npm registry - Package installation
- GitHub (for lerna and dependencies)
- npm publish (for package release)

---

*Integration audit: 2026-02-10*

# Caricare Wiki - Project Documentation

## Project Overview

The Caricare Wiki is a documentation website built with **Docsify** that serves as the official wiki for the **CARIcare** platform. CARIcare is an online platform for the management and monitoring of Carimali and Elektra coffee machines. The wiki is hosted on GitHub Pages and provides comprehensive documentation for users of Carimali and Elektra products.

The project implements a multilingual documentation system supporting English, Italian, Chinese, German, Russian, and Spanish. It features a custom UI with a distinctive blue-themed navigation bar and responsive design that works across devices (smartphones, tablets, and PCs).

### Key Features
- Real-time monitoring of coffee machine status, product dispensing, and error notifications
- Remote control capabilities for modifying recipes, prices, and machine configurations
- Support ticket management system
- Customer and user management with role-based access
- API integration for external system connectivity
- Custom tagging system for data classification

## Project Architecture

The repository follows a monorepo structure managed with **Lerna**, containing both the Docsify documentation generator and the wiki content:

- `docs/` - Contains the published wiki content and configuration files (`_sidebar.md`, `_navbar.md`, `index.html`)
- `docs/docs-*/` - Localized content directories (e.g., `docs/docs-it`, `docs/docs-en`)
- `docs/_images` and `docs/_media` - Assets referenced by the wiki
- `src/`, `packages/`, `build/` - Docsify source code and build scripts
- `server.js` - Local development server implementation
- `packages/` - Additional packages in the monorepo (currently `docsify-server-renderer`)

## Technologies Used

- **Documentation Generator**: Docsify (dynamic documentation site generator)
- **Frontend**: Vanilla JavaScript, HTML, CSS
- **Build Tools**: Rollup, Stylus, npm-run-all
- **Libraries**: marked (Markdown parser), prismjs (syntax highlighting), medium-zoom, handlebars
- **Package Management**: npm, Lerna (monorepo management)
- **Development Server**: live-server
- **Styling**: Custom CSS with multiple theme support (vue, dark, buble, pure)

## Building and Running

### Prerequisites
- Node.js
- Git
- VS Code or another editor that supports Markdown

### Installation and Local Development

1. **Clone the repository**
   ```bash
   git clone https://github.com/carimali/wiki.git
   ```

2. **Install dependencies**
   ```bash
   npm install
   npm i docsify-cli -g
   ```

3. **Start the local server**
   ```bash
   # For Unix/Linux/Mac:
   docsify serve docs
   
   # For Windows:
   npx docsify serve docs
   ```

4. **Alternative development commands**
   ```bash
   npm run serve          # Start local server on http://localhost:3000
   npm run dev           # Run server with JS/CSS watchers
   npm run lint          # Run ESLint with auto-fix
   npm test             # Run linting only
   ```

The wiki will be accessible at `http://localhost:3000`. The local server automatically reflects changes made to Markdown files in the `docs` directory.

## Development Conventions

### File Structure
- Markdown files are stored in the `docs/` directory
- Language-specific content is organized in subdirectories (`docs/docs-en/`, `docs/docs-it/`, etc.)
- Images and media assets are stored in `docs/_images` and `docs/_media`
- Navigation is controlled via `_sidebar.md` and `_navbar.md`

### Styling and Customization
- The project uses custom CSS in the `index.html` file to override default Docsify themes
- A distinctive blue color scheme (`#053752`) is applied throughout the interface
- Responsive design considerations for mobile and desktop views
- Custom JavaScript for enhanced navigation and scrolling behavior

### Code Style
- JavaScript follows `xo-space` conventions: 2-space indentation, no semicolons
- ESLint configuration is defined in `.eslintrc`
- File naming should follow existing patterns (e.g., `machine-*.png`, `docs-<lang>`)

### Localization
- The wiki supports multiple languages through the alias system in `index.html`
- Navigation elements are language-aware and switch content appropriately
- Flag images are used in the navigation bar for language selection

## Content Management

To update the wiki, edit the Markdown files in the `docs` directory. The local server will automatically reflect changes. Key content files include:

- `docs/README.md` - Main landing page content
- `docs/_sidebar.md` - Navigation sidebar structure
- `docs/_navbar.md` - Top navigation bar
- `docs/_coverpage.md` - Cover page (currently disabled in the custom CSS)

## Deployment

The wiki is designed to be deployed on GitHub Pages. The `index.html` file in the `docs` directory contains all necessary configuration and customizations for the production deployment.

## Testing

The project includes linting checks via ESLint. Run `npm test` or `npm run lint` before submitting changes. There are no unit tests in this repository, as it primarily consists of documentation content.

## Git Workflow

- Keep commits concise and scoped to specific changes
- Use short, descriptive commit messages
- Include PR numbers when referencing related pull requests
- Smaller PRs typically review faster than large, complex changes
- Follow the existing commit message conventions used in the repository
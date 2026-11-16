<a name="uistackjs"></a>

# Aiursoft UIStack.js

[![Pipeline](https://badge-proxy.aiursoft.com/aiursoft/UIStack.js/badges/master/pipeline.svg)](https://gitlab.aiursoft.com/aiursoft/UIStack.js/-/pipelines) [![npm](https://img.shields.io/npm/v/@aiursoft/uistack)](https://www.npmjs.com/package/@aiursoft/uistack)

Shared styles, scripts, fonts and images for Aiursoft applications.

## Overview

### What is UIStack.js?

Shared styles, scripts, fonts and images for Aiursoft applications.

<a name="install"></a>

## Installation

Install the package in your project:

```bash
npm install @aiursoft/uistack
```

The npm package contains compiled `dist/` assets. Serve its CSS, JavaScript, fonts and images together so relative asset URLs remain valid. Node.js is needed to install or build the package, not to run the deployed browser assets.

## Usage

Save the following as `index.html` beside `node_modules/` and serve that directory over HTTP with your existing static-file server:

```html
<!doctype html>
<html lang="en" data-bs-theme="light">
  <meta charset="utf-8">
  <title>UIStack example</title>
  <link rel="stylesheet" href="./node_modules/@aiursoft/uistack/dist/css/app.css">
  <body>
    <main class="container py-4">
      <h1>UIStack</h1>
      <button class="btn btn-primary" type="button">Styled button</button>
    </main>
    <script src="./node_modules/@aiursoft/uistack/dist/js/app.js" defer></script>
  </body>
</html>
```

```html
<link rel="stylesheet" href="./node_modules/@aiursoft/uistack/dist/css/app.css">
<script src="./node_modules/@aiursoft/uistack/dist/js/app.js" defer></script>
```

The npm package contains compiled `dist/` assets. ASP.NET Core components and the demo live in [UIStack](https://github.com/AiursoftWeb/UIStack).

UIStack 2.x no longer bundles Quill or exposes `window.Quill`. Applications that need a rich-text editor must provide one separately.

### Included assets

The bundle includes Bootstrap components, jQuery-based integrations, chart and table helpers, icons, theme controls and UTC timestamp formatting. It is a compiled application stack rather than a set of independently initialized ES modules. Load `app.js` once after the page markup is available; keep the generated asset directory structure intact.

### Related projects

Use the linked ASP.NET Core UIStack project for server-side components and the application demo. This npm repository supplies the shared static assets; it does not itself host an ASP.NET Core application.

## Configuration

The compiled assets are configured through page markup and browser state; there is no package-level configuration file or environment variable for consumers.

**Theme controls**

Set Bootstrap's `data-bs-theme` on the document element for the initial theme. A `.js-theme-toggle` element toggles the document's `data-bs-theme` and `data-sidebar-theme`, persists its choice under `appstack-config-theme`, and refreshes the shared CSS variables. The toggle uses `dark` and `default`; an optional `data-when-changed-post` URL receives JSON `{ "theme": "dark" }` or `{ "theme": "light" }`. The host application is responsible for that endpoint and its authorization/CSRF requirements.

**Components and time formatting**

Bootstrap popovers and tooltips use `data-bs-toggle`; the bundle exposes `window.bootstrap`. Elements with `data-utc-time` receive full localized timestamps and Bootstrap tooltips, including newly inserted or changed timestamp elements. Exposed `window.cssVariables` values are read from the active CSS custom properties. Other bundled plugins retain their own markup and initialization contracts.

**Building a customized bundle**

The entry point is [src/js/app.js](src/js/app.js); theme and layout styles are in [src/scss/app.scss](src/scss/app.scss). [webpack.config.js](webpack.config.js) defines generated resources. `NODE_ENV=production` enables the production build; the existing build command sets it automatically. Changing these sources requires rebuilding the package rather than setting runtime consumer options.

## Development

Install a supported Node.js release compatible with the locked build dependencies. The current build is verified with Node.js 24.

From the repository root, install the locked dependencies, run the existing checks and create a package:

```bash
npm ci
npm run check
npm pack
```

The existing checks run the production Webpack build. `npm pack` creates a local archive; it does not publish a release.

## How to contribute

There are many ways to contribute to the project: logging bugs, submitting pull requests, reporting issues, and creating suggestions.

Even if you have push rights on the repository, you should create a personal fork and create feature branches there when you need them. This keeps the main repository clean and your workflow cruft out of sight.

We're also interested in your feedback on the future of this project. You can submit a suggestion or feature request through the issue tracker. To make this process more effective, we're asking that these include more information to help define them more clearly.

## License

Licensed under the [MIT License](LICENSE).

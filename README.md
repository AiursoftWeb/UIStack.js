# UIStack.js

[![Pipeline](https://badge-proxy.aiursoft.com/aiursoft/UIStack.js/badges/master/pipeline.svg)](https://gitlab.aiursoft.com/aiursoft/UIStack.js/-/pipelines) [![npm](https://img.shields.io/npm/v/@aiursoft/uistack)](https://www.npmjs.com/package/@aiursoft/uistack)

Shared styles, scripts, fonts and images for Aiursoft applications.

## Install

```bash
npm install @aiursoft/uistack
```

## Usage

```html
<link rel="stylesheet" href="./node_modules/@aiursoft/uistack/dist/css/app.css">
<script src="./node_modules/@aiursoft/uistack/dist/js/app.js" defer></script>
```

The npm package contains compiled `dist/` assets. ASP.NET Core components and the demo live in [UIStack](https://gitlab.aiursoft.com/aiursoft/uistack).

## Development

```bash
npm ci
npm run check
npm pack
```

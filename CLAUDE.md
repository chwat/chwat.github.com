# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a static HTML/CSS/JS site template (no backend, no build tool configured). Files are served directly — there is no compilation or bundling step wired up.

## Asset pipeline

- **LESS → CSS**: `less/base.less` is the entry point; it imports `less/bootstrap.less` (a tweaked Bootstrap v1.1 / Preboot.less fork). Compiled output goes to `css/base.min.css`. No LESS compiler is configured in this repo — run `lessc less/base.less css/base.min.css` manually if you have `lessc` installed.
- **JS**: `js/base.js` is the unminified site init source. `js/base.min.js` is the production bundle (jQuery + plugins + site code concatenated and minified). Update the bundle manually if you change `base.js`.

## Architecture

- **`templates/base.html`** — the single HTML template. Loads `css/base.css` (not the `.min` variant, so rename or adjust the link as needed), then defers all JS to the bottom via `js/base.min.js`.
- **`less/bootstrap.less`** — variables, mixins, grid, and CSS3 helpers. Variables like `@c_grey`, `@baseline`, and `@gridColumns` are defined here and consumed in `base.less`.
- **`js/base.js`** — uses a `window.SITE` namespace; `SITE.init` runs on DOM ready.
- **Grid**: 12 columns × 60 px + 20 px gutters = 960 px total. Use `div.grid > div.span{N}` markup.
- **Analytics placeholders**: `UA-XXXXX-X` (Google Analytics) and ClickTale ID `2975` in `base.html` must be replaced before deploying.

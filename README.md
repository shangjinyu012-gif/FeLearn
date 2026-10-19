# FeLearn

English | [简体中文](README.zh-CN.md)

Learn the fundamentals of front-end development in one week, then connect a back end and build full-stack apps.

`index.html` is the whole learning site in a single file. Open it directly in a browser:

- **Mind-map home page** (`#home`): a front-end/full-stack mind map, a one-week learning path, and entry points to every module.
- **Modules**: each module is a `<section class="view v-<id>" data-view="<id>">` in the page, opened with the URL hash `#<id>`. Current modules:
  - `#tools` VS Code development environment (before you start: install Node, Git and VS Code; shortcuts, extensions, debugging)
  - `#html5` HTML5 essentials (the old `html5/index.html` has been merged in here)
  - `#css` CSS styling and layout
  - `#js` JavaScript core
  - `#net` Browser and networking
  - `#fw` Front-end framework: React
  - `#eng` Engineering and tooling
  - `#be` Back end and full stack

## Adding a module

1. In the `MODULES` list in the script at the end of the page, set the module's `ready` to `true` (add an entry if it doesn't exist). The home-page card, the top navigation and the "Open module" button on the mind map then appear automatically.
2. Copy a `<section class="view lesson v-<id>" data-view="<id>" hidden>` and write the content. `.lesson` provides the shared lesson styles (chapters, callouts, tables, editors, quizzes, table of contents); styles that belong only to this module start with `.v-<id>`.
3. Wrap the module's script in `(function(){ ... })();` and use the shared `FL` helpers:
   - `FL.makeEditor`: a runnable editor. `data-mode` picks how it runs: `html` (default), `css`, `js` (with a console; click "Run" to execute), `react` (React 18 + JSX), plus `express` (a mini Express with a request panel) and `sql` (an alasql practice database) registered by the back-end module. Put extra HTML or preset requests in a `<template>`, add `data-resize` for a preview-width slider, and `data-store` to save the code in localStorage.
   - `FL.addMode(name, { hl, label, manual, build(code, tpl) })`: registers a new run mode.
   - `FL.runTests(code, testExpressions, { prelude, html, timeout })`: runs the code in a hidden sandboxed iframe, evaluates each expression and returns an array of booleans. Every challenge's auto-grading uses it.
   - `FL.makeReader`, `FL.makeQuiz`, `FL.tocSpy`.
   - External libraries (React, Babel, alasql) are loaded only from the cdn.jsdelivr.net URLs in `FL.CDN`, with pinned versions.
4. Element ids inside a module must not clash with other modules: a URL like `#some-id` automatically switches to the module containing that id and scrolls to it.

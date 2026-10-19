# FeLearn

一周学习前端基础，再接上后端做全栈开发。

`index.html` 是整个学习站，一个文件、浏览器直接打开即可：

- **脑图首页**（`#home`）：前端全栈脑图、一周学习路径、知识模块入口。
- **知识模块**：每个模块是页面里的一个 `<section class="view v-模块id" data-view="模块id">`，用网址 `#模块id` 打开。目前有：
  - `#html5` HTML5 核心速通（原来的 `html5/index.html` 已并入这里）
  - `#css` CSS 样式与布局
  - `#js` JavaScript 核心
  - `#net` 浏览器与网络
  - `#fw` 前端框架 React
  - `#eng` 工程化
  - `#be` 后端与全栈

## 新增一个模块

1. 在页尾脚本的 `MODULES` 里，把对应条目的 `ready` 改成 `true`（没有就加一条）。首页卡片、顶部导航、脑图上的“进入模块”按钮会自动出现。
2. 复制一个 `<section class="view lesson v-模块id" data-view="模块id" hidden>` 写内容。`.lesson` 提供共用的课程样式（章节、提示框、表格、编辑器、测验、目录）；只属于这个模块的样式以 `.v-模块id` 开头。
3. 模块脚本包在 `(function(){ ... })();` 里，用共用组件 `FL`：
   - `FL.makeEditor`：可运行的编辑器，`data-mode` 选运行方式：`html`（默认）、`css`、`js`（带控制台，点“运行”执行）、`react`（React 18 + JSX），以及后端模块注册的 `express`（迷你 Express + 请求面板）和 `sql`（alasql 练习库）。`<template>` 里放额外的 HTML 或预设请求，`data-resize` 加预览宽度滑块，`data-store` 把代码存进 localStorage。
   - `FL.addMode(名字, { hl, label, manual, build(code, tpl) })`：注册新的运行方式。
   - `FL.runTests(code, 测试表达式数组, { prelude, html, timeout })`：在隐藏的沙箱 iframe 里运行代码并逐条求值，返回布尔数组，挑战题的自动判题都用它。
   - `FL.makeReader`、`FL.makeQuiz`、`FL.tocSpy`。
   - 外部库只从 `FL.CDN` 里的 cdn.jsdelivr.net 地址加载（React、Babel、alasql），并固定版本号。
4. 模块里的元素 id 不要和其他模块重复：网址 `#某个id` 会自动切到该 id 所在的模块并滚动过去。

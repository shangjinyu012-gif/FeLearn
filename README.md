# FeLearn

一周学习前端基础，再接上后端做全栈开发。

`index.html` 是整个学习站，一个文件、浏览器直接打开即可：

- **脑图首页**（`#home`）：前端全栈脑图、一周学习路径、知识模块入口。
- **知识模块**：每个模块是页面里的一个 `<section class="view v-模块id" data-view="模块id">`，用网址 `#模块id` 打开。目前有：
  - `#html5` HTML5 核心速通（原来的 `html5/index.html` 已并入这里）
  - `#css` CSS 样式与布局

## 新增一个模块

1. 在页尾脚本的 `MODULES` 里，把对应条目的 `ready` 改成 `true`（没有就加一条）。首页卡片、顶部导航、脑图上的“进入模块”按钮会自动出现。
2. 复制一个 `<section class="view lesson v-模块id" data-view="模块id" hidden>` 写内容。`.lesson` 提供共用的课程样式（章节、提示框、表格、编辑器、测验、目录）；只属于这个模块的样式以 `.v-模块id` 开头。
3. 模块脚本包在 `(function(){ ... })();` 里，用共用组件 `FL`：`FL.makeEditor`（HTML 或 `data-mode="css"` 的 CSS 编辑器，`data-resize` 加预览宽度滑块）、`FL.makeReader`、`FL.makeQuiz`、`FL.tocSpy`。
4. 模块里的元素 id 不要和其他模块重复：网址 `#某个id` 会自动切到该 id 所在的模块并滚动过去。

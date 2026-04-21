# XJTU-thesis-dev

基于 [obster-y/XJTU-thesis](https://github.com/obster-y/XJTU-thesis) 修改的个人使用版西安交通大学学位论文模板仓库。

这份仓库的目标不是继续维护“官方模板”本体，而是提供一份已经在我本机环境中调通、适合继续填写自己论文内容的可用模板。

## 说明

- 本仓库基于原项目 `XJTU-thesis` 二次整理而来。
- 原项目是西安交通大学硕博学位论文 LaTeX 模板的重要来源，本仓库仅用于个人学习、写作和环境适配。
- 学校在 2025 年发布了新的论文模板要求，本仓库未对那一版要求进行全面重新适配；正式提交前，请务必自行核对学校最新规范。

## 当前环境

- OS: Windows
- TeX 发行版: TeX Live 2026
- 编辑器: VS Code + LaTeX Workshop
- 推荐编译方式: `latexmk`
- 引擎: `XeLaTeX`

## 这份仓库相对原模板做过的适配

### 1. 字体适配

为解决 Windows + TeX Live 2026 环境下 `STKaiti` 无法直接按字体名识别的问题，这份仓库已改为直接加载本机字体文件：

`C:/Users/Hello/AppData/Local/Microsoft/Windows/Fonts/STKaiti.ttf`

已同步修改：

- `XJTU-thesis.cls`
- `beamerfontthemexjtubeamer.sty`

### 2. 新版宏包兼容

为了兼容 TeX Live 2026 中较新的宏包版本，做了以下调整：

- 去掉 `xcolor` 中已经过时的 `usenames` 选项
- 调整 `mathtools` 与 `unicode-math` 的加载顺序
- 修复旧版 `tabularray` 示例语法
- 将旧数学写法 `\over` 改为 `\frac`

### 3. VS Code 编译配置

已将 `.vscode/settings.json` 调整为更适合本模板的配置：

- 默认输出目录为 `Build/`
- 默认 recipe 优先使用 `LaTeXmk`
- 适合右上角“构建 LaTeX 项目”直接编译

### 4. 示例内容的轻量清理

为减少日志中的无关警告，对少量示例文本做了缩短或排版调整，例如：

- `Main_Miscellaneous/abstract_chs.tex`
- `Main_Miscellaneous/abstract_eng.tex`
- `Main_Spine/c2.tex`

这些修改只影响样例内容，不影响论文整体版式结构。

## 已验证

当前仓库已经验证以下文件可正常编译并生成 PDF：

- `main.tex`
- `main_beamer.tex`

生成结果位于：

- `Build/main.pdf`
- `Build/main_beamer.pdf`

## 如何开始写自己的论文

新手建议按下面顺序使用：

### 第一步：先改基本信息

先编辑 `main.tex`，把以下内容替换成你自己的：

- `\title`
- `\degree`
- `\author`
- `\advisor`
- `\subject`
- 答辩日期、地点、委员会信息

### 第二步：改摘要

编辑：

- `Main_Miscellaneous/abstract_chs.tex`
- `Main_Miscellaneous/abstract_eng.tex`

### 第三步：改正文

正文章节默认放在：

- `Main_Spine/c1.tex`
- `Main_Spine/c2.tex`
- `Main_Spine/c3.tex`
- `Main_Spine/c4.tex`
- `Main_Spine/c5.tex`
- `Main_Spine/c6.tex`

如果你实际论文章节数不同，可以在 `main.tex` 中自行增删 `\include{...}`。

### 第四步：改参考文献

参考文献数据库默认在：

- `References/reference.bib`
- `References/achievement.bib`

### 第五步：编译

推荐方式：

1. 打开本仓库根目录
2. 打开 `main.tex`
3. 在 VS Code 中点击右上角“构建 LaTeX 项目”
4. 或选择 recipe: `LaTeXmk`

## 常见提醒

- `输出` 面板里看到 `LaTeX Compiler` / `LaTeX Workshop` 是日志通道，不是编译器切换本体。
- `Nothing to do` 表示“已经编译成功且文件是最新的”，不是报错。
- `Problems` 面板里很多是 warning，不一定是真正的编译失败。
- 真正需要优先关注的报错通常是：
  - `LaTeX Error`
  - `Package ... Error`
  - `Undefined control sequence`
  - `Emergency stop`

## 目前仍可能看到的警告

当前模板在 TeX Live 2026 下仍可能出现少量警告，例如：

- `Underfull \hbox`
- `Overfull \hbox`
- `Overfull \vbox`
- `xdvipdfmx:warning`

这些大多来自样例内容、超链接锚点或页面紧凑度，不会阻止 PDF 生成。正式写作时，随着你替换为自己的内容，很多警告会自然减少。

## 推荐阅读顺序

如果你是新手，建议这样看：

1. `README.md`
2. `main.tex`
3. 编译生成的 `Build/main.pdf`
4. 再去逐章修改 `Main_Spine/*.tex`

## 来源与致谢

- 原始项目: [obster-y/XJTU-thesis](https://github.com/obster-y/XJTU-thesis)
- 原项目许可证: [LPPL](https://www.latex-project.org/lppl/)

感谢原作者提供模板基础。本仓库仅在其基础上完成个人环境适配与使用整理。

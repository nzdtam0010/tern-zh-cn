# tern-zh-cn

[Tern](https://stencil.so/tern) 终端的简体中文全面汉化插件（适配 Tern `0.9.34`）。

基于 [maicent/tern-zh-cn](https://github.com/maicent/tern-zh-cn)（MIT License）深度扩展，通过官方插件机制实现设置界面、弹窗菜单与命令面板的全量简体中文化。

## 功能特性

- **设置中心全量汉化（全部 14 个页面）**：
  - 左侧导航栏（`应用 / 系统` 分组、全部 14 个菜单项）及底部配置文件按钮。
  - 通用、智能体、外观、终端、命令视图、数据库、笔记本、Carly 助手、快捷键、Git、插件、会话、主机、高级 14 个页面的标题、分区、设置项、说明文本、分段按钮、操作按钮及空状态提示。
  - 按当前选中页精准作用域隔离（`.pf-nav:has(... .nav-row.on)`），在**设置搜索模式**下自动退让，避免误覆盖搜索结果。
  - 插件页采用首行与末尾行锚定，无论安装多少插件都不会覆盖插件自身名称。
- **全局界面与弹窗汉化**：
  - 命令面板作用域页签（`全部 / 命令 / 文件 / 搜索 / 分支 / 提交 / 会话 / 主机`，使用 `[title^="..."]` 属性选择器，兼容动态页签）及底部快捷键提示（`选择 / 运行 / 随时切换会话 / 关闭`）。
  - 顶部待处理通知弹窗（`待处理事项 / 全部清除 / 暂无待处理事项`）。
  - 左上角账户与主机菜单（`访问 Stencil 账户 / 设置… / 退出登录 / 切换主机…`）。
  - 终端查找栏（`无匹配项`）与标签栏按钮文字（`新建标签页 / 文件`）。
- **160+ 条全量中文命令面板**：
  - 通过 `window.luau` 注册 160+ 个常用内置命令的中文包装，涵盖标签页与窗口、会话、分屏与块、画中画、终端、Carly 助手、数据库与笔记本、文件与笔记、文件面板、外观与布局、远程主机、应用与设置 12 大分组。
  - 按 `Ctrl+Shift+P`（macOS 为 `⌘K`）即可直接用中文关键词搜索并执行。

## 安装方式

### 方式一：命令行一键安装（推荐）

```sh
tern plugin install github.com/nzdtam0010/tern-zh-cn
```

更新已有安装：

```sh
tern plugin install github.com/nzdtam0010/tern-zh-cn --force
```

### 方式二：在 Tern 客户端中安装

1. 打开 **Settings › Plugins**（设置 › 插件）。
2. 在 **Install…** 输入框中填写：
   ```text
   github.com/nzdtam0010/tern-zh-cn
   ```
3. 点击 **Install** 即可自动安装并生效。

## 原理与边界说明

- `window.luau`：调用 `tern.command` 注册中文命令包装，执行时透传对应内置命令（`cx:command(...)`），不改变任何原始行为。
- `zh-cn.css`：利用 `font-size: 0` 隐藏原英文文本并通过 `::before` / `::after` 注入中文；体积约 142 KiB（低于 Tern 256 KiB 的插件样式表限制）。
- **受插件机制限制暂无法翻译的部分**：
  - 输入框 `placeholder`（如 `Search settings`）及鼠标悬停 `title` 工具提示。
  - 运行时动态生成的提示气泡（toast）、错误消息与弹窗正文。
  - 主题名称、Lenses 示例命令及版本号/路径等动态值（刻意保留原样）。

## 致谢与协议

- 初始项目与实现思路源自 [maicent/tern-zh-cn](https://github.com/maicent/tern-zh-cn)。
- 本项目沿用 [MIT License](LICENSE) 开源。

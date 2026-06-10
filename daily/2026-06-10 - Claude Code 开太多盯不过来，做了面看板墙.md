# Claude Code 开太多盯不过来，做了面看板墙

![CC Mission Control 看板](https://raw.githubusercontent.com/bencode/cc-mission-control/3c119bc08798776654ebd9c31033b52cefc4a5c7/docs/screenshot.png)

我主要在 WezTerm 里用 Claude Code，开着开着就是十来个 session 同时跑：按项目分在不同 workspace，每个项目里又是几个 tab。切起来不慢，`Ctrl+Shift+W` 切 workspace，`Ctrl+Shift+{` / `Ctrl+Shift+}` 切 tab。麻烦的是看不到全局——哪个在干活、哪个停下来等我批权限、哪个早就 idle 了，得一个个切过去才知道。于是写了 [cc-mission-control](https://github.com/bencode/cc-mission-control)。

把每个 pane 渲染成一张实时的终端缩略图，按 workspace 分组铺成一面墙。缩略图就是真的终端画面：xterm.js 把 WezTerm 的屏幕 dump 按原样（带颜色）画出来再缩小。顶上一行计数 `working · waiting · idle · shell`，谁是什么状态扫一眼就够。

状态我没自己去检测，是现成的：Claude Code 自己就把它写进了 pane 标题，盲文 spinner（`⠋` 那种）在转就是在干活，`✳` 是 idle。等我批权限的那种（权限弹窗 / plan 确认）从屏幕内容认出来，单独标成 `waiting`，配琥珀色脉冲。四个状态，一个字都不用配。

除了看，还有几处能直接操作：

- **等审批的能直接批**：`waiting` 的 tile 上有 `✓ Approve` / `✗ Esc`，例行的扫一眼标题就点了，拿不准就点开放大看清弹窗再批。
- **点一下跳过去**：点 tile 切到 WezTerm 里对应的 pane。跨 workspace 跳 `wezterm cli activate-pane` 干不了，就挂了个小 Lua bridge 在 GUI 里接管这步。
- **当前在敲的那个**会高亮一圈，回头不迷路。

还很实验性，macOS + WezTerm 上自用。开源在 [github.com/bencode/cc-mission-control](https://github.com/bencode/cc-mission-control)，欢迎来玩。

## 🚀 泰深 v1.4.2 正式发布

引导页新增中英文切换，国际化体验升级。

### 核心功能
- DeepSeek V4 全模型支持（V4-Pro / V4-Flash），前缀缓存命中率 ~99%，长会话成本恒定
- 主动弹窗引导 — 不会写 Prompt 也能用，AI 主动确认需求
- Commander 形态 — AI 自主规划、调度、验证一条龙
- 泰案画布系统 — 六种流式画布（写作/代码/HTML/终端/数据/图片），双向编辑，历史版本追踪
- HTML 高级预览器 + 内置浏览器独立窗口 — 所见即所得，多标签、收藏夹、Chrome 扩展
- 内置截图工具 — 泰深自我截图，配合 Myeyes 全自动识图标注
- 经验封装系统 — skillCreator / tool_creator / skillPatcher，AI 自主创造工具
- 视觉代理 Myeyes — 模型不支持多模态也能"看图"，IM 渠道全面打通
- FlexDog 动态模型引擎 — 对话中随时切换模型
- 多供应商支持（DeepSeek / OpenAI / Mimo 等自由切换），上下文窗口 per-model 细调
- SubAgent 子代理并行调度（v3.1 架构，独立 Skill/Memory/MCP），分身并行处理
- Skill 自定义安装与扩展（agentskills.io 开放标准，group/subgroup 二级分组）
- MCP 服务接入（Streamable HTTP / SSE / stdio），能力随生态生长
- IM 远程接入（飞书 / QQ / 微信），全面支持图片与文件发送
- 四层安全防线 — PathGuard → 沙箱 → 网络守卫 → 门控防重试
- AI 自诊断 — 6 级 × 9 分类日志，AI 自己查错、自己修复
- 定时任务调度器 + 全局会话搜索 + 回收站系统
- macOS 双架构正式支持（x64 + arm64）

### v1.4.2

- 为初始化引导页添加了中英文切换按钮，国际用户首次体验更友好。

> 🇬🇧 Added a language toggle button (Chinese/English) to the onboarding guide — making the first-run experience welcoming for international users.

### v1.4.1

- 修复了内置浏览器崩溃的 bug。
- 修了泰案 HTML 画布偶尔白屏、无法在文件夹内打开的 bug。
- 泰案 HTML 画布新增预览/批注双按钮切换，操作更直观。
- 紧急修复：旧版本升级到 1.4.0 后启动闪退的恶性 bug。问题出在记忆维护模块启动时找不到新表直接原地爆炸。

### v1.4.0

- 重大更新，「流」(Flow) 画布正式上线！这是泰案家族的新成员——一个结构化思维可视化工具。AI 不再只是跟你聊天，它可以在画布上帮你理清关系、对比方案、推导验证、重组结构、头脑风暴、审视成果。
  - 支持六种节点类型：代码块、Mermaid 图表、图片、表格、文件卡片，还有 ECharts 图表节点（散点/折线/面积/雷达/热力/箱线/漏斗/仪表盘/柱状 9 种图表，数据可视化一步到位）。
  - 节点形状可玩性拉满：圆形、菱形、六边形、胶囊形、平行四边形、圆角矩形，想怎么排列就怎么排列。
  - 连线三模式：直线、阶梯、回环，贝塞尔曲率 + 三色箭头 + hover 发光，关系一目了然。
  - 三大交互原语：拖拽布阵、锚点连线、右键批注——你就是导演，AI 负责把脑子里的乱麻织成锦缎。
  - 三种布局引擎：树状、时间线、矩阵，外加入场动画和 Ctrl+E 一键导出 PNG。
- 泰案终端画布全面升级：从 spawn pipe 切换到 node-pty (ConPTY)，SSH 等交互程序现在可以检测到真 TTY 了。新增 tail/wait 捕获模式、终端控制信号注入（Ctrl+C/D/L/Z/\\ 全支持）、粘贴支持。最常用场景，泰深可以利用终端画布实现 SSH 远程连接各类服务器执行任意工作。
- 调整了泰案画布的拖拽加载文件行为，拖文件进画布时不再直接开搞，先弹窗问你是否让 AI 分析，确认了才动手——手滑党的福音。
- 项目编辑弹窗多了个 X 关闭按钮，未保存变更会弹确认，不会默默丢数据。
- Shell 引导新增 bash-PowerShell 命令速查表。
- 添加了一个全局异常崩溃捕获就位。是的，1.3.8 版本的锅我接了。
- 修复了 Provider HTTP 错误（比如 403）被 SDK 吞掉导致 UI 假死的问题。
- 修复了一个可能会引起输入框卡顿的 bug。
- 修复了会话文件卡片错误加载文件夹目录的 bug。

### 安装
- **taishen_setup_1.4.2.exe** — Windows 安装包（推荐）
- **taishen_1.4.2.zip** — 解压即用免安装版
- **taishen_1.4.0_macOS_arm64.dmg** — macOS Apple Silicon (M1-M4) 安装包（v1.4.0）

### 文件校验（SHA256）
| 文件 | SHA256 |
|------|--------|
| taishen_setup_1.4.2.exe | `79E4C19D3B1FCD13C6F90F3CAA75BCC866E4D5DC3D215BA26E50FABEC736DAEB` |
| taishen_1.4.2.zip | `6593774A2C6F6DA13BE115663D1327D3F7F7270899CF91C0AB4C4DFCDF30F4EE` |
| taishen_1.4.0_macOS_arm64.dmg | `9C88BC7FDABB4F7FE6A5FB953E74264781477FA21BE0A95B2E07F3EA636967A7` |

---

📖 深入了解泰深的设计哲学与技术架构，请阅读[白皮书](WHITEPAPER.md)。

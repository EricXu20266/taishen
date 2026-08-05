## 🚀 泰深 v1.4.4 正式发布

MCP 自带 Node 运行时，连接开箱即用。

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

###v1.4.4

- 针对MCP更新，泰深现在内置了node，以后mcp的调用会优先使用内置node，确保mcp调用稳定。
- 内置浏览器换上了标准 Chrome UA，现在是一个真实的浏览器。
- 修复了上下文压缩的一个隐蔽 Bug：虚拟截断后 token 水位统计没对齐，导致连续触发压缩。
- 数据库搜索索引旧定义自愈重建。
- 做了些程序稳定的加固，并且现在程序崩溃后会进行完整性校验。

- MCP updates — Taishen now ships with a built-in Node.js runtime. MCP calls will prioritize the bundled Node, ensuring stable MCP connections.
- The built-in browser now uses the standard Chrome UA — it's now a real browser.
- Fixed a subtle context compaction bug: token watermark stats were misaligned after virtual truncation, causing repeated compaction.
- Database search index now self-heals and rebuilds stale definitions automatically.
- General stability hardening across the app — and integrity verification now runs automatically after a crash.


### v1.4.3

- 新增 Slack IM 接入，支持私聊与群聊 @ 机器人、图片下载、富文本解析、@here/@channel 提及检测，IM 远程控制新增第四种渠道。
- 新增模型级提示词模式开关（promptMode: auto/full/compact），不同模型可各自微调提示词完整度。
- 模型配置「系统提示词完整度」选项添加 hover 解释并中文化，UI 更直观。

- Added Slack IM integration — the fourth remote IM channel, supporting private chats, group @-mentions, image downloads, rich-text parsing, and @here/@channel mention detection. 
- Added a model-level prompt mode switch (promptMode: auto/full/compact) for per-model tuning of prompt verbosity. 
- The "System Prompt Completeness" option in model config now shows hover explanations with localized labels.

### v1.4.2

- 为初始化引导页添加了中英文切换按钮，国际用户首次体验更友好。

> 🇬🇧 Added a language toggle button (Chinese/English) to the onboarding guide — making the first-run experience welcoming for international users.



### 安装
- **taishen_setup_1.4.4.exe** — Windows 安装包（推荐）
- **taishen_1.4.4.zip** — 解压即用免安装版
- **taishen_1.4.4_macOS_arm64.dmg** — macOS Apple Silicon (M1-M4) 安装包

### 文件校验（SHA256）
| 文件 | SHA256 |
|------|--------|
| taishen_setup_1.4.4.exe | `B14B4506D857ABCCB99A07480F5712FC84AE39B058F855D12388D8C8958CC83D` |
| taishen_1.4.4.zip | `73D285C88275201746AD5ED5DFB2F6CF0905F48A27BBCDB74D85D8D0B013BB33` |
| taishen_1.4.4_macOS_arm64.dmg | `FCF1C52CA0042B83D0C8FB4465EDF2E5B9CEB3EFEB760E15C69566B5CABDAEA3` |

---

📖 深入了解泰深的设计哲学与技术架构，请阅读[白皮书](WHITEPAPER.md)。

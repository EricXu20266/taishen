## 🚀 泰深 v1.4.6 正式发布

全局代理与长任务超时修复。

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

###v1.4.6

- 现在网络设置面板内代理是全局代理了，覆盖LLM API连接、MCP、内置浏览器、plugin。
- MCP工具参数现在在系统题词里是结构化传递。
- 为数据查询工具添加了一些额外参数。
- Stream 空闲超时配置上限从 10 分钟上调到 60 分钟，长任务更从容。
- 稍微优化了泰案-A-Stocks 股票画布，打开画布默认加载自选股行情，省去手动推送。
- 修复了长任务被误杀的隐蔽 bug：模型持续流式输出（一直思考/写正文、不调工具）超过 25 分钟会被墙钟硬超时误杀，现在按输出活动自动续期。
- 修复了会话继承的摘要歧义的问题

- The proxy in the network settings panel is now a global proxy, covering LLM API connections, MCP, the built-in browser, and plugins.
- MCP tool parameters are now passed in structured form in the system prompt.
- Added some extra parameters to the data query tools.
- The Stream idle timeout cap was raised from 10 minutes to 60 minutes — long tasks now have more breathing room.
- Slightly optimized the Taishen A-Stocks canvas — it now auto-loads your watchlist quotes on open, no manual push needed.
- Fixed a hidden bug that killed long tasks: when a model kept streaming output (thinking/writing without calling tools) for over 25 minutes, it was killed by a wall-clock hard timeout. It now auto-renews based on output activity.
- Fixed an ambiguity issue with inherited session summaries.

###v1.4.5

- 重大更新，泰案-A-Stocks 股票画布全面上线：
  - 内置行情数据管线，一键获取市场全景、自选股票分时\K线\5档买卖、涨停版等基础行情信息。
  - L1使用腾讯财经、百度、东财等免费源；
  - L2使用用户配置的TDX、东财、富途、同花顺等收费MCP接口（需要用户批准使用）；
  - L3为自定义混合使用，泰深会根据用户需求自主编写模板来获取数据，无需借助外部代码语言环境，内置Node.js直接使用。
  - 鉴于股(jiu)民(cai)们都会有看盘软件，所以股票画布更侧重于股票策略系统的构建。
    - 你现在可以将你的经验或是策略，直接告诉泰深，agent将会在画布上，根据你的自然语言形成条件式策略。
    - 内置条件引擎 + 策略执行器 + 决策时间轴，策略触发自动唤醒 AI 深度分析，整体形成了智能盯盘体系。
    - 可以配置多套策略，泰深会默认会执行混合策略模式，并会结合验证信息，可以将任意成功的策略固化。
    - 总体而言，整套策略系统是泰深经验封装体系在股票画布的呈现，将你的经验以自然语言告诉泰深，形成公式化条件化的可执行策略。
  - AI画线功能：在单股深度页面，泰深可以根据K线/分时图进行五种线型标注（趋势线、水平线、箱体等）。
- 重大更新：现在泰深配置了几个超级好用的内置 MCP 开箱即用。
  - anysearch、firecrawl两大搜索类MCP，其中anysearch支持匿名模式，firecrawl需要你输入 api key。
  - 通达信mcp，经典股票API接口，此MCP需要收费api key，如果需使用需要在通达信注册，并购买额度。
  - codegraph，代码explore mcp，这个我就不多介绍了。
  - chrome-devtools，配合playwright CLI，可以让agent控制浏览器。
  - 以上内置MCP不会挤占用户级别的配置，如果用户自己配置了相同的MCP，以用户侧配置为准。
- 为定时任务添加了会话绑定选项，现在定时任务可以绑定已有会话执行，泰深可以在你指定的会话里定时工作。
- 修复了主页聊天框右键菜单误弹时钟菜单的 bug。
- 做了些小的安全加固。

**Major update — Taishen A-Stocks canvas is now fully live:**
- Built-in market data pipeline — one-click access to market panorama, watchlist intraday/K-line charts, 5-level order book, limit-up board, and other basic market data.
- L1 uses free sources: Tencent Finance, Baidu, Eastmoney, etc.
- L2 uses user-configured paid MCP interfaces (TDX, Eastmoney, Futu, Tonghuashun, etc.) — requires user approval.
- L3 is custom hybrid mode — Taishen autonomously writes data-fetching templates based on your needs, powered by the built-in Node.js runtime, no external code environment required.
- Since every investor already has their own charting software, the stock canvas focuses on **strategy construction**.
  - Tell Taishen your experience or strategies in plain language, and the agent will turn them into conditional strategies right on the canvas.
  - Built-in condition engine + strategy executor + decision timeline — when a strategy triggers, the AI is auto-woken for deep analysis, forming an intelligent monitoring system.
  - Configure multiple strategies; Taishen runs a mixed-strategy mode by default and, combined with verification results, can solidify any successful strategy.
  - In short, the whole system is Taishen's experience-encapsulation framework shown on the stock canvas — your experience in natural language becomes formulaic, conditional, executable strategies.
- AI chart drawing: on the single-stock deep-dive page, Taishen can annotate K-line/intraday charts with five line styles (trendline, horizontal line, box, etc.).

**Major update — Several super-useful built-in MCPs, ready out of the box:**
- anysearch & firecrawl — two search-class MCPs. anysearch supports anonymous mode; firecrawl requires an API key.
- TDX (Tongdaxin) MCP — the classic stock API. This one requires a paid API key; register on Tongdaxin and purchase quota to use it.
- codegraph — code exploration MCP, you know the drill.
- chrome-devtools — pairs with Playwright CLI to let the agent control a browser.
- The built-in MCPs never conflict with user-level configuration — if you configure the same MCP yourself, your side takes precedence.

- Scheduled tasks now support session binding — tasks can execute in an existing session, so Taishen can work on a schedule in the session you specify.
- Fixed a bug where the right-click context menu on the home page chat input mistakenly popped up the clock menu.
- Minor security hardening.

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
- **taishen_setup_1.4.6.exe** — Windows 安装包（推荐）
- **taishen_1.4.6.zip** — 解压即用免安装版
- **taishen_1.4.6_macOS_arm64.dmg** — macOS Apple Silicon (M1-M4) 安装包

### 文件校验（SHA256）
| 文件 | SHA256 |
|------|--------|
| taishen_setup_1.4.6.exe | `BCE55C4ED10F7B4FFF634B7201F2632C70FD4B5B15D5A851DFCB0D21781AC423` |
| taishen_1.4.6.zip | `D06B8623D09FDCDB795CD930FCF8DD85C01E1646D3ADB12448A21BE2B36A3178` |
| taishen_1.4.6_macOS_arm64.dmg | `2CDC9796DDF1FEB0B6C871A5921FFF1785CD23C93D9CBB5D374C19DE9A33FEB0` |

---

📖 深入了解泰深的设计哲学与技术架构，请阅读[白皮书](WHITEPAPER.md)。

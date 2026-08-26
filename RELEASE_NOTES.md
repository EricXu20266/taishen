## 🚀 泰深 v1.6.0 正式发布

提示词瘦身，MCP 按需加载，外部 Agent 会话导入上线。

### 核心功能
- DeepSeek V4 全模型支持（V4-Pro / V4-Flash），前缀缓存命中率 ~99% + 系统提示词瘦身，长会话成本恒定
- 主动弹窗引导 — 不会写 Prompt 也能用，AI 主动确认需求
- Commander 形态 — AI 自主规划、调度、验证一条龙
- 泰案画布系统 — 八种流式画布（写作/代码/HTML/终端/数据/图片/A-Stocks/Flow），双向编辑，历史版本追踪
- HTML 高级预览器 + 内置浏览器独立窗口 — 所见即所得，多标签、收藏夹、Chrome 扩展
- 内置截图工具 — 泰深自我截图，配合 Myeyes 全自动识图标注
- 经验封装系统 — skillCreator / tool_creator / skillPatcher，AI 自主创造工具；pilot 转正机制闭环，好习惯固化
- 他化自在法（DSH 插件迁移）— 其他工具积累的插件能力整体平移进泰深，无需重写
- 视觉代理 Myeyes — 模型不支持多模态也能"看图"，IM 渠道全面打通
- FlexDog 动态模型引擎 — 对话中随时切换模型
- 多供应商支持（DeepSeek / OpenAI / Mimo 等自由切换），上下文窗口 per-model 细调
- SubAgent 子代理并行调度（v3.1 架构，独立 Skill/Memory/MCP），分身并行处理
- Skill 自定义安装与扩展（agentskills.io 开放标准，group/subgroup 二级分组）
- MCP 服务接入（Streamable HTTP / SSE / stdio）+ 按需加载，工具说明不挤占提示词空间，会话内自主一键启用，热加载即时生效
- 外部 Agent 会话迁移 — 17+ 种外部 Agent（Claude Code/Cowork、Codex、Cursor、ChatGPT、Gemini、Qoder、Kimi、WorkBuddy、DSH 等）会话读取迁移，继承续聊
- IM 远程接入（飞书 / QQ / 微信 / Slack），全面支持图片与文件发送
- 四层安全防线 — PathGuard → 沙箱 → 网络守卫 → 门控防重试
- AI 自诊断 — 6 级 × 9 分类日志，AI 自己查错、自己修复
- 定时任务调度器 + 全局会话搜索 + 回收站系统
- macOS 双架构正式支持（x64 + arm64）

###v1.6.0

- 重大更新，系统提示词瘦身工程完成：内置功能与工具增加导致提示词膨胀，本次深度瘦身降低 token 消耗。
  - Skill 介绍的 when_to_use 截断，调整 SKILL 隐式激活逻辑弥补隐式调用。
  - MCP 按需加载上线：工具说明不再挤占系统提示词空间，会话内可一键启用，会话级生效不影响全局默认设置。
  - 内置 firecrawl、tdx-finance 两大 MCP 出厂默认禁用（工具说明过大，压缩会影响精度）。
  - MCP 热加载模式：会话内开启关闭，下轮消息直接感知，无需新会话；设计上考虑 DeepSeek 缓存命中，影响最小化。
  - 泰深现在可以自主开启和关闭 MCP（字面意思）。
  - 系统提示词细节调整，异步任务与异常处理有所改观。
- 重大更新，外部 Agent 会话读取与导入系统上线：
  - 新增 import_session 内置工具，支持 17+ 种外部 Agent 会话（Claude Code/Cowork、Codex、Cursor、ChatGPT、Gemini、Qoder、Kimi、WorkBuddy、DSH 等）读取与迁移。
  - 支持按外部会话 ID 或标题关键字搜索定位、会话阅读。
  - 双层设计：先导入外置挂载库（缓冲层），再按需转正到主库（UI 面板可见），避免迁移冲击主库。
- 重大更新，DSH 插件迁移能力（他化自在法）上线：
  - 内置 DSH 插件迁移 Skill，可将其他工具积累的能力平移进泰深。
  - 平移前自动判断是否需要、是否满足条件（不能基于 DSH 封装核心或某些 UI 调整）。
  - 两种模式：简单插件转为用户级工具注册进工具列表；复杂插件以组合包（tools + skill + scripts）注册为泰深插件（参考内置 deepresearch）。
- 数据库读取降噪器（NoisyFilter）：三个内置读取工具默认过滤工具调用噪音，只留对话内容，查历史更清爽。
- 经验封装系统闭环完成：新增 encapsulation_mark_done 工具，使用追踪接入 PostToolUse，pilot 转正机制跑通，好习惯能被固化。
- 浏览器稳定性大幅修复：导航/截图/快照失败返回真实错误信息，禁用 backgroundThrottling 根治截图空图，调整 taishen_screenshot 逻辑。
- 修复 tool_creator 假死根因（buildSync 同步 API 阻塞主进程），创建工具不再卡死。
- 修复用户工具返回 JSON 字符串导致会话崩溃的问题，工具返回对象标准化。
- 后台子代理输出目录改用运行时目录，不再污染项目根目录。
- 安全加固：新增「用户与宿主机安全」确认+预检流程，安装外部程序前先查一遍。
- 一堆零零散散的小修复。

- **Major update — system prompt slimming completed**: as built-in features and tools grew, the prompt began to bloat; this update deep-slims it to cut token consumption.
  - Skill `when_to_use` descriptions truncated; SKILL implicit activation logic adjusted to compensate.
  - MCP on-demand loading is live: tool descriptions no longer occupy prompt space; one-click session-level enable, global defaults untouched.
  - Built-in firecrawl & tdx-finance MCPs disabled by default out of the box (tool descriptions too large to compress without hurting accuracy).
  - MCP hot-reload: toggling takes effect on the very next message, no new session needed; designed around DeepSeek cache hits to minimize impact.
  - Taishen can now enable and disable MCPs autonomously (literally).
  - Fine-grained prompt adjustments — async task handling and error handling improved.
- **Major update — external Agent session import system is live**:
  - New built-in `import_session` tool supports reading and migrating sessions from 17+ external agents (Claude Code/Cowork, Codex, Cursor, ChatGPT, Gemini, Qoder, Kimi, WorkBuddy, DSH, etc.).
  - Locate and read sessions by external session ID or title keyword.
  - Two-layer design: sessions import into a separate mount library (buffer layer), then promote to the main database on demand (visible in the UI) — no stress on the main DB during migration.
- **Major update — DSH plugin migration ("Ability Transfer") is live**:
  - Built-in DSH plugin migration Skill — transfer capabilities accumulated in other tools into Taishen.
  - The transfer evaluates whether a capability is needed and feasible (cannot be based on DSH core packaging or certain UI adjustments).
  - Two modes: simple plugins become user-level tools in the tool list; complex plugins register as Taishen plugin packages (tools + skill + scripts), see built-in deepresearch.
- Database read noise suppressor (NoisyFilter): three built-in read tools filter out tool-call noise by default, leaving only conversation content.
- Experience encapsulation loop completed: new `encapsulation_mark_done` tool, usage tracking wired into PostToolUse, pilot-to-stable promotion live — good habits can finally be solidified.
- Major browser stability fixes: real error messages on navigation/screenshot/snapshot failure; backgroundThrottling disabled to root-cause blank screenshots; taishen_screenshot logic adjusted.
- Fixed the root cause of tool_creator freezes (buildSync synchronous API blocking the main process).
- Fixed a session crash from user tools returning JSON strings; tool returns standardized as objects.
- Background subagent output now goes to the runtime directory instead of polluting the project root.
- Security hardening: "User & Host Security" confirmation + pre-check flow — external programs are vetted before installation.
- A bunch of miscellaneous small fixes.

###v1.4.9

- 峰谷定价时钟支持「周一~周五」生效日，周末全天谷价，匹配deepseek最新价格策略。
- 修复了起始页，右侧卡片坞错误弹出的bug。
- 修复了会话文件面板可能会漏收文件的 bug。

- The peak/valley pricing clock now supports "Monday–Friday" effective days, with valley pricing all weekend — aligned with DeepSeek's latest pricing strategy.
- Fixed a bug where the home page's right-side card dock popped out incorrectly.
- Fixed a bug where the session file panel could miss some files.

###v1.4.8

- 泰深工具调用进化。
- 做了匹配DeepSeek Vision 新模型的系统提示词更新。
- 修复切换设定页、定时任务时，详细会话页聊天框预输入内容丢失的bug。
- 修复 QA 问答卡片偶发丢失：流式没写完先存着，冷启动也能回显。
- 修复 / 命令候选列表混入无关命令的问题。

- Taishen's tool calling has evolved.
- System prompt updated to match the new DeepSeek Vision model.
- Fixed a bug where draft input in the detailed session page was lost when switching to the settings or scheduled-task pages.
- Fixed occasional QA card loss: streaming content is staged until finalized, and cold-start echo now works.
- Fixed unrelated commands leaking into the "/" command candidate list.

###v1.4.7

- 定时任务全面进化：任务可以指定 Provider，不同模型各干各的活；支持工作区挂载、会话轮换、自定义命名，执行全程计费/置顶/标题推送，工具调用和进度卡片实时生效——定时任务从"闷头干活"升级成"全程直播"。
- 修复 Windows 通知中心把泰深显示成 electron.app.Electron。
- 泰案html画布和内置html预览器新增外部编辑冲突检测：文件在外部被改过不再闷声覆盖，先弹确认再处理，批注锚点也会校验是否还指得准。
- 修复了命令执行回显无法正常显示的bug。

- Scheduled tasks have fully evolved: tasks can now specify a Provider, letting different models do their own jobs. Supports workspace mounting, session rotation, and custom naming. Full billing / pin-to-top / title notifications throughout execution, with tool calls and progress cards taking effect in real time — scheduled tasks have upgraded from "working silently in the dark" to "live broadcasting."
- Fixed the issue where Windows Notification Center displayed Taishen as "electron.app.Electron".
- The Tai An HTML canvas and the built-in HTML previewer now detect external edit conflicts: files modified outside the app are no longer silently overwritten — a confirmation prompt appears first, and annotation anchors are validated to make sure they still point to the right place.
- Fixed a bug where command execution echo could not display correctly.

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
- **taishen_setup_1.6.0.exe** — Windows 安装包（推荐）
- **taishen_1.6.0.zip** — 解压即用免安装版
- **taishen_1.6.0_macOS_arm64.dmg** — macOS Apple Silicon (M1-M4) 安装包

### 文件校验（SHA256）
| 文件 | SHA256 |
|------|--------|
| taishen_setup_1.6.0.exe | `798399CB89F47C2CF68D3BF25C13C4608E9AB75C9241CE66CF7A882D8422BE31` |
| taishen_1.6.0.zip | `F398775262CF7D26FB4B4A4B948F4D1591C7A407AA0B02A6A29DC333B08C0A89` |
| taishen_1.6.0_macOS_arm64.dmg | `7BDDE3FC3F2A66AC359495EFB014CA5C45E38A50B887230E4FDF031F68471EF0` |

---

📖 深入了解泰深的设计哲学与技术架构，请阅读[白皮书](WHITEPAPER.md)。

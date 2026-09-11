## 🚀 泰深 v1.6.4 正式发布

PPT 画布正式出道，泰深原生改写 PPT。

### 核心功能
- DeepSeek V4 全模型支持（V4-Pro / V4-Flash / V4-Flash-vision），前缀缓存命中率 ~99% + 系统提示词瘦身，长会话成本恒定
- 主动弹窗引导 — 不会写 Prompt 也能用，AI 主动确认需求
- Commander 形态 — AI 自主规划、调度、验证一条龙
- 泰案画布系统 — 九种流式画布（写作/代码/HTML/终端/数据/图片/调色/Flow/股票），双向编辑，历史版本追踪
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

###v1.6.4

- 重大更新，PPT 画布正式出道——泰深现在能把你的 .pptx 直接打开、看懂、改好、再还给你。注意，这里说的是原生不是截图式的「预览」，是真的逐元素解析：文字、形状、图片、表格、图表、组合、母版主题……都能在画布上还原，改完导出回标准 .pptx，PowerPoint 打开原样可编辑。
  - 打开即全解析：文本样式（字号/字色/字重/行距/段距/项目符号/悬挂缩进）、形状几何与渐变、图片裁剪与阴影、表格真表、原生图表、组合嵌套、深色主题——按官方渲染逐项对齐，连「渐变背景页一旦重写就褪成纯色」这种暗坑都补了。
  - 改起来是所见即所得：拖拽/缩放/旋转元素，双击改文字，表格单元格直接编辑（行列/底色/四向边框/文字样式），图表改数据改配色（系列色/单点色/图例/网格线/数据标签/堆积），右侧面板调外观与文字（行距/段间距/斜体/下划线/删除线/字间距）；撤销链按字节精确比对，拉伸一下也撤得回来。
  - 从零造一页：插入菜单不再只是占位——形状、表格、图表都能插了，插入即可编辑；新建的图表还能导出成 PowerPoint 里可继续改数据的原生图表。
  - 让 AI 看懂你的 PPT：AI 打开 deck 先拿到「版式地图」（有几种版式、各含哪些页、代表页是哪几页）和页级标签（封面/目录/章节/图表页……），不用逐页通读；需要看画面时，一键把代表页渲染成 PNG 交给它对照真实设计（配色/字体/logo 位置），AI 还能自己翻到指定页对着看。
  - 导出更靠谱：缺图不再打断导出（占位 + 降级清单如实告知），导出前先校验源包与媒体完整性，未改动的页面保持原样不动——只重写你真正改过的那几页。
- 拼豆画布从「格子填色」进化成「纸上做作品」——九种材质 + 四种豆形 + 六种入场编排，图纸和成品终于不再长得像一回事了。
  - 豆子有形状：方形 / 圆角 / 圆形 / 平行四边形「斜片」，倾斜度和圆角都能单独调。
  - 豆子有材质（九种）：浮纸、瓷片、原生拼豆（能看到中心孔）、糖衣豆，加上树脂、磨砂玻璃、珐琅、织物、像素积木——统一光源、真实高光与接触阴影，切换材质会自动推荐搭配的形状和动作。
  - 有动效了：斜推 / 逐行 / 随机 / 中心扩散 / 轮廓入内 / 分色成形六种编排，配轻落、翻面、浮浪、微倾、浮雕五种单颗动作，强度三档可调；换色是淡出淡入、删格是退场，改图不再「啪」一下跳变。
  - 导出分两路：「图纸」保留网格/分片/水印用来照着拼，「作品」按材质重绘成成品图可以直接晒；颜色清单点一行就高亮该颜色的所有豆子。
- ChatGPT 订阅额度直接接入——用你的 ChatGPT 订阅来跑泰深，不必再单独烧 API 额度；登录一次、token 自动刷新，接入前有两道风险提示（非官方通道、可能失效），说清楚了再决定。
  - 此项登录使用Codex鉴权，你需要先使用Codex登录验证过
  - 在泰深设置-大模型配置页面，点击codex provider页面，选择登录GPT。
- 调色画布补上「按颜色换色」和「批量调色」：色桶算子能在不碰其他颜色的前提下把红裙换成蓝裙（跨色相 1:1 换色）；批量调色工具一次处理整批图，三种模式（统一调整链 / 逐图自适应校偏 / 按文件名或主色条件分组），输出带前后数值对照的清单。
- 子代理现在跨协议工作：Codex / OpenAI Responses 协议的子代理能正常跑、正确压缩、正确恢复；一批「恢复执行后工具全失效」「并发配额串了会话」「压缩摘要为空」的暗病一并清掉。
- 模型设置更可信：模型偏好按 Provider 记忆（会话级优先、全局兜底，重启不丢）；Provider 图标换成官方图并适配明暗主题；GPT 系支持用量统计与推理强度档位；协议下拉多了 OpenAI Responses 选项。
- 适配了deepseek v4.1 flash，包含内置价格更新，默认视觉能力。
- 长会话更稳：压缩触发改看 token 水位（不再把轮数当唯一闸门），压缩模型恒定跟随当前会话；空响应与上游 HTTP 错误不再被静默吞掉；会话恢复不再重复投递同一条消息。
- 安全与网络加固：会话级授权补上会话维度（堵住跨会话越权窗口）、SSRF 校验补齐 IPv6 字面量写法、代理开启后 LLM 与语音链路都走得通。
- Windows 命令环境：反引号雷区检测 + 引导改写文件执行，node 运行时统一解析——AI 少踩 PowerShell 语法坑，你少看几次莫名其妙的失败。
- 修复一批：代理开启后语音识别恒 400、CSP 缺 blob: 导致音频处理加载失败、代理探测失败导致启动白屏、glob 扫不到文件夹、macOS 左上角红绿灯与按钮重叠、Provider 按钮描边与暗色图标显示、内置模型删不掉、重启后不恢复上次模型……
- 一堆零零散散的小修复。

- Major Update: The PPT canvas officially debuts — Taishen can now open your .pptx directly, understand it, edit it, and hand it back. Note that this is native parsing, not a screenshot-style "preview": text, shapes, pictures, tables, charts, groups and master themes are all parsed element by element and rendered on canvas — and the result exports back to a standard .pptx that PowerPoint opens and edits as usual.
  - Full-fidelity decoding: text styling (size / color / weight / line & paragraph spacing / bullets / hanging indent), shape geometry and gradients, picture cropping and shadows, real tables, native charts, nested groups and dark themes are all aligned to the official rendering — down to fixing traps like "a gradient background fading to a solid color after a page rewrite".
  - WYSIWYG editing: drag / resize / rotate elements, double-click to edit text, edit table cells directly (rows & columns, fill, four-way borders, text style), edit chart data and colors (series colors, per-point colors, legend, gridlines, data labels, stacking), and tune appearance & text from the right panel (line spacing, paragraph spacing, italic, underline, strikethrough, letter spacing). Undo is byte-exact — even after a resize.
  - Build a slide from scratch: the insert menu is no longer a placeholder — shapes, tables and charts can all be inserted and immediately edited; newly created charts even export as native, data-editable PowerPoint charts.
  - Let the AI read your deck: on open, the AI first gets a "layout map" (how many layouts, which slides belong to each, which slides are the representatives) plus per-slide semantic tags (cover / agenda / section / chart …) instead of reading every page; when it needs the visuals, one call renders representative slides to PNG (colors, typeface, logo placement), and it can jump to any slide to inspect it.
  - Reliable export: missing images no longer block the export (placeholder + an honest degradation list); source package and media integrity are checked beforehand; untouched slides stay untouched — only the pages you actually edited get rewritten.
- The Beads canvas evolves from "coloring cells" to "crafting a piece" — nine materials, four bead shapes and six entry choreographies, so a pattern and a finished piece no longer look like the same thing.
  - Shaped beads: square / rounded / circle / parallelogram "paper slivers", with independent tilt and corner radius.
  - Nine materials: paper, porcelain tile, native perler (center hole visible), candy-coat, plus resin, frosted glass, enamel, fabric and pixel-brick — one light source, real highlights and contact shadows; switching material recommends a matching shape and motion.
  - Motion: six choreographies (diagonal sweep / row by row / random / center-out / outline-in / color-formed) with five per-bead actions (drop, flip, wave, tilt, emboss) and three intensity levels; recoloring fades out-in and deletions exit gracefully instead of snapping.
  - Two export flavors: "pattern" keeps the grid / tiles / watermark for actually building it; "artwork" re-renders with materials into a shareable piece — and clicking a row in the color list highlights every bead of that color.
- ChatGPT subscription quota is now supported — drive Taishen with your ChatGPT subscription instead of burning a separate API budget. Sign in once, tokens refresh automatically, and two risk notices appear beforehand (unofficial channel, may break) so you decide with eyes open.
  - This sign-in uses Codex authentication — you need to have signed in with Codex first.
  - In Taishen Settings → Model Configuration, open the Codex provider page and click "Sign in with GPT".
- The Color canvas gains "change a color, keep everything else" plus batch grading: the hue-bucket operator turns a red dress blue without touching other hues (1:1 cross-hue swap); the batch tool processes a whole folder in three modes (one chain for all / per-image auto white balance / rule-based routing by filename or dominant hue), and reports a before/after numeric manifest.
- Subagents now work across protocols: Codex / OpenAI Responses subagents run, compact and resume correctly; a batch of latent issues (tools failing after resume, quota buckets crossing sessions, empty compaction summaries) got cleaned up.
- More trustworthy model settings: model preference is remembered per Provider (session-level first, global fallback — survives a restart); official Provider icons with light/dark adaptation; the GPT family gains usage stats and reasoning-effort levels; OpenAI Responses joins the protocol dropdown.
- DeepSeek v4.1 Flash is now supported — built-in pricing updated and vision enabled by default.
- Long sessions are steadier: compaction is now driven by token level (turn count is no longer the sole gate) and always follows the current session's model; empty responses and upstream HTTP errors are no longer silently swallowed; session resume no longer double-delivers a message.
- Security & network hardening: session-level authorization now carries a session dimension (closing a cross-session privilege window), SSRF checks cover IPv6 literals, and both LLM and voice paths work with a proxy enabled.
- Windows shell: backtick landmine detection + guidance to write a script file instead, unified node runtime resolution — fewer PowerShell syntax traps for the AI, fewer inexplicable failures for you.
- Fixes: voice recognition always returning 400 with a proxy on, CSP missing blob: breaking audio processing, blank screen on startup when proxy probing failed, glob failing to match folders, macOS traffic lights overlapping the buttons, Provider button borders and dark-theme icons, built-in models that could not be deleted, model selection not restored after restart…
- A bunch of miscellaneous small fixes.

###v1.6.3

- 重大更新，调色画布（Color）正式出道——泰深内置的图片调色工具：一个「AI 使用的弱化版 Lightroom」，主要用于图片调色。不给你堆满专业按钮，而是让 AI 直接听懂你的话、动手调色。它本质上是为 AI 使用而设计的工具（AI-First）——AI 是调色师，你是导演。
  - 怎么调（AI-First 概念）：你不用自己拖滑块，两种驱动方式任选——
    - ① 会话内对话：直接说「这张图太灰了不通透」「帮我把天空调蓝、山别动」「脸上发黄救一下」，泰深把话翻译成专业调整链执行；
    - ② 画布批注：在画布上圈选区域（矩形/圆形/梯形/套索）或吸管点色，附一句说明，泰深收到批注即动手。
    - 无论哪种方式，泰深都会先给照片做一次数值「体检」（直方图、通道、白平衡，绝不空口说"看到了"），再按专业顺序——先白平衡、再影调、后色彩——开方调整，边调边告诉你改了什么、为什么。
  - 调什么：人像肤色、山水风光、夜景霓虹、阴天废片都能上手——你说的「通透点 / 太灰 / 偏蓝 / 调肤色」，背后是 21 个专业算子（白平衡 / 影调 / 对比 / 清晰度 / 去雾 / 分区色调等）+ 各场景套路配方 + 「去灰 / 胶片 / 清冷」等风格预设。
  - 区域精修（蒙版级局部调色）：只调天空不动山、只调肤色不动背景？圈个空间选区、或吸管点一下同色区域，AI 挂局部调整链——区外原样保护、自带羽化过渡；框都不想画，AI 还能调用视觉识别能力自动认出画面主体，分区分着调。
  - 交付：一键导出成品图（PNG）；还能导出蒙版分层 PSD——每个调整区域独立成层、自带蒙版，丢进 Photoshop 还能接着精修。
  - 顺手的地方：撤销/重做（含区域级）、选区自由变换手柄（PS 语义）、前后对比视图、实时直方图与刷新；GPU 渲染加速，六千像素宽的航拍大图调整缩放不卡顿。
- 调色画布细节打磨：自定义风格库保存/套用、Lightroom 预设（XMP）一键导入、连续圈选多区域统一调整、批量多图导入分页、区域序号角标（"区域 2 调亮"按号报位）……几十处交互修复，把它从「能用」磨到「顺手」。
- 子代理大升级（攒了一整轮）：后台派活真正异步，不再卡住主对话；任务超 3 分钟自动转后台，随时查进度、继续等或主动叫停；跑偏了能优雅按停，结果落盘不再丢。
- Windows 细节修复：任务栏右键菜单、固定图标、通知气泡不再空图标；开始菜单快捷方式改为按需创建，更少被安全软件误报。
- 安全与稳定性：历史消息里的毒 JSON 不再诱发会话死锁；粘贴附件预览与右键粘贴恢复正常；DeepSeek 内置定价表同步 9 月最新价，成本估算更准。
- 泰案画布家族统一工程收尾：工具栏、图标、面板、快捷键全面对齐，多画布操作手感一致。
- 一堆零零散散的小修复。

- Major Update: The Color Grading canvas officially debuts — Taishen's built-in photo grading tool, best described as an "AI-driven lite Lightroom" for picture color grading. Instead of burying you in pro buttons, it lets the AI understand your words and do the grading for you. It's built AI-First — a tool designed for the AI to use: the AI is the colorist, you're the director.
  - How it works (AI-First concept): no slider-dragging needed. Two ways to drive it —
    - ① Chat in the session: just say "this photo is too gray and dull", "make the sky bluer without touching the mountains", "fix the yellowish skin" — Taishen translates your words into a professional adjustment chain and executes it.
    - ② Annotate on canvas: circle a region (rect / ellipse / trapezoid / lasso) or eyedrop a color, add a note, and Taishen acts on the annotation.
    - Either way, Taishen first runs a numerical "checkup" on the photo (histogram, channels, white balance — it never pretends to "see" things), then follows the pro order — white balance first, then tone, then color — explaining what it changed and why.
  - What it grades: portraits & skin tones, landscapes, neon nights, and overcast "discarded" photos — your plain words like "more clarity", "too gray", "too blue", "fix skin tone" map to 21 pro-grade operators (white balance / tone / contrast / clarity / dehaze / split-toning, etc.) plus scene recipes and presets such as "de-haze", "film" and "cool tone".
  - Region-level (masked) grading: want only the sky bluer or only the skin retouched? Select a spatial region, or eyedrop a color range, and the AI applies a local adjustment chain — everything outside stays protected, with feathered transitions. Don't want to draw at all? The AI can invoke vision recognition to identify the subjects and split regions for you.
  - Delivery: one-click export of the finished image (PNG), plus layered PSD export — each adjustment region becomes its own layer with a mask, ready for further refinement in Photoshop.
  - Nice touches: undo/redo (region-level too), free-transform selection handles (Photoshop semantics), before/after comparison, live histogram and refresh; GPU-accelerated rendering keeps 6000px-wide aerial shots fluid while adjusting and zooming.
- Detail polish on the Color canvas: custom style library save/apply, one-click Lightroom XMP preset import, continuous multi-region selection with batch adjustment, multi-image import across tabs, region number badges ("make region 2 brighter" by number)... dozens of interaction fixes that took it from "usable" to "pleasant".
- Subagent overhaul (a full round of upgrades): background spawns are truly async and no longer block the session; tasks running past 3 minutes auto-convert to background — check progress, keep waiting, or actively stop them anytime; graceful cancellation with reliable result persistence.
- Windows detail fixes: taskbar right-click / pinned icons / notification toasts no longer show blank icons; Start menu shortcuts are now created on demand, reducing false positives from security software.
- Security & stability: poisoned JSON in message history can no longer deadlock the session; paste-attachment preview and right-click paste fixed; the built-in DeepSeek pricing table is synced to the latest September rates for more accurate cost estimates.
- Tai'an canvas family unification wrapped up: toolbars, icons, panels and shortcuts are now consistent across all canvases.
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
- **taishen_setup_1.6.4.exe** — Windows 安装包（推荐）
- **taishen_1.6.4.zip** — 解压即用免安装版
- **taishen_1.6.4_macOS_arm64.dmg** — macOS Apple Silicon (M1-M4) 安装包

### 文件校验（SHA256）
| 文件 | SHA256 |
|------|--------|
| taishen_setup_1.6.4.exe | `A53B04D8C81F2FF8F2180D72DFEFF2887F973BA70AC7C336A62F5903AF7557AF` |
| taishen_1.6.4.zip | `64E05507EBD9EFAA804C1C4D2572E5CC33D777C6B452D1B73563F30E5B3A56C6` |
| taishen_1.6.4_macOS_arm64.dmg | `C5895E074FE28BA5033AF48B1ACDCBEFA18F83B8281DCCB1D88710C5B7FB1FF0` |

---

📖 深入了解泰深的设计哲学与技术架构，请阅读[白皮书](WHITEPAPER.md)。

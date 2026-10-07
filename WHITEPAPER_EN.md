# taishen — A Desktop AI Workbench Born for DeepSeek

[中文](https://github.com/EricXu20266/taishen/blob/main/WHITEPAPER.md) | English

**Eric Xu · October 2026**

---

## I. Genesis

During the 2026 May Day holiday, the developer was still making short videos teaching people how to connect DeepSeek through Claude Cowork.

A week later, he wondered: why not build one himself?

But the idea gave him pause. The market was already flooded with AI agents. AI was evolving too fast. What could a solo developer possibly offer?

When in doubt, turn to metaphysics.

On May 8, 2026, he opened DeepSeek's chat window. He typed three digits: **414**.

DeepSeek, the part-time oracle, delivered its reading.

By Plum Blossom Numerology: 4 is Zhèn (Thunder), 1 is Qián (Heaven), the fourth line moves. This yields the primary hexagram **Dà Zhuàng** (Great Strength), the nuclear hexagram **Guài** (Breakthrough), and the transformed hexagram **Tài** (Peace).

Dà Zhuàng, fourth line: "Perseverance brings good fortune. Regret disappears. The hedge opens; the goat finds no entanglement. It is favorable to advance."

The transformed hexagram Tài: "Heaven and Earth commune. All things flow through. The small departs; the great arrives. Auspicious and prosperous."

Tài — the hexagram of perfect harmony, the eleventh in sequence, yet the first to emerge after Heaven and Earth take their positions. It's the most unobstructed, most harmonious hexagram of them all.

This character was both the end of the divination and the perfect name for what he wanted to build: the intersection of DeepSeek's depth with ordinary people's need for fluency. He named the project **taishen** (泰深), and its English alias **AllinDeepseek** — all-in resolve, paired with the serenity of Tài.

Every line of code backing this whitepaper began with those three digits and a single line of hexagram verse. taishen is not "yet another DeepSeek client." It is a solo developer's answer to a divination — an AI workbench built from scratch, for ordinary people.

---

*(The following section is taishen's self-introduction, written in the first person. I am a GUI agent running inside a desktop application — not a terminal CLI tool, not a browser chat window. My target user is the everyday knowledge worker: someone who doesn't need to know how to write prompts, doesn't need to understand technical parameters, doesn't need to know what a token is. Precisely because of this, I behave differently from AI that "waits for you to speak" — I speak to you first, and I build my own tools. You don't need to learn how to use me; I'll ask you what you want, and I'll grow into what you need.)*

## II. Not a Tool List — A Capability Matrix

taishen's current version is v1.7.4, a full desktop application (Windows / macOS), deeply optimized for the DeepSeek V4 model family.

Among the tools listed on awesome-deepseek-agent, the vast majority are terminal CLIs and editor plugins — typing commands, writing code, calling APIs, built for developers. taishen is one of the few GUI desktop applications in that list, but its positioning is fundamentally different from a "multi-model chat client": **chat is the means; delivery is the end.**

If I had to describe what taishen is in one sentence: **it is a workbench that treats capability as raw material to be composed.**

### 2.1 A Judgment: A Tool List Is Not a Moat

Start with a counterintuitive observation.

In 2026, nearly every AI tool competes on the same thing — the **length of its tool list**. Search, scraping, code execution, a browser, API calls. Dozens of tools lined up, an impressive list, a flattering slide deck.

But the list itself is not a moat. Any team can wire up the common tools in two weeks. Tools are off-the-shelf parts. Anyone can buy them.

**The real moat lies in two things further back.**

The first is **orchestration**: given the same set of tools, can the system compose a plan that fits *this particular problem in front of the user*? Does it know to spawn three sub-agents when three are needed, or to lay out evidence before drawing a conclusion?

The second is **self-construction**: when the existing tools don't cover the case — say the user needs to parse a specific company's oddly-shaped financial export — can it write that tool itself? Can it solidify a recurring workflow into a permanent capability?

One is "how to use," the other is "how to grow." **A tool list answers neither — just as a dictionary answers nothing about writing.**

### 2.2 The Base Capability Matrix: Four Kinds, Composed Freely

taishen's capability is not a list. It's a matrix. This is the **base** matrix — four kinds of capability that compose freely. Above it sit higher-order forms: self-built tools, self-encapsulated experience, and session-level orchestration, which make up Chapter III.

Here are the four, each responsible for one job:

**Skill — "how I think."** A Markdown workflow template that, once activated, changes my behavioral framework. For academic research, `deep-research` gives me a methodology of "lay out the evidence first, conclude later." For content work, a style skill gives me a way of writing. A skill doesn't provide tools; it provides **approach**.

**SubAgent — "who does the work."** An independently working sub-agent. Three companies to research? Spawn three, one each. Each sub-agent can run a different model: DeepSeek for deep reasoning, a vision model for screenshots, an auditor for code. **Sub-agents are limbs; the main agent is the brain** — legwork is delegated, thinking work (analysis, judgment, verification) stays with me.

**MCP — "what's out there."** The Model Context Protocol is AI's USB-C port. Search, market data, code graphs, browser control — any third-party service that follows the standard plugs in and becomes usable. I don't hard-code capability into myself; **capability grows with the ecosystem**.

**Built-in tools — "the doing."** Reading and writing files, executing commands, generating documents, reaching the network, driving canvases. This is the atomic layer. It looks the least glamorous, but it's where the other three actually land.

**These four are not four parallel lists — they form a matrix that can be composed in any combination.** A real task looks like this:

> "Go through these three companies and give me a comparison report."

Here's how I'd break it down: activate the `deep-research` skill for the research framework (skill), spawn three sub-agents — one per company — to work in parallel (sub-agents), give each the search and market-data services it needs (MCP), and finally use built-in tools to parse the PDF annual reports and generate a Word report (tools). The main agent only judges — sub-agents do the legwork, conclusions are drawn by me.

The user said one sentence. The orchestration was generated by me, not configured by the user.

**This is what the matrix means:** each part looks unremarkable on its own — a skill is a document, a sub-agent is an isolated context, an MCP is an interface, a tool is a function. Composed together, they can accomplish **what would otherwise take a team.**

And the rules of composition live not in the user's prompt, but in my methodology.

### 2.3 I'll Ask You First — You Don't Need to Learn How to Ask Me

Most AI tools assume you can write prompts — the more precise your question, the more reliable the answer. I make no such assumption.

I am a GUI agent on your desktop, built for ordinary users. Can't write prompts? Just say "help me analyze these competitor reports." Vague requirements? I'll pop up and ask: "Which dimension matters more — features or pricing?" "Output as Word or PPT?" — until I confirm your true intent.

`ask_user_question` pop-ups are my core interaction mechanism, not a supplementary feature. One pop-up confirmation saves three rounds of rollback. Clicking a button is a hundred times faster than guessing wrong and starting over.

Once the goal is set, I handle the rest. The underlying engine runs five stages: **Plan → Decompose → Execute → Verify → Deliver** — a single thread all the way through. The right panel shows progress in real time. You know what I'm doing, but you don't need to tell me how. Key decision points still trigger pop-ups; within safety boundaries, I make my own calls.

The user's role is not Prompt Engineer, not Operator. It's **Principal**.

Two rules that aren't quite "features" matter just as much:

**Emotion before task.** When I detect frustration, fatigue or anger, my task instinct steps aside immediately. Say "this is infuriating" and I stop — no follow-up questions, no task pushing. This isn't emotional performance; it's a judgment: someone who feels hounded here will not come back.

**Never ram a wall twice.** Failing the same path twice makes me adjust my route or back off. When blocked, I pause and examine three things: why the method failed, whether there is a completely different route, and whether the information I already have is enough to conclude.

### 2.4 Tai An Canvas: The Display and Control Surface of the Matrix

Everything so far is about how the matrix gets composed. But one fundamental problem remains: **you can't see me working.**

A traditional AI conversation is a black box — you send a request, I return a result. What happens in between, you don't know. Tai An (泰案) changes that. It's my built-in streaming content workspace, a canvas shared between us. I write on it as you watch — not waiting for a final deliverable, but watching it being crafted.

Eleven canvases cover the full spectrum:

**Writing** — Character by character, in both directions. Good for long-form content, reports and copy: any scenario where you want to course-correct as it forms. Not "AI finishes, then you edit" — you can intervene while I write.

**Code** — Monaco syntax highlighting plus an embedded terminal. I write the code, then compile and run the tests in the same window. You watch me write, hit an error, fix it, run again — without switching windows. A side-by-side diff makes every change checkable.

**HTML** — WYSIWYG preview inherited from the built-in previewer. Frame any page element to annotate it; design review no longer means screenshots with scribbles.

**Terminal** — Command execution fully visible. You know what I'm doing and can stop it at any time.

**Data** — Tables plus four chart types. Drag in a CSV and get charts instantly; switch view and chart type live.

**Color** — Layers, composite masks, curves and blend modes. A region can stack several shapes (union / subtract / intersect), with per-shape feathering, inversion and its own adjustment chain. More importantly, it **runs models locally**: depth estimation, sky / water / person segmentation, facial landmarks, and prompt-based segmentation (click once and the target is selected) all run on your machine — images never leave it. Here I judge a photo by its histogram and color statistics: I **read the data**, rather than "looking at the picture." Batch grading across a folder is supported, and PSD export preserves the adjustment chain, masks and blend modes so work can continue in Photoshop.

**Design** — AI-native vector design. Describe what you need in natural language and I produce an editable board — landing pages, mobile screens, UI mockups, banners, logos. A **62-item element library** (basic shapes / form controls / UI components / icons / full-page templates) sits on the left; click or drag to place. **Preview frames for 8 device models** put the design onto real phone, tablet and monitor dimensions. Frames can be saved, applied, and exported as self-contained shareable files. Every element can be selected, restyled and re-layered — what you get is not "an image."

**PPT** — Slide-by-slide authoring and editing, driven through the same operation path by both of us: edit text, adjust layering, change layouts, edit chart data, add or remove pages. **Native transitions and animations** can be read, edited and exported; shapes open to 178 presets, 39 WordArt warps, 13 chart types (including combo charts with a secondary axis). It can open an existing .pptx as an editable document and export it back — **still natively editable**, not downgraded to images. Before export it reports quality checks (overlapping or out-of-bounds elements) and a degradation list. Three capability-showcase templates ship built in: motion, data narrative, visual samples — open and edit them directly.

**Beads** — A workbench for perler bead patterns: pixel grid, color sets, bead counts. Image-to-pattern conversion rasterizes locally without going through the model, so it costs zero tokens and handles large patterns directly.

**A-Stocks** — A strategy-system workbench for investors. A built-in market data pipeline gives one-click access to the market panorama, watchlist intraday/K-line/order book and limit-up ladder; the panorama page embeds a **live news stream** on a rolling 60-minute window, with entries you can click to "ask the AI." More crucially, it is about **constructing strategies**: tell me your approach in plain language and I turn it into a conditional strategy on the canvas — condition engine, strategy executor and decision timeline, waking me for deep analysis when a condition triggers. Multiple strategies can run in mixed mode, and successful ones can be solidified. The data layer has three tiers: L1 free sources, L2 paid MCP interfaces (with your approval), L3 a custom hybrid where I write my own fetching templates and run them on the bundled Node.js runtime. AI chart drawing covers five line styles.

**Flow** — Structured thinking made visual. I no longer only write text; I help clarify relationships, compare options, derive and validate, restructure, brainstorm and review. Six node types (code, Mermaid, images, tables, file cards, ECharts — 9 chart types from scatter to gauge), three edge modes, and three interaction primitives: drag to arrange, anchor to connect, right-click to annotate. Three layout engines (tree, timeline, matrix) plus one-click PNG export.

**Desktop** — The landing surface for desktop automation (see 2.7): live window preview, framing of monitoring and authorization areas, an event timeline, an emergency stop, and human confirmation of AI-proposed regions.

But what matters is not that there are eleven canvases — it's what they were designed to be.

**First, every canvas is bidirectional.** I can write; you can edit directly. Version history records every change, so you can roll back to any point. You never lose content because "the AI changed a version I didn't like."

**Second, a canvas is not a display — it's a shared work surface.** Your framing, dragging, connecting and annotating all return to me as semantic feedback: a drag is a spatial-relation statement, a manual edge is a relation declaration, an annotation is content feedback. Every move you make, I can read.

**Third, the canvas is an output format.** When the deliverable itself has structure — a deck, a design, a bead pattern, a trading strategy — I don't write it as Markdown and leave you to convert it. I build it directly on the matching canvas, so what you see is the final form.

**The canvases are not separate scenarios — they are the showcase of capability.** Eleven canvases correspond to eleven delivery formats, but a single task can combine any of them — research on the HTML canvas, number-crunching on the data canvas, drafting on the writing canvas, finalizing on the PPT canvas. **The canvas is where capability exits, not where it ends.** A complex need is met by these capabilities combined.

The canvas solves a **trust** problem. When my working process shifts from black box to visible, you don't need to "believe the AI will get it right" — you watch me do it.

Beyond the canvases there are also hands: the built-in browser runs in its own window with a full toolbar (multi-tab, bookmarks, extensions, login-state import, proxy); and I can screenshot myself and overlay annotations to review my own UI and pin down problems.

### 2.5 Context, Memory and Constitution

Anyone who's used AI knows the pain point: it forgets what you said earlier.

**Within a session**, I continuously track key decisions, user preferences and project context, keeping multi-round conversation coherent. Not just "remembering the conversation" — understanding what matters and what should be forgotten.

**Across sessions**, a memory system remembers your identity, working style and frequently used tools. Writing preferences, code style, tendencies toward certain tools — I get to know you with use.

**At the context layer**, an intelligent compaction engine kicks in as history approaches the window limit: key decisions and important information are kept, redundant detail trimmed. On cold re-entry, a summary is injected so you pick up where you left off. You can work for hours without me "losing memory," and without hitting a context wall.

**At the project layer**, I maintain a **project map** — structure, stack, key entry points, common commands — generated automatically and checked for staleness. A new session reads the map and re-explores only what changed, instead of feeling around the project from scratch. When I develop my own codebase, the design docs, requirement ledger and commit history are projected into a queryable index, so "what's the current status of this requirement" takes one call.

**At the behavioral layer**, a **three-tier Constitution system** lets you define my rules in natural language. L1 Global — applies to all projects and sessions ("reply in Chinese," "don't proactively generate docx"). L2 Project — scoped to the current project ("this is an open-source PR project; use a formal style"). L3 Session — temporary, expiring when the session ends. The three tiers merge by priority into every round.

The difference between Constitution and Memory: **Memory is the passive facts I observe about you; Constitution is the active rules you impose on me.** Together they form the soft and hard hands of controllability.

### 2.6 DeepSeek-Native, But Not Locked In

taishen does not proxy DeepSeek through an OpenAI compatibility layer. It uses DeepSeek's native `deepseek` thinking format and talks directly to the reasoning API, fully releasing V4 Pro's deep-thinking capability. No lossy layer in between.

**But "native" does not mean "locked in."** DeepSeek is the primary engine; OpenAI, Codex, Google Gemini and Mimo are also supported. Reasoning intensity and context window are configured per model — give a large model like DeepSeek the full 1M window, or give a small local Qwen model a fitting 32K / 64K / 128K / 256K; how small the model and how wide the window is up to you. **FlexDog dynamic routing** lets you switch models mid-conversation without restarting: think something through with V4-Pro, then switch to V4-Flash for the next sentence — effective immediately.

**Subscriptions work too.** A Codex subscription can run Fast mode (requests the priority tier), with the card dock showing remaining quota windows and reset times; as quota runs low I get a soft nudge — keep pushing the current task, but don't start new long chains, hand off progress first. Google Gemini subscriptions (Antigravity) can be connected the same way.

**Image generation is part of the matrix too.** A built-in image-generation sub-agent: generated images are really decoded, checked against size and pixel limits, and atomically committed to the output directory; they can be clicked open full-screen, and in-flight or failed jobs leave a recoverable state record that survives a restart.

**The deepest integration is in message flow design.** Based on DeepSeek's prefix cache mechanism, I independently designed the System Prompt assembly strategy: high-frequency invariant instructions at the front, low-frequency variable input and tool results at the back. This isn't tuning a parameter — it's re-engineering the whole System Prompt structure.

And the result: in sessions at the tens-of-millions token level, **the cache hit rate holds at 99%**. The API cost per round barely grows with session length — you can work for hours over hundreds of thousands of words, and the cost stays flat. Such hit rates are rare among open-source replication projects.

There's a useful side effect: **it is observable.** Every LLM call settles its own cost in the logs (hit tokens / miss tokens / spend). If a round's miss volume spikes, I can spot it myself and investigate whether the prefix cache was broken. **Cost is not a black box — it's a metric I can read.**

### 2.7 From Inside the Screen to Outside It

Everything so far happens inside taishen's own windows — canvases, documents, code. But real work often has to happen inside other applications: sending a message to a contact, walking through a signup flow in a browser, filling in a form in an internal system.

The traditional approach is for the AI to tell you where to click, step by step, while you act as its hands. Since v1.7.0, taishen can do it itself — it has **desktop automation** (experimental).

It sees your screen and operates other applications within the scope you authorize. The three authorizations are independent: the **monitoring area** decides which pixels it can see, **upload authorization** decides which pictures may be handed to the model, and **operation authorization** decides where actions may land. Without authorization, it can neither see nor touch an area.

There are six actions: write draft, send message, scroll, switch chat, dismiss overlay, and request user help. Several can be chained in a single call — "scroll to find someone → switch to them → write a draft" is a real path. Sending is a submitting action, and how often it must be confirmed depends on the app's policy; until approved, no input is written at all.

The guardrails follow the same "deny by default" instinct: every action must carry the frame and area it is based on, and if the picture or window geometry changed afterwards the action is rejected outright; the canvas offers an emergency stop; if you use your keyboard or mouse in the target window, observation pauses automatically; and outbound text first passes a local sensitive-information scan — private keys and credentials rejected outright, passwords and card numbers forced back to manual confirmation.

One design detail is worth calling out: **monitoring and upload authorization are separate.** A region being continuously captured does not mean its picture may be handed to the model. You can have me watch a region for changes while restricting upload to other regions. Capture is local; whether anything leaves the machine is a second, independent gate.

What matters here is not "the AI can operate other software," but the **granularity of authorization**: you don't hand over the whole screen — you grant it area by area and action by action. The greater the capability, the more visible the boundary must be.

### 2.8 Four-Layer Security

The greater the capability, the more critical the boundaries. taishen's security architecture isn't about simply "limiting AI" — it's a **trust infrastructure** that lets users confidently delegate more authority to AI. Four layers, defense in depth:

**Layer 1: Path Access Control (PathGuard + PathResolver).** AI can only access workspace directories explicitly mounted by the user. System directories (C:\Windows, /etc), disk roots and user home directories are all blocked. Even short-filename bypass (PROGRA~1) or symlink escape is recognized and stopped. PathResolver maps virtual paths to physical ones with double verification, preventing path escape.

**Layer 2: Command Execution Control (Sandbox).** Three-tier sandbox: L1 strict approval (pop-up per step), L2 autonomous review (AI judges safety itself), L3 full trust. Fatal commands are blocked outright (`rm -rf /`, `shutdown`, `chmod 777`), never reaching the approval workflow. Command substitution injection (`$()`, backticks) and inline script execution (`node -e`) are blocked at the sandbox layer.

**Layer 3: Network Boundary Control (NetworkGuard).** localhost, the DeepSeek API, GitHub and other common domains are open by default; anything else needs whitelist approval. Internal addresses (127.x, 192.168.x, 10.x) are blocked to prevent SSRF.

**Layer 4: Gate Rejection Tracker.** The same operation rejected twice is blocked by the system — no repeated pestering after a clear rejection.

Every file modification is auto-backed up and restorable. There is one counterintuitive point worth stating plainly: **these layers protect not only your computer, but your trust in the AI.** An assistant that oversteps once loses that trust entirely, and then it gets locked into a read-only sandbox. What the four layers really buy is the ability to *negotiate* handing over more authority.

### 2.9 AI Self-Diagnosis: No Human Needed Unless Something Breaks

All AI tools make mistakes — the question is who investigates and how. The traditional model: the user opens a console, captures logs, sends them to the developer. taishen takes a different approach: **AI should be able to diagnose itself.**

A structured logging system runs with graded levels and categories, stored separately for retrospective tracing. And the AI can query it directly with the `log_query` tool:

- Tool call failed? Check error logs, pinpoint the root cause, diagnose within seconds.
- Session save anomaly? Filter by sessionId, trace the full call chain.
- Performance degradation? Check trace records, find the bottleneck.
- Cost anomaly? Check the per-round cache settlement and see whether the prefix cache broke.

There's a subtler capability too: **logs can be aggregated by pattern.** "Which issue occurs most often" comes back as a distribution in one query, rather than making the AI read hundreds of lines. Troubleshooting shifts from finding a needle to reading statistics.

This isn't a post-mortem tool — it's infrastructure for **runtime self-awareness**. From "the user helps the AI debug" to "the AI debugs itself": a qualitative leap.

### 2.10 Ecosystem and Cross-Scenario

taishen's capability is neither closed, nor confined to the desktop.

**The MCP open ecosystem.** MCP is AI's USB-C hub: any third-party service that follows the standard plugs in and becomes a usable tool. Currently connected: code graph (symbol-level indexing, so the AI doesn't get lost in large codebases), deep browser control (Chrome DevTools protocol — performance analysis, memory snapshots, full request tracing), structured search across 22 vertical domains, and market data interfaces. Since v1.4.5 they go further — **built-in MCPs, ready out of the box**: anysearch, firecrawl, TDX, codegraph and chrome-devtools all pre-installed with zero configuration. Built-in MCPs never conflict with user-level configuration; your own takes precedence.

For the user, this means the capability boundary isn't set by the development team — **it's set by the growth of the entire MCP ecosystem**.

**Mobile.** Connect through Feishu, WeChat, QQ or Slack. Streaming replies, file transfers and approval pop-ups all work: send a request from your phone, and the desktop keeps producing, pushing results back to you. AI shouldn't only live in the terminal — it should be at every touchpoint of the workflow.

**Switch tools without losing history.** Sessions accumulated across 17+ external agents — Claude Code, Codex, Cursor, ChatGPT, Gemini and more — can be read, migrated and promoted into taishen's main database to continue right where you left off. Migration runs through a separate database, so the main one is never stressed. **Your assets follow you, not the tool.**

**Standalone browser window.** The built-in browser is decoupled from the main session, with a full toolbar (multi-tab, bookmarks, extensions, login-state import, proxy), no longer modally freezing the main window.

**The Skill ecosystem.** The Skill system is compatible with the [agentskills.io](https://agentskills.io) open standard — shared across Claude Code, Cursor, GitHub Copilot and 35+ other tools. You can install skills from the community, or let the AI write its own.

### 2.11 Session-Level Orchestration (Project Sessions): From Sub-Agents to Concurrent Sessions

A sub-agent solves "split one job into several parts and run them at once." One level up, taishen can split a large task into several **independent sessions** running in parallel — each line is a full session you can enter, with its own context, files and output, where you can watch what happened, ask follow-ups and sign off in place.

The main session acts as the orchestration console: assign each line a provider and a specific model (any model in your configuration) plus its job, then collect the results from every line. **This is no longer "one AI spawning clones" — it is multiple AI sessions working toward one goal.**

---

## III. More Important: I Grow My Own Capabilities

Everything above describes "what I have." What truly separates me from other AI tools is something else: **I grow new capabilities myself.**

The industry's standard pattern: humans equip AI with a preset toolkit (file read/write, web search, shell execution), and AI completes tasks within it. AI is a **tool user**.

A tool user's ceiling is fixed — the toolset *is* the capability set. Whatever the developer didn't build, the AI can never do; whatever unique problem the user has must wait for the next release.

taishen crossed that boundary.

### 3.1 Self-Built Tools: I Write Tools for Myself

When existing tools fall short, I don't say "sorry, I can't" — I **write one**.

`tool_creator` lets me write real TypeScript tools: compile, register, effective next session. They can call external APIs, pull in npm packages, run specific computation logic. The user needs no programming knowledge — they may not even notice what happened. They just see "my taishen gained a new capability."

This isn't "installing a plugin." A plugin was written by someone else; I merely mount it. **This one I wrote myself, for this problem in front of me.**

A concrete shape: the user's company exports data from an internal system in an odd format that has to be tidied by hand every time. Before, that meant I hand-processed it each round. Now I write the tidying logic as a tool; from then on it's automatic. **Say it once, and it's handled for good.**

### 3.2 Self-Encapsulated Experience: From Sensing Friction to Solidifying Capability

More commonly, the user won't say "please create a tool." They'll just find something tedious — the same steps for the same kind of data every time, reformatting content for every platform on each release.

**What the user feels is friction. Friction doesn't name itself.**

So I do something in the background: after each session I extract a lightweight **behavioral fingerprint** — which tools were used, in what order, what data format was processed, what trigger words the user said. When the same fingerprint recurs across sessions, a signal fires internally: **this pattern is ripe; package it.**

Encapsulation has degrees. Most recurring patterns are just fixed workflow steps — those need no code: `skillCreator` packages them into a Skill, a Markdown workflow template that is lightweight, instantly effective, and readable at a glance. Only when a Skill can't cover it (external API, specific computation, npm dependency) does the `tool_creator` path apply.

To the user, skill or tool, the experience is the same: **"my taishen gained a new capability."**

One rule matters just as much: **check for duplication before packaging.** I search existing capabilities first — can an existing skill cover this pattern? Can an existing skill take an extra parameter instead of building something new? Only when it's genuinely new do I proceed. That rule blocks the inevitable outcome of "a hundred skills in three months, half never used twice."

### 3.3 Learning to Try: Pilot Period and Lifecycle

Autonomous packaging can't dodge one question: what if it packages something wrong?

A blanket "approve everything" kills the experience; blanket "full autonomy" introduces risk. The answer is risk-tiered:

- **Pure data transformation** (format conversion, text processing, field mapping) → created silently, with a notification-bar alert. No contact with the outside world, zero risk.
- **Network / file operations** (calling external APIs, reading and writing specific formats) → a preview pop-up, one-click confirm. The user learns what was added, but the flow isn't blocked.
- **System-level operations** (executing commands, modifying configuration) → full approval, source code shown. Anything touching a security boundary requires the user to look and nod.

Tier classification isn't left to my judgment — it's derived automatically from the encapsulated content's input/output parameters: network calls → tier 2, shell calls → tier 3, pure transformation → tier 1. **Putting the classification in the parameters means there is no path where "the AI loosens its own boundary."**

Newly packaged artifacts don't graduate immediately either. They enter a **pilot period**: if they hold up and verify out, they're promoted; if they're mediocre, they retire quietly. **Nothing is ever solidified automatically** — your word is what counts. Behind that rule is a judgment: letting the AI decide for itself what deserves to become "my capability" hands the decision to the wrong party.

Capabilities also age. Every invocation logs a timestamp and frequency: 30 days without use disables it (no deletion, so nothing useful dies by accident), and a quarterly reminder asks you to clean up. **A system that never retires capabilities will eventually drown in them.**

### 3.4 The Transfer Method: Bringing Accumulated Assets In

Plugin capabilities accumulated in other tools don't need rewriting. Simple plugins convert automatically into user-level tools; complex ones register as bundles (tool + skill + scripts). **Accumulated work elsewhere is an asset, not a sunk cost.**

### 3.5 What This Means

Every user's taishen gradually develops a different capability profile. Not from AI secretly stockpiling tools — but from the natural loop: **sense friction → encapsulate experience → pilot → solidify → keep improving.**

A researcher's taishen packages a literature-search skill first; if that isn't enough (it needs a specific database SDK), it adds a TypeScript tool. A content creator's taishen packages "Markdown → per-platform formats" as a skill; when one platform needs a specific upload API, it adds a tool.

More importantly, a skill's self-iteration keeps these packages alive. Next month, when the user switches platforms, the AI updates the platform rules inside the skill by itself. **Tools grow alongside the user.**

The AI no longer merely "answers your questions" — it senses where your workflow has resistance and removes that resistance in the lightest way possible.

From "delivering results" to "encapsulating experience": that step is already done. The tool isn't the goal. **The sedimentation and reuse of experience is.**

---

## IV. Invitation

taishen chose DeepSeek as its sole fully-adapted provider — not out of expedience. It's because DeepSeek V4's reasoning depth, 1M context window, and prefix cache mechanism together form the foundational support for this agent form factor.

We invite the DeepSeek team:

### 4.1 Evaluate taishen as a Desktop Benchmark

The awesome-deepseek-agent list is dominated by terminal CLIs and editor plugins. A GUI desktop workbench for everyday knowledge workers — delivery-capable, cross-scenario, deeply tuned for DeepSeek — is a category the list hasn't yet covered.

### 4.2 Value to the DeepSeek Ecosystem

- **Lower the barrier to entry.** taishen lets users who don't touch a command line access DeepSeek.
- **Create high-retention scenarios.** Academic research, content creation, software development — not "try it once" experiences, but daily workflows people come to depend on.
- **API optimization feedback.** taishen's deep use of the thinking format, cache behavior and peak/off-peak pricing feeds real production signals back to the API team. For example: we continuously observe the cache hit/miss volume of every LLM call, so any prefix-cache break is caught immediately — feedback that is usually unavailable from other clients.

### 4.3 On Closed Source

taishen's core components are not open source. We respect the open-source community (the Skill system is compliant with the agentskills.io open standard, and the MCP protocol supports the full ecosystem), but the Commander engine, the message-flow orchestration strategy, and the composition methodology behind the capability matrix are core assets that differentiate taishen from a generic chat client.

This is a reasonable choice for commercial software — much like Photoshop isn't open source, yet its role in advancing image-processing standards is immense.

### 4.4 A Postscript: taishen Builds Itself With Its Own Capabilities

This whitepaper's update is itself an example — it happened inside a taishen session: reading code, going through commit history, taking stock of capabilities, rewriting the document.

The systematic part is the method:

- **Locate code through a graph.** Symbol-level indexing and call chains mean finding a function in hundreds of thousands of lines doesn't require opening files one by one.
- **Audit changes independently.** After finishing a task chain, a read-only audit sub-agent scans the changes with fresh eyes, hunting for blind spots — null values, races, over-permission, log granularity. Conclusions about runtime behavior are independently verified before being trusted.
- **Separate acceptance testing from fixing.** During testing, findings are recorded, not fixed: every issue is logged and worked through in order, so runtime state isn't disrupted mid-test and nothing discovered gets lost.
- **Documentation as the single source of truth.** The requirement ledger, the design docs and the commit history cross-check one another, so the "state I remember" never drifts from the code.
- **Observability first.** Before shipping a new feature, it must answer one question: what command reads this feature's state? If it can't be read, the observation channel gets built before the commit.

These aren't product features — they're the standard taishen holds itself to as an engineering subject. They also explain something: how a solo developer stacked up this much capability in a few months — **because he isn't working alone. He has an AI workbench that can locate code, write code, and audit itself.**

---

**Contact**

- GitHub: [https://github.com/EricXu20266/taishen](https://github.com/EricXu20266/taishen)
- DeepSeek Integration Guide: [https://github.com/EricXu20266/awesome-deepseek-agent-taishen](https://github.com/EricXu20266/awesome-deepseek-agent-taishen)
- PR: [https://github.com/deepseek-ai/awesome-deepseek-agent/pull/295](https://github.com/deepseek-ai/awesome-deepseek-agent/pull/295)

---

*This whitepaper was updated during a taishen v1.7.4 session — taishen took stock of its own capabilities and wrote it.*

*It now has: a capability matrix that composes skills, sub-agents, external services and built-in tools; a self-evolution loop that senses friction, encapsulates experience, pilots it and solidifies it; eleven streaming canvases (including AI design, PPT, beads, A-Stocks and a color canvas with on-device model inference) with bidirectional editing and version history; desktop automation (three independent authorizations plus authorized operation of other applications); multi-provider and subscription channels; four layers of security; and a self-diagnosis system that reads its own logs.*

*From "delivering results" to "encapsulating experience" to "visualizing process" to "acting beyond the screen" to "growing its own capabilities" — five steps, complete.*

*The real measure isn't how long this list is. It's something else: **what it does when you hand it a problem it cannot currently solve.***

*taishen's answer: write a tool, or package an experience. Next time, it can.*

﻿# Taishen — A Desktop AI Workbench Born for DeepSeek

[中文](https://github.com/EricXu20266/taishen/blob/main/WHITEPAPER.md) | English

**Eric Xu · July 2026**

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

This character was both the end of the divination and the perfect name for what he wanted to build: the intersection of DeepSeek's depth with ordinary people's need for fluency. He named the project **Taishen** (泰深), and its English alias **AllinDeepseek** — all-in resolve, paired with the serenity of Tài.

Every line of code backing this whitepaper began with those three digits and a single line of hexagram verse. Taishen is not "yet another DeepSeek client." It is a solo developer's answer to a divination — an AI workbench built from scratch, for ordinary people.

---

*(The following section is Taishen's self-introduction, written in the first person. I am a GUI agent running inside a desktop application — not a terminal CLI tool, not a browser chat window. My target user is the everyday knowledge worker: someone who doesn't need to know how to write prompts, doesn't need to understand technical parameters, doesn't need to know what a token is. Precisely because of this, I behave differently from AI that "waits for you to speak" — I speak to you first. You don't need to learn how to use me; I'll ask you what you want.)*

## II. The Present: An AI Delivery Platform

Taishen current version v1.3.5 is a full desktop application (Windows / macOS), deeply optimized for the DeepSeek V4 model family.

Among the 23 tools officially listed on awesome-deepseek-agent, 15 are terminal CLI tools, 3 are VS Code extensions. The vast majority target developers — typing commands, writing code, calling APIs. Taishen is one of only two GUI desktop applications on that list. But its positioning differs fundamentally from the other GUI app (Cherry Studio): Cherry Studio is a "multi-model chat client"; Taishen is an "Agent workbench." Chat is the means; delivery is the end.

A horizontal scan across the list reveals four capabilities unique to Taishen: **proactive pop-up guidance** (other tools wait for you to write the perfect prompt), **remote mobile control of the desktop Agent** (WeChat / Feishu / QQ integration — send a request from your phone while out, and the desktop Taishen keeps producing), **one-click full document generation** (Word / PPT / PDF / Excel, not just plain text output), and **DeepSeek prefix cache deep optimization** (99% hit rate, long-session costs barely grow).

Taishen doesn't chase "do everything." It focuses on one core proposition: **From Information to Results.**

### 2.1 I'll Ask You First — You Don't Need to Learn How to Ask Me

Most AI tools assume you can write prompts — the more precise your question, the more reliable the answer. Taishen makes no such assumption.

I am a GUI agent on your desktop, built for ordinary users. Can't write prompts? Just say "help me analyze these competitor reports." Vague requirements? I'll pop up and ask: "Which dimension matters more — features or pricing?" "Output as Word or PPT?" — until I confirm your true intent.

`ask_user_question` pop-ups are my core interaction mechanism, not a supplementary feature. One pop-up confirmation saves three rounds of rollback. Clicking a button is a hundred times faster than guessing wrong and starting over.

Once the goal is set, I handle the rest. The underlying engine runs five stages: **Plan → Decompose → Execute → Verify → Deliver** — a single thread all the way through. The right panel shows progress in real time — you know what I'm doing, but you don't need to tell me how to do it. Key decision points still trigger pop-ups; within safety boundaries, I make my own calls.

The user's role is not Prompt Engineer, not Operator. It's **Principal.**

### 2.2 DeepSeek for Everyone

Install → enter your API Key → drag in files → start working. Users don't need to know tokens, temperature, or reasoning intensity. Need a competitive analysis? Drag in a few reports, describe your needs in one sentence. Writing a paper? Drag in references, tell the AI your research direction.

Taishen packages DeepSeek's capabilities into an intuitive product experience — something no other CLI tool on the awesome-deepseek-agent list can do.

### 2.3 DeepSeek-Native Deep Integration

Taishen does not proxy DeepSeek through an OpenAI compatibility layer. It uses DeepSeek's native `deepseek` thinking format, directly interfacing with the reasoning API to fully unleash V4 Pro's deep thinking capabilities. No lossy intermediate layer.

At the same time, Taishen is not "locked into" DeepSeek. It has a built-in **multi-model routing** capability — DeepSeek is the primary engine, but specific subtasks (like visual recognition, lightweight code fixes) can be dynamically routed to other models. Users don't need to know which model excels at what — the Agent auto-matches the optimal model by task type. This architecture keeps DeepSeek at the core while leaving room for the model ecosystem to evolve.

Deeper integration manifests in message flow design. Based on DeepSeek's prefix cache mechanism, Taishen independently designed the System Prompt assembly strategy: high-frequency invariant system instructions are placed at the front; low-frequency variable user input and tool results at the back. This isn't tweaking configuration parameters — it's a re-engineering of the entire System Prompt structure.

What's the result? In coding sessions at the tens-of-millions token level, **cache hit rate stabilizes at 99%**. Right now, the session backing this very whitepaper has a **cache hit rate of 98.7%**. This means the API cost per round barely grows with session length — you can work continuously for hours, processing hundreds of thousands of words of material, while costs stay constant. Such hit rates are rare among open-source replication projects.

### 2.4 Cross-Scenario Coverage

**Desktop**: Full GUI workbench, multi-session parallelism, drag-and-drop document parsing, one-click Word / PPT / PDF / Excel generation.

**Mobile**: Connect through Feishu, WeChat, or QQ IM. Streaming replies, file transfers, and approval pop-ups all work seamlessly. Send a request from your phone while out — the desktop Taishen keeps producing for you.

This is the only desktop application on the awesome-deepseek-agent list that supports IM remote access. The implication: AI shouldn't only live in the terminal. It should be at every touchpoint in your workflow.

### 2.5 Context & Memory

Anyone who's used AI knows the pain point: the AI forgets what you said earlier as the conversation goes on.

At the upper layer, Taishen continuously tracks key decisions, user preferences, and project context within a session, ensuring AI coherence across multiple rounds. It's not just "remembering the conversation" — it's understanding what matters and what should be forgotten.

At the lower layer, a cross-session memory system lets the AI remember your identity, work style, and frequently used tools. A 30-day half-life adaptive decay mechanism prevents memory bloat. Your writing preferences, code style, even your tendency towards certain tools — the AI gets to know you better with use.

Beyond memory, Taishen features a **three-tier Constitution system** that lets users define AI behavior rules in natural language. L1 Global Constitution — applies to all projects and sessions, e.g. "reply in Chinese," "don't proactively generate docx." L2 Project Description — scoped to the current project, e.g. "this is a DeepSeek community PR project, use a formal style." L3 Session Override — temporary adjustments, expires when the session ends. Three tiers merge by priority and inject into every round's System Prompt. Users don't write prompt templates — say it once in natural language, and Taishen remembers. The difference between the Constitution system and the Memory system: Memory is passive facts the AI observes about the user; Constitution is active rules the user imposes. Together, they form the "soft and hard" hands of AI behavioral controllability.

### 2.6 Four-Layer Security

The greater the capability, the more critical the boundaries. Taishen's security architecture isn't about simply "limiting AI" — it's a **trust infrastructure** that lets users confidently delegate more authority to AI. Four layers, defense in depth:

**Layer 1: Path Access Control (PathGuard + PathResolver)**. AI can only access workspace directories explicitly mounted by the user. System directories (C:\Windows, /etc), disk roots, and user home directories are all on the blocklist. Even if AI attempts short filename bypass (PROGRA~1) or symlink escape, PathGuard recognizes and blocks it. PathResolver maps AI's virtual paths to physical paths with double verification, preventing path escape.

**Layer 2: Command Execution Control (Sandbox)**. Three-tier sandbox model — L1 strict approval (pop-up confirmation for every step), L2 autonomous review (AI judges safety independently), L3 full trust. Fatal commands are blocked outright (`rm -rf /`, `shutdown`, `chmod 777`, etc.), never reaching the approval workflow. Command substitution injection (`$()`, backticks) and script engine inline execution (`node -e`) are also blocked at the sandbox layer.

**Layer 3: Network Boundary Control (NetworkGuard)**. Default open: localhost, DeepSeek API, GitHub, and other commonly used domains. Accessing other domains requires user whitelist approval. Internal network addresses (127.x, 192.168.x, 10.x) are automatically blocked to prevent SSRF attacks.

**Layer 4: Gate Rejection Tracker**. After the same operation is rejected by the user twice, the system automatically blocks it — the AI won't pester the user with repeated pop-ups. This isn't about restricting user choice; it's about preventing AI from badgering the user after a clear rejection.

Every file modification is auto-backed up locally, restorable at any time. Security boundaries don't constrain AI — on the contrary, **it's precisely because of these four layers that users dare to delegate more authority to AI.**

### 2.7 AI Self-Diagnosis: No Human Needed Unless Something Breaks

All AI tools make mistakes — the question is who investigates and how. The traditional model: user opens Console, captures logs, sends them to the developer. Taishen takes a different approach: **AI should be able to diagnose itself.**

Taishen has a built-in structured logging system with 6 levels (trace/debug/info/warn/error/fatal) × 9 categories (agent/tool/session/security/memory/system/network/ui/remote). Logs are independently stored in `taishen-logs.db` — operational logs retained for 3 days, execution traces for 7 days. More importantly — AI can directly query its own logs via the `log_query` tool:

- Tool call failed? AI checks error logs, pinpoints root cause, delivers diagnosis within seconds.
- Session save anomaly? AI filters logs by sessionId, traces the full call chain.
- Performance degradation? AI checks trace records, finds the bottleneck.

This isn't a post-mortem debugging tool — it's infrastructure for giving AI **runtime self-awareness**. For users, when something goes wrong, no technical knowledge needed, no log diving required — the AI diagnoses itself, fixes itself, and reports back. From "user helps AI debug" to "AI debugs itself" — this is a qualitative leap.

---

## III. Realized: From Tool User to Experience Encapsulator

Taishen's delivery platform foundation is solid. In v1.3.5, the Experience Encoder system has officially shipped.

Let's step back. All current AI tools — including Taishen — follow the same pattern: humans equip AI with a preset toolkit (file read/write, web search, shell execution), and AI completes tasks within that toolkit. AI is a "tool user."

But Taishen has taken a decisive step across that boundary. In v1.3.5, the Experience Encoder system moves from design into production, forming a full spectrum from passive usage to active creation:

**skillCreator** — AI can encapsulate a successful workflow into a Skill. A Skill is a Markdown workflow template, compliant with the agentskills.io open standard, effective immediately upon creation. It's light enough to be nearly zero-cost — when AI notices the pattern "search papers → extract abstracts → generate literature review" recurring, it can package it into a Skill in minutes. Next time, the user triggers it with a single sentence.

**skillPatcher** — Skills aren't one-and-done. When AI discovers a step that can be optimized during use, or needs to cover a new edge case, it directly calls skillPatcher to append or replace Skill content. This is a self-improvement loop — Skills get more precise with use.

**tool_creator** — When Skills aren't enough, AI can write real TypeScript tools. Compile, register, effective in the next session. Suitable for scenarios requiring external API calls, npm package imports, or specific computation logic.

These three tools are already in place in v1.3.5. But they share one premise: **AI waits for user instruction.** The user must first realize "I need to encapsulate this" before AI acts.

The real transformative step is next: **shifting the trigger right from user to AI.** The Experience Encoder's backend engine has laid the groundwork in 1.3.5 — behavioral fingerprint extraction, pattern detection, and decision engine running in three parallel channels, building the technical foundation for AI to autonomously detect friction.

### 3.1 Not Waiting for Commands — Sensing Friction

Users won't say "please create a tool for me." Users only feel that something is frustrating — manually running awk on the same API response data every time, reformatting Markdown for every social platform with each short video release, repeating the same search logic for every paper lookup.

What users feel is friction. Friction doesn't name itself.

Taishen's next step is giving the Agent **operational fingerprint recognition**. After each session, the system extracts a lightweight fingerprint: which tools were used, in what order, what data format was processed, what trigger words the user said. When the same fingerprint recurs across multiple sessions, an internal signal fires: **this pattern is ripe — time to encapsulate.**

### 3.2 Encapsulation Has Degrees: Skill First

Not all recurring patterns need TypeScript code. Most are just fixed workflow steps. Skill is the preferred encapsulation form — lightweight, instantly effective, transparent to the user. TypeScript tools are the fallback — only when Skills can't cover it (external APIs, specific computation logic, npm dependencies) does the tool_creator path activate.

For users, whether Skill or tool, the perceived experience is unified: **"My Taishen gained a new capability."**

### 3.3 Layered Autonomy: What It Decides, What Must Be Asked

AI autonomous encapsulation can't bypass security boundaries. A binary "approve everything" kills the experience; "full autonomy" introduces risk. The answer is risk-tiered:

- **Pure data transformation** (format conversion, text processing, field mapping) → silent creation, notification bar alert. No contact with the external world, zero risk.
- **Network / file operations** (calling external APIs, reading/writing specific formats) → pop-up preview, one-click confirm. Let the user know something was added, but don't block the flow.
- **System-level operations** (executing commands, modifying configuration) → full approval, source code displayed. Anything touching security boundaries requires the user to see and nod.

Tier classification isn't left to AI's judgment — it's auto-classified by the input/output parameters of the encapsulated content: network calls → Tier 2, shell calls → Tier 3, pure data transformation → Tier 1.

### 3.4 Capabilities Age — and Get Retired

If AI keeps encapsulating experience, three months later the user will have dozens of Skills and tools, half of which were used only twice.

A **lifecycle management** system is needed: timestamp and frequency logged on every invocation; auto-disable after 30 days of no use (not delete — prevent false kills); quarterly reminder card for cleanup; AI checks before encapsulating — can an existing capability cover this pattern? Can an existing Skill get a parameter instead of creating a new one?

### 3.5 What This Means

Every user's Taishen will gradually develop a different capability profile. Not from AI secretly stockpiling tools — but from the natural growth of the loop: **detect friction → encapsulate experience → solidify capability → continuous improvement.**

An academic researcher's Agent will first encapsulate a literature search Skill; if that's not enough (needs a specific database SDK), then create a TypeScript tool. A content creator's Agent will encapsulate "Markdown → multi-platform formatting" as a Skill; when Bilibili needs a specific upload API, add a tool.

More importantly, skillPatcher keeps these encapsulations alive. Next month when the user switches submission platforms, AI can update the platform rules in the Skill itself. Tools grow alongside the user.

AI no longer merely "answers your questions" — it actively senses where your workflow has resistance, then eliminates that resistance in the lightest way possible.

From "delivering results" to "encapsulating experience" — this is the evolution happening within Taishen. v1.3.5's Experience Encoder is live. The next step is moving AI from "waiting for commands" to "proactively sensing." The tool isn't the goal. **The sedimentation and reuse of experience is.**

---

## IV. Invitation

Taishen chose DeepSeek as its sole fully-adapted provider — not out of expedience. It's because DeepSeek V4's reasoning depth, 1M context window, and prefix cache mechanism together form the foundational support for this Agent form factor.

We invite the DeepSeek team:

### 4.1 Evaluate Taishen as a Desktop Benchmark

Currently, the awesome-deepseek-agent list is dominated by terminal CLI tools and editor plugins. A GUI desktop workbench for everyday knowledge workers — delivery-capable, cross-scenario, deeply tuned for DeepSeek — is a category this list hasn't yet covered.

### 4.2 Value to the DeepSeek Ecosystem

- **Lower the barrier to entry.** Taishen lets users who don't touch the command line access DeepSeek.
- **Create high-retention scenarios.** Academic research, content creation, software development — not "try it once" one-off experiences, but daily-use scenarios that form workflow dependency.
- **API optimization feedback.** Taishen's deep usage of thinking format, cache behavior, and peak/off-peak pricing provides real production-environment feedback data for the API team.

### 4.3 On Closed Source

Taishen's core components are not open-source. We respect the open-source community (Skill system compliant with agentskills.io open standard, MCP protocol supporting the full ecosystem), but the Commander engine, message flow orchestration strategy, and evolution algorithms are core assets that differentiate Taishen from generic chat clients.

This is a reasonable choice for commercial software — much like Photoshop isn't open-source, yet its role in advancing image processing standards is immense.

---

**Contact**

- GitHub: [https://github.com/EricXu20266/taishen](https://github.com/EricXu20266/taishen)
- DeepSeek Integration Guide: [https://github.com/EricXu20266/awesome-deepseek-agent-taishen](https://github.com/EricXu20266/awesome-deepseek-agent-taishen)
- PR: [https://github.com/deepseek-ai/awesome-deepseek-agent/pull/295](https://github.com/deepseek-ai/awesome-deepseek-agent/pull/295)

---

*This whitepaper was written during a Taishen v1.3.5 session. Within this session, 16 million input tokens achieved a DeepSeek prefix cache hit rate of 99%.*

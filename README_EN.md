# taishen

[中文](README.md) | English

**By Eric Xu (二班的Eric)** | v1.7.4 | 2026

---

A desktop AI agent client built for everyday knowledge workers. Born for DeepSeek — turning your files, research, and ideas directly into finished deliverables, not just chat bubbles.

> 📖 To understand taishen's design philosophy and architecture journey, read the [Whitepaper](WHITEPAPER_EN.md).

> ⚠️ While you can connect other LLMs, only DeepSeek has been rigorously tested. Optimal results are not guaranteed with other models.

---

## Where taishen Stands Out: Tools are Raw Materials; Composition is Capability

Most AI tools compete on who has the **longest tool list** — search, web scrapers, code execution, headless browsers... dozens of icons lined up in an impressive presentation grid.

taishen sees it differently: **Anyone can assemble a parts list. Real capability lives in composition.**

Having dozens of built-in tools is nothing extraordinary. What really matters are two things:

**First, Orchestration.** How those tools — combined with workflow skills, external MCP services, and parallel sub-agents — are coordinated into a tailored plan for *the exact problem in front of you*. The same raw ingredients, arranged differently, yield completely different outcomes.

**Second, Self-Construction.** When existing tools fall short, taishen writes its own tools, codifies its own experience, and grows new capabilities — without you touching code or waiting for another release.

That is the true dividing line between an "AI workbench" and a "chat client."

### Base Capability Matrix: Four Tiers, Composed Freely

This is taishen's **base capability matrix** — four tiers that compose together seamlessly. Higher-order evolutions (autonomous tool development, workflow encapsulation, session orchestration) build directly on top of this.

| Category | What It Is | When It Is Used |
|------|-----------|-----------------|
| **Skill** | A working methodology (Markdown template) | Shifts *how* it thinks — providing a structured framework |
| **SubAgent** | Independent sub-agents with dedicated models | Pushing multiple independent tasks concurrently |
| **MCP Service** | External services (search / stocks / code graph...) | Tapping into *what exists outside* |
| **Built-in Tool** | Atomic operations (I/O, execution, network, docs) | Doing the heavy lifting on your disk |

These four are not parallel lists; they form an active matrix. A real-world assignment looks like this:

> *"Audit the financials of these three EV makers over the last three years and draft a comparison report."*

taishen breaks it down automatically:

1. Activates the **deep-research skill** — adopting a "gather evidence first, conclude later" methodology.
2. Launches **three sub-agents** in parallel — each auditing one company's annual filings, news, and balance sheets.
3. Calls **MCP services** — anysearch for public filings, firecrawl for deep company sites, and TDX for market charts.
4. Uses **built-in tools** — parses PDF reports, extracts Excel spreadsheets, and formats the final Word document.
5. Throughout, the **main agent serves as the judge** — sub-agents do the legwork, while final conclusions are drawn by the lead agent.

You typed one single sentence. The orchestration was synthesized by taishen, not configured by you.

### Self-Evolution: taishen Grows Its Own Limbs

This is where taishen stops feeling like traditional software.

**Self-Built Tools** — When a workflow template isn't enough, taishen writes clean TypeScript tools on the fly, compiling and registering them for your next session. It can invoke private APIs, pull npm packages, and run custom logic — **no coding required on your part.**

**Self-Encapsulated Experience** — Recurring workflows, taishen picks up on its own: when the same few steps are walked again and again, it takes note. This isn't a rule you configured — it read it out of everyday collaboration.

taishen will proactively ask: *"This workflow seems to have repeated several times now — want me to package it as a skill?"*

**Trial, Then Solidify** — A newly packaged skill enters a trial state. If it works well and verifies out, it is promoted; if not, it retires quietly. **Nothing is ever solidified automatically** — your word is what counts.

**Capabilities Age and Retire** — Usage is tracked for every capability; ones that go unused for a long time are retired — disabled, never deleted, so nothing useful dies by accident. Before packaging anything, taishen checks first: can an existing capability cover this? Can an existing skill take a parameter instead of building something new?

What does this mean? **Three months in, every user's taishen looks completely different.** An academic's client develops deep citation tools; a marketer's client builds cross-platform publishing pipelines. It grows along the grain of your daily work.

---

## Commander Agent Engine

taishen is not a Q&A chatbot. It is a Commander-class agent that plans, schedules, and verifies results autonomously.

**Five-Stage Workflow** — Plan → Todo → Execute → Verify → Done. Live progress updates on the right dock. The AI decomposes complex assignments and verifies deliverables, consulting you only on pivotal decisions.

**Proactive Clarification Modals** — This is taishen's core interaction paradigm, not a side gimmick. Don't know how to write prompts? Just say *"analyze these competitor PDFs."* If the request is ambiguous, taishen pops open an inquiry modal: *"Do you prioritize feature parity or pricing models?" "Should the deliverable be a Word brief or a visual mind map?"* Clicking a button is 100x faster than rolling back a hallucinated response. You are the **client**, not a prompt engineer.

**Root-Cause Diagnosis** — Diagnoses the underlying issue before prescribing fixes. Never sweeps errors under the rug with fragile workarounds.

**Responsible Delivery** — Clarifies ambiguous goals upfront, states assumptions explicitly when uncertain, and self-checks before sign-off.

**Emotion Overrides Task** — If it senses frustration or fatigue (e.g., *"stop," "this is annoying"*), its task instinct yields immediately without nagging or pushing.

**Never Ram a Wall Twice** — If an approach fails twice consecutively, it changes course or pauses to explain the blocker instead of stubbornly repeating the same mistake.

---

## Tai An Canvas System

A built-in streaming content workspace — the AI crafts content in real time as you watch it take shape.

Eleven specialized canvases cover every deliverable:

| Canvas | Capability |
|------|------|
| **Writing** | Character-by-character typewriter streaming; highlight any passage to polish in place |
| **Code** | Monaco editor + embedded terminal; write code, run tests, and inspect side-by-side diffs in one view |
| **HTML** | True WYSIWYG preview; select page elements to leave direct revision notes |
| **Terminal** | Transparent command execution with live output and instant killswitches |
| **Data Analysis** | Tables + interactive charts; drop in CSVs to generate pivot views and trends |
| **Color Grading** | Layers, composite masks, curves; runs lightweight on-device models for depth, sky, and facial segmentation; exports layered PSDs |
| **Vector Design** | AI-native vector artboard — 62-item UI library + 8 real device preview frames; exports SVG/PNG/JSON |
| **PPT** | Native transitions and animations + 178 shapes + 39 WordArt styles + 13 chart types; imports existing `.pptx` and preserves native editability |
| **Beads** | Offline rasterization of images into perler bead grid patterns with color matching and bead counts |
| **A-Stocks** | Plain-language strategy builder + condition engine + live news tickers + chart markups |
| **Desktop** | Real-time window preview + three independent permission tiers + six automated screen actions |

**Flow Thinking Canvas** (`mode="flow"` on HTML canvas) — Visualized structural thinking: 6 node types (including 9 ECharts charts), 3 layout engines (tree, timeline, matrix), and one-click PNG export.

**Bidirectional Editing** — The AI writes, and you can edit directly. Comprehensive version history lets you roll back anytime. AI work shifts from a mysterious black box to a transparent workbench.

**Canvases are Work surfaces, Not Screens** — Dragging elements or framing regions feeds spatial and semantic signals right back to the AI.

---

## Desktop Automation

With your permission, taishen can inspect your screen and operate external applications (Experimental).

Three independent permission boundaries: **Monitoring Area** (what it can view), **Upload Authorization** (which frames reach the cloud model), and **Operation Authorization** (where clicks and keys may land). It cannot see or touch areas outside your authorization.

Six atomic actions: write draft, send message, scroll, switch dialog, dismiss modal, request human intervention.

Safety guardrails: Every action is tethered to the exact captured frame; if the window geometry changes, the action is rejected. Observation pauses when user input is detected. Outbound text is scanned locally to prevent credential leakage.

---

## Parallel SubAgents

Traditional AI handles one task at a time. taishen can distribute independent work to multiple specialized sub-agents at once.

**Tailored Models per SubAgent** — DeepSeek for deep reasoning, vision models for diagrams, and code models for unit tests. Simply describe your goal, and taishen delegates appropriately.

**13 Built-in Specialists** — General Tasks, Code Exploration, Task Planning, Architecture Design, DevOps, AI Engineering, DevRel, Content Writing, Vision OCR, Image Generation, Dynamic Routing, Bulk Refactoring, and Independent Code Audit.

**Project Sessions** — Orchestrate complex projects across multiple isolated, persistent sessions running in parallel.

---

## IM Remote Access

Away from your desk? Chat apps on your phone become your mobile taishen terminal.

| Platform | Integration | Capabilities |
|------|-------------|--------------|
| Feishu (Lark) | Custom Enterprise App | Direct message + group chat @bot, file transfer |
| QQ | QQ Open Platform Bot | Direct message + group chat + channel, file transfer |
| WeChat | iLink ClawBot | Direct message, file transfer |
| Slack | Slack API | Direct message + group chat @bot, rich text & files |

Streaming replies, document delivery, and confirmation modals are fully routed to your phone.

---

## External Agent Session Migration

Don't abandon chats accumulated in other tools. taishen can ingest and migrate history from **17+ external agents** — including Claude Code / Cowork, Codex, Cursor, ChatGPT, Gemini, Qoder, Kimi, and WorkBuddy.

Search by session ID or keywords, review past discussions, and promote them into taishen's active database to continue right where you left off.

---

## Multi-Provider & Models

* **Seamless Switching** — DeepSeek, OpenAI, Codex, Google Gemini, Mimo, and local endpoints. Context windows and reasoning effort can be tuned per model.
* **Subscription Quotas** — Connect Codex or Gemini subscriptions directly; monitor remaining quotas in the card dock.
* **FlexDog Dynamic Routing** — Switch between heavy reasoning models and lightning-fast models mid-turn without restarting.
* **Peak & Off-Peak Pricing** — Real-time cost ledger adjusted for provider pricing tiers.

---

## Four-Layer Security Architecture

1. **Path Access Control (PathGuard + PathResolver)** — Strict sandboxing to mounted workspaces. Sensitive system folders and symlink escapes are hard-blocked.
2. **Command Sandbox** — L1 step-by-step approval, L2 autonomous review, L3 full trust. Destructive commands (`rm -rf /`, `shutdown`) and shell script injections are terminated immediately.
3. **Network Boundary** — DeepSeek API and GitHub are open by default; unexpected external domains require explicit whitelist approval. Internal IP spaces (SSRF protection) are blocked.
4. **Gate Rejection Lockout** — Rejecting an action twice locks that operation category from bothering you again.

---

## AI Self-Diagnosis

taishen features a structured internal logging system. The AI queries its own runtime logs via `log_query`:
* Tool call failed? Pinpoint root cause within seconds.
* Context anomalies? Trace full call chains.
* Token spikes? Inspect cache hit rates directly.

From *"user helps AI debug"* to *"AI inspects, fixes, and reports back."*

---

## Quick Start

### Installation

* **taishen_setup_1.7.4.exe** — Windows Installer (Recommended)
* **taishen_1.7.4.zip** — Windows Portable Archive
* **taishen_1.7.4_macOS_arm64.dmg** — macOS Apple Silicon (M1-M4)

> 📥 **Downloads:** [GitHub Releases](https://github.com/EricXu20266/taishen/releases)

### Setup

1. Launch taishen and enter your DeepSeek API Key in Settings.
2. (Optional) Enable needed MCP services or skills in the Plugins tab.
3. Start talking — describe your goal or drop in your files.

---

## License

Copyright (c) 2026 Eric Xu (二班的Eric). All Rights Reserved.

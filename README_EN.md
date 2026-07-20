# taishen

[中文](README.md) | English

**Eric Xu · Vibe Coding** | v1.3.7 | 2026

---

An AI agent desktop client for everyone. Born for DeepSeek — turn your materials and ideas directly into deliverable structured output, not just chat.

> 📖 For a deep dive into Taishen's design philosophy and technical architecture, read the [Whitepaper](WHITEPAPER_EN.md).

> ⚠️ Taishen can connect to other LLMs, but only DeepSeek has been fully tested. Other models are not guaranteed to work as expected.

---

## Core Capabilities

### 🤖 Commander Agent Engine

Taishen is not a "Q&A bot" — it's a Commander-mode agent that autonomously plans, orchestrates tools, and verifies results.

**Five-Stage Workflow** — Plan → Todo → Execute → Verify → Done. Every step is visible in real-time on the right panel. The AI independently breaks down complex tasks, orchestrates the toolchain, and verifies output quality — you only need to confirm key decisions.

**Root-Cause Diagnosis** — Diagnose first, prescribe second. Distinguishes symptom fixes from root-cause fixes. No workarounds passed off as solutions.

**Closed-Loop Accountability** — From planning to delivery, the complete chain. The AI proactively questions fuzzy requirements, states assumptions when uncertain, and self-verifies upon completion.

### 🎨 Tai An Canvas System

Taishen's built-in streaming content workspace — AI writes in real time as you watch.

Six canvas types for every scenario:

| Canvas | Capability |
|------|------|
| Writing | Character-by-character streaming output |
| Code | Syntax highlighting + embedded terminal |
| HTML | WYSIWYG preview, click-to-annotate elements |
| Terminal | Fully visible command execution, stop anytime |
| Data | Tables + four chart types, drag CSV to visualize |
| Image | Display + annotation + comparison |

All canvases are **bidirectional** — AI writes, you edit directly. Version history tracks every change for instant rollback. When AI's work process shifts from black box to visible, you don't need to "trust AI will get it right" — you watch it happen.

### 🧩 Parallel Agents

Traditional AI does one thing at a time. Taishen dispatches multiple independent tasks to parallel workers — searching financial reports while reading industry analysis while crunching data, all simultaneously. Each worker can use a different model: DeepSeek for deep reasoning, GPT-4o for visual tasks. Just say "analyze these reports" — Taishen distributes the work automatically.

### 🧬 Experience Encoder

Taishen doesn't just use tools — it **creates** them.

**skillCreator** — Package a successful workflow into a Skill (Markdown template, agentskills.io open standard), effective immediately.

**skillPatcher** — Skills evolve. AI appends or replaces content as it discovers optimizations during use. Skills get more precise with every use.

**tool_creator** — When Skills aren't enough, AI writes real TypeScript tools. Compile, register, effective next session.

Your Taishen learns your workflow and develops a unique capability profile over time.

### 📱 IM Remote Access

Out and about without your computer? Feishu, QQ, and WeChat on your phone become your Taishen terminal.

| Platform | Connection | Capabilities |
|------|---------|------|
| Feishu | Enterprise self-built app | DM + group chat @bot, file sending |
| QQ | QQ Open Platform Bot | DM + group chat + QQ Channel, file sending in DM |
| WeChat | iLink ClawBot | DM, file sending |

All three IM channels support streaming replies, file transfer, and remote approval popups. AI-generated documents, spreadsheets, and presentations can be pushed directly to your phone.

Configuration: Taishen Settings → IM Access panel, enter AppId/AppSecret to launch the Gateway.

### 🧩 SubAgent System

Equip Taishen with a professional team — dispatch sub-agents to work in parallel, each with their own specialty.

**Built-in SubAgents (10 types)**:
- general-purpose (general tasks), explorer (code exploration), planner (task planning)
- software-architect (architecture design), infrastructure-maintainer (infrastructure ops)
- ai-engineer (AI engineering), developer-advocate (developer advocacy)
- content-creator (content creation), myeyes (visual recognition), flexdog (dynamic model routing)

**v3.1 Architecture Upgrade** — SubAgents now have full capability parity with the main agent: Skill system, Memory, MCP external services, Hooks, plus dedicated color identifiers and independent file output. The agents you dispatch can truly hold their own.

**Cross-Model Collaboration** — With multiple AI providers configured, Myeyes can call vision models in the background for image recognition, and FlexDog can switch to other models for task execution — multiple AIs working together within a single conversation.

### 🔌 Multi-Provider & Extension Ecosystem

**Multi AI Provider** — Freely switch between DeepSeek, OpenAI, Mimo, and more. Reasoning intensity and context window parameters are per-model, allowing fine-tuning for each model individually.

**Skill System** — Compatible with the [agentskills.io](https://agentskills.io) open standard (used by Claude Code, Cursor, GitHub Copilot, and 35+ other tools). Create custom Skills, search and install community Skills from GitHub/Gitee, or let AI autonomously create new Skills. Supports group/subgroup two-level organization.

**MCP Protocol** — Supports Streamable HTTP / SSE / stdio transport. Connect external capabilities like web search, browsers, and academic databases to the AI.

**Plugins + Self-Creating Tools** — Drop plugins in to load instantly; AI can write new tools (TypeScript) on demand — no manual coding required.

### 📄 Full Document Workflow

- Drag and drop Word (.docx), PPT (.pptx), PDF, Excel (.xlsx) files for parsing
- AI analyzes and generates Word reports, PPT presentations, Excel spreadsheets, PDF documents in one click
- HTML Advanced Previewer: preview AI-written web pages directly inside Taishen, select elements to annotate revision suggestions — WYSIWYG

### 🛡️ Four-Layer Security

**Path Access Control** — AI only accesses workspaces you designate. System directories, disk roots, and home directories are auto-blocked. Short filename bypass and symlink escape recognized and blocked.

**Command Execution Control** — Three-tier sandbox: L1 step-by-step approval → L2 AI autonomous review → L3 full trust. Fatal commands blocked outright (`rm -rf /`, `shutdown`, etc.). Command injection and script inline execution blocked at sandbox layer.

**Network Boundary Control** — DeepSeek API, GitHub, and common domains open by default. Other domains require whitelist approval. Internal addresses (127.x, 192.168.x, 10.x) auto-blocked to prevent SSRF attacks.

**Gate Rejection Tracker** — Same operation rejected twice → system auto-blocks. AI won't pester you after a clear rejection.

Every file modification auto-backed up locally. Recycle bin keeps accidentally deleted sessions, Skills, and SubAgents forever. **It's precisely these four layers that let you confidently delegate more authority to AI.**

### 🩺 AI Self-Diagnosis

Taishen has a built-in structured logging system (6 levels × 9 categories). The AI queries its own runtime logs: tool failure → auto-locate root cause; session anomaly → trace full call chain; performance drop → find bottleneck. From "user helps AI debug" to "AI debugs itself" — no technical knowledge needed, no log diving required.

### 🎨 Experience Highlights

- **6 Themes** — Deep Ocean Amber (default) / Minimalist B&W / Soft Eye-Care / Follow System
- **AI Completion Sound** — Plays a chime when the AI finishes responding; toggleable (on by default)
- **Context-Aware Memory** — Remembers your preferences, work style, and frequently used tools across sessions
- **1M Token Context** — Full DeepSeek V4 window support; long papers and large projects without pressure
- **Proactive Pop-Up Guidance** — Can't write prompts? Just say one sentence. Vague requirements? AI pops up to confirm — clicking is 100× faster than guessing wrong and redoing
- **99% Prefix Cache Hit Rate** — Prompt structure deeply optimized for DeepSeek's cache mechanism. Per-round cost constant even in 200M+ token sessions
- **Built-in Screenshot Tool** — Taishen screenshots itself. With Myeyes, fully automated image recognition, annotation, and editing
- **Conversation Search** — Natural-language cross-session full-text search; the AI can also proactively reference past discussions
- **Scheduled Tasks** — Five modes: Interval / Daily / Weekly / Cron / One-shot. AI can create and manage tasks autonomously
- **Clickable File Paths** — Project-relative paths and backtick-wrapped paths are automatically rendered as clickable links
- **Right-Click Context Menu** — Rename, delete, recover from recycle bin — all with a right-click

---

## Quick Start

### Installation

- **taishen_setup_1.3.7.exe** — Windows installer (recommended)
- **taishen_1.3.7免安装.zip** — Windows portable, extract and run
- **taishen_1.3.7_macOS_arm64.dmg** — macOS Apple Silicon (M1-M4) installer

> 📥 **Download:** [GitHub Releases](https://github.com/EricXu20266/taishen/releases) — Go to the latest version and download from "Assets".

### Configuration

1. Launch Taishen, enter your DeepSeek API Key in Settings
2. (Optional) Enable desired MCP services in the Tools & Plugins page
3. (Optional) Enable professional Skills in the Skill Management page
4. Start a conversation — describe your needs, drag in files, and you're set

### Recommended Models

- **DeepSeek V4 Pro** (default) — Full-featured, ideal for deep research, paper writing, and code development
- **DeepSeek V4 Flash** — Fast response, suitable for daily Q&A and lightweight tasks

---

## File Verification (SHA256)

| File | SHA256 |
|------|--------|
| taishen_setup_1.3.7.exe | `CDB977AFEE0AAEB6F54374681DFA16A2C1AB10CBD2DAAFD449350F68AB93F3A4` |
| taishen_1.3.7免安装.zip | `6A5763858D1C5781323CC9A7B88426157602AEA06DB933E9BB8DADCF03583BAA` |
| taishen_1.3.7_macOS_arm64.dmg | `C5AB35E7E1EE4BA131802C208CF30A5255F5C6ED0060A79DECB159AE9F2BFE8A` |

---

## System Requirements

| Item | Minimum |
|------|---------|
| OS | Windows 10+ / macOS 12+ |
| RAM | 8 GB |
| Disk | 500 MB |
| Network | DeepSeek API access required |

---

## FAQ

**Q: Do I need to deploy my own model?**
No. Taishen connects to DeepSeek's cloud models via API. You only need an API Key.

**Q: Are other models supported?**
The client supports configuring OpenAI-compatible endpoints, but only DeepSeek has been fully tested. You can compare different models within the same conversation via the FlexDog SubAgent.

**Q: Is my data secure?**
All data is stored locally (conversation history, user profile, file backups) and is never uploaded to Taishen servers. API Keys are stored using system-level encryption (Windows DPAPI / macOS Keychain).

**Q: Can I use it on my phone?**
Yes. Connect through Feishu, QQ, or WeChat IM, and your phone becomes your Taishen terminal — streaming replies, file transfers, and approval popups all work seamlessly.

**Q: What's the difference between Skill and MCP?**
Skill = AI's working mode ("how to think") — a Markdown file that changes AI's behavior style when activated. MCP = AI's external tools ("what to use") — connecting web search, browsers, and other capabilities to the AI.

**Q: Can I migrate data from Windows to Mac?**
Yes. Copy the `.taishen` folder from your Windows user directory to your macOS user directory (`~/.taishen`). Note that API Keys need to be re-configured (different encryption methods per platform).

**Q: Do SubAgents consume tokens?**
Yes. SubAgent token consumption is accumulated in the session budget, with complete and transparent cost tracking.

---

## License

Copyright (c) 2026 Eric Xu. All Rights Reserved.

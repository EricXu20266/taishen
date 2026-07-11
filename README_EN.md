# Taishen

[中文](README.md) | English

**Eric Xu · Vibe Coding** | v1.3.4 | 2026

---

An AI agent desktop client for everyone. From Information to Results — turn your materials and ideas directly into deliverable structured output, not just chat.

> ⚠️ Taishen can connect to other LLMs, but only DeepSeek has been fully tested. Other models are not guaranteed to work as expected.

---

## Core Capabilities

### 🤖 Commander Agent Engine

Taishen is not a "Q&A bot" — it's a Commander-mode agent that autonomously plans, orchestrates tools, and verifies results.

**Five-Stage Workflow** — Plan → Todo → Execute → Verify → Done. Every step is visible in real-time on the right panel. The AI independently breaks down complex tasks, orchestrates the toolchain, and verifies output quality — you only need to confirm key decisions.

**Root-Cause Diagnosis** — Diagnose first, prescribe second. Distinguishes symptom fixes from root-cause fixes. No workarounds passed off as solutions.

**Closed-Loop Accountability** — From planning to delivery, the complete chain. The AI proactively questions fuzzy requirements, states assumptions when uncertain, and self-verifies upon completion.

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

### 🛡️ Security & Control

- **Three-Tier Sandbox** — L1 approval required → L2 autonomous review → L3 full trust, globally applied
- **Workspace Isolation** — AI can only access folders you designate; all operations are auditable
- **Command Risk Rating** — Shell commands labeled with 🔴🟡🟢 three-level risk before execution
- **Auto-Backup on Edit** — Every file modification is automatically snapshotted locally; restore anytime
- **Recycle Bin** — Accidentally deleted conversations, Skills, and SubAgents go to the recycle bin, never expire, waiting for you to permanently clear

### 🎨 Experience Highlights

- **6 Themes** — Deep Ocean Amber (default) / Minimalist B&W / Soft Eye-Care / Follow System
- **AI Completion Sound** — Plays a chime when the AI finishes responding; toggleable (on by default)
- **Context-Aware Memory** — Remembers your preferences, work style, and frequently used tools across sessions
- **1M Token Context** — Full DeepSeek V4 window support; long papers and large projects without pressure
- **Prefix Cache Optimization** — Prompt structure designed for DeepSeek's cache-hit mechanism, targeting >98% hit rate. Measured at ~99% cache hit rate even in 200M+ token sessions, with constant per-round cost
- **Conversation Search** — Natural-language cross-session full-text search; the AI can also proactively reference past discussions
- **Scheduled Tasks** — Five modes: Interval / Daily / Weekly / Cron / One-shot. AI can create and manage tasks autonomously
- **Clickable File Paths** — Project-relative paths and backtick-wrapped paths are automatically rendered as clickable links
- **Right-Click Context Menu** — Rename, delete, recover from recycle bin — all with a right-click

---

## Quick Start

### Installation

- **taishen_setup_1.3.4.exe** — Windows installer (recommended)
- **taishen_1.3.4免安装.zip** — Windows portable, extract and run

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
| taishen_setup_1.3.4.exe | `61485F7AD4BA68734A9A1FCE5BE66999A5FBF3EDB16BAC9F0125D999B4BD544D` |
| taishen_1.3.4免安装.zip | `8AC2A55E45D90CA96F6AA2CC6465390185025B4A137AC2A986059F7D0D64CE68` |

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

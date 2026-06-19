# 泰深 taishen

**二班的Eric · Vibe Coding 作品** | v1.2.3 | 2026

---

面向普通人的 AI 智能体桌面客户端，交互更加友好，更加的智能，针对 DeepSeek 深度特调。

核心理念：**从信息到成果**——将你的资料和想法直接转化为可交付的结构化产出（代码、报告、论文、PPT、数据分析），而非仅仅聊天。

> ⚠️ **仅支持 Windows 系统。** 客户端可连接其他大模型，但未经过实机测试，不保证效果。

---

## 快速开始

### 安装
- **taishen_setup_1.2.3.exe** — Windows 安装包（推荐）
- **taishen1.2.3免安装版.zip** — 解压即用免安装版

> 📥 **下载地址：** [GitHub Releases](https://github.com/EricXu20266/taishen/releases) — 进入页面后选择最新版本，在「Assets」中下载所需文件。

### 配置
1. 启动泰深，在设置页填入 DeepSeek API Key
2. （可选）在工具&插件页启用需要的 MCP 服务
3. （可选）在技能管理页启用专业 Skill
4. 开始对话——拖入文件、直接描述需求即可

### 推荐模型
- **DeepSeek V4 Pro**（默认）— 全功能，适合深度研究、论文写作
- **DeepSeek V4 Flash** — 快速响应，适合日常问答、代码辅助

---

## 核心功能

### 🧠 智能体引擎

- **Skill 技能系统** — 兼容 [agentskills.io](https://agentskills.io) 开放标准，可自建 Skill 或从 GitHub/Gitee 搜索安装社区 Skill，支持 AI 自主创建新 Skill
- **任务追踪** — Plan→Todo→Execute→Done 五阶段工作流，右侧面板实时可见

### 🔌 深度扩展
- **MCP 协议支持** — 支持三源接入 MCP 
- **插件扩展系统** — 支持自定义功能插件
- **工具自主创建** — AI 可根据需求自行编写新工具（TypeScript）

### 📄 文档全流程
- **多格式文档解析** — 直接拖入 Word (.docx)、PPT (.pptx)、PDF、Excel (.xlsx) 文件
- **扫码版 PDF 识别** — 内置 OCR 引擎，扫描版文献也能读
- **一键生成交付物** — AI 分析后直接输出 Word 报告、PPT 演示、Excel 表格

### 🛡️ 安全可控
- **三级沙箱模型** — L1 默认关闭（审批后执行）→ L2 自主审查 → L3 完全信任，灵活掌控
- **工作区隔离** — AI 只能访问你指定的文件夹，所有操作可审计
- **命令安全风险评级** — 执行 Shell 命令前标注 🔴🟡🟢 三级风险
- **编辑前自动备份** — 每次修改文件自动快照，随时恢复

### 🎨 体验优化
- **4 套主题** — 深海琥珀（默认）/ 极简黑白 / 柔光护眼 / 跟随系统
- **上下文感知记忆** — 跨会话记住你的偏好、工作风格和常用工具
- **1M Token 上下文** — DeepSeek V4 全窗口支持，长论文、大项目无压力
- **前缀缓存优化** — 针对DeepSeek的缓存命中机制，特别设计了系统prompt结构，目标缓存命中率 >95%，大幅节省 Token 消耗。(实机测试中，多轮2亿token消耗会话，缓存命中平均98.7%）

---

## Skill 系统

泰深兼容 [agentskills.io](https://agentskills.io) 开放标准——这是由 Anthropic 发起、已被 **35+ 工具**（Claude Code、Cursor、GitHub Copilot、VS Code 等）采用的 Skill 规范。

这意味着：

- ✅ **自建 Skill** — 用 Markdown 写一份 SKILL.md，拖入泰深即可生效
- ✅ **无痛迁移** — 你在 Claude Code、Cursor 等其他兼容 agentskills.io 的工具中创建的 Skill，直接复用
- ✅ **社区共享** — 从 GitHub/Gitee 搜索安装他人分享的 Skill
- ✅ **AI 自主创建** — 告诉 AI 你想要的工作流程，它帮你写出 Skill

无需学习新格式，不用重复造轮子。一份 SKILL.md，到处可用。

---

## 文件校验（SHA256）

| 文件 | SHA256 |
|------|--------|
| taishen_setup_1.2.3.exe | `BD6AE9539EBE83E62D0DCF37FD0D04DE26CF98BE72DEF9CCE1F41F6B84135729` |
| taishen1.2.3免安装版.zip | `0956EA2BED5AC9ACB09410B953D038EB945AD7768694F966467843136281E5F5` |

---

## 系统要求

| 项目 | 最低配置 |
|------|---------|
| 操作系统 | Windows 10+ |
| 内存 | 8 GB |
| 磁盘空间 | 500 MB |
| 网络 | 需连接 DeepSeek API |

---

## 常见问题

**Q: 需要自己部署模型吗？**
不需要。泰深通过 API 连接 DeepSeek 云端模型，你只需要一个 API Key。

**Q: 支持其他模型吗？**
客户端支持配置 OpenAI 兼容接口，但仅 DeepSeek 经过完整测试，其他模型不保证效果。

**Q: 数据安全吗？**
所有数据存储在本地（包括对话记录、用户画像、文件备份），不上传至泰深服务器。API Key 使用系统级加密存储。

**Q: Skill 和 MCP 有什么区别？**
- **Skill** = AI 的工作模式（"怎么想"）——一份符合 [agentskills.io](https://agentskills.io) 开放标准的 Markdown 文件，激活后改变 AI 的行为风格和专业领域
- **MCP** = AI 的外部工具（"用什么"）——给 AI 接入网页搜索、浏览器、学术数据库等能力

**Q: 有 Mac 版本吗？**
暂无。当前仅支持 Windows。

---

## 许可证

MIT License

Copyright (c) 2026 二班的Eric

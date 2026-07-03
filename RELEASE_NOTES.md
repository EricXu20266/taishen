## 🚀 泰深 v1.3.1 正式发布

Deep Research 全面升级、Diff 撤销上线、需求补齐、MCP 体验优化与多项修复。

### 核心功能
- DeepSeek V4 全模型支持（V4-Pro / V4-Flash）
- 多供应商支持（DeepSeek / OpenAI / Mimo 等自由切换）
- 视觉代理 Myeyes — 模型不支持多模态也能"看图"，IM 渠道全面打通
- FlexDog 动态模型引擎 — 对话中随时切换模型
- Commander 形态 — AI 自主规划、调度、验证一条龙
- HTML 高级预览器 + 元素批注系统 — 所见即所得，选中即标注
- 回收站系统 — 误删会话、Skill、子代理随时捞出，永不过期
- Skill 自定义安装与扩展（兼容 agentskills.io 开放标准，支持 subgroup 子分组）
- MCP 服务接入（多源连接，支持 Streamable HTTP / SSE / stdio）
- IM 远程接入（飞书 / QQ / 微信），全面支持图片发送
- SubAgent 子代理并行调度（v3.1 架构，独立 Skill/Memory/MCP）
- 定时任务调度器 + 全局会话搜索
- macOS 双架构正式支持（x64 + arm64）

### v1.3.1

- MCP安装配置系统小重构，主要针对安全加固，现在MCP的的密钥全程加密。
  - 更新版本后原先MCP配置Json内的密钥会自动加密转码。
  - 当然如果遇到MCP连接报错，建议你手动再输入一次密钥。
- 优化了新的deep research的流转流程和最终report质量。
- 泰深的行为引导进一步强化。
- Diff 撤销按钮上线。对话流里每个代码修改后的show diff块上有撤回按钮。
- 启动性能微调：正常退出后跳过完整性校验，下次启动更快。顺带加了启动耗时日志，哪里慢了一目了然。

### 安装
- **taishen_setup_1.3.1.exe** — Windows 安装包（推荐）
- **taishen_1.3.1免安装.zip** — 解压即用免安装版
- **taishen_1.3.1_macOS_arm64.dmg** — macOS Apple Silicon (M1-M4) 安装包（即将发布）

### 文件校验（SHA256）
| 文件 | SHA256 |
|------|--------|
| taishen_setup_1.3.1.exe | `DE2AB57A7D8E13F3BA3C3EA0757C72C618FEB7A422D838D97492698DF92AB54D` |
| taishen_1.3.1免安装.zip | `9423410640C2239682ACBA4B19CA2AB5DB02424593DF9BF38566A7950996E0A9` |
| taishen_1.3.1_macOS_arm64.dmg | 待 CI 发布 |

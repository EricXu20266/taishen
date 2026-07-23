## 🚀 泰深 v1.3.8 正式发布

语音交互、消息归档与 Headless CLI 三大更新。同步发布[白皮书](WHITEPAPER.md)——《为 DeepSeek 而生的桌面 AI 工作台》。

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

### v1.3.8

- 重大更新，语音交互系统全面上线！现在泰深能听会说——语音输入（STT）转文字，语音输出（TTS）朗读回复，三种模式自由切换（关/手动/自动/AI决定）。
  - 语音输入（STT）转文字，使用Google云端API接口或是本地whisper模型。
    - 使用Google云端接口需要配置Google的api key。
    - 使用本地Whisper模型，在首次使用的时候需要下载模型，工作模式是自建一个whisper http 服务使用。
    - Whisper配置4种模型下载选择，越大精度越高但是识别速度会越慢。推荐使用Small或是base模型。
    - Whisper推理引擎也有两种，CPU或是GPU，推荐使用GPU，配置GPU推理引擎需要CUDA环境，初次使用会下载安装，如果你已经有了CUDA，只需下载Whisper本体。
  - 语音输出（TTS）朗读回复，配置了Windows系统的TTS（macOS不支持），以及云端免费的Edge TTS。
- 重大更新，消息归档系统就位。泰深会自动把过期会话（默认60天，推荐30天）迁移到archive文件夹内的JSONL，前台设置页可以自己调归档阈值天数，WAL checkpoint + VACUUM 双管齐下回收磁盘空间。
- 重大更新，Headless CLI 模式上线。`泰深.exe --headless -p "你的问题"` 纯命令行运行，不弹 GUI 窗口，适合脚本集成和服务器场景。
- 新增 Anthropic Messages API 协议支持，Claude 系列模型现在可以接入泰深了。
- 为泰深添加了一个Monitor 监控工具，事件驱动监控，支持持久化（重启恢复）+ 智能告警（自定义关键词触发 Agent 分析）+ 速率熔断。
- 内置浏览器补充了浏览器扩展插件的安装与管理按钮。
- spawn_agent 子代理增强：支持 `skill_ids` 和 `mcp_ids` 参数，技能和 MCP 工具直接注入子代理，主身不用激活，上下文保持干净。
- FlexDog 灵活狗更灵活了：在你配置了多个provider和多个model时，你可以指定任意具体的model来使用。
- 修复了 UI 按钮 hover 效果不统一的问题，现在所有聊天按钮的 hover/active 动画整齐划一。
- 一堆零零散散的小修复。旧的不去新的不来，代码如是，bug 亦如是。

### 安装
- **taishen_setup_1.3.8.exe** — Windows 安装包（推荐）
- **taishen_1.3.8免安装.zip** — 解压即用免安装版
- **taishen_1.3.8_macOS_arm64.dmg** — macOS Apple Silicon (M1-M4) 安装包

### 文件校验（SHA256）
| 文件 | SHA256 |
|------|--------|
| taishen_setup_1.3.8.exe | `522D4DF7CC29F8CD8CD62C043D967CF72ECF1B3B237E551F55D033EB8F2F4D7D` |
| taishen_1.3.8免安装.zip | `E8FD77721E539D488581F01B58227AF7AA6901489CAE3A0A7FA42F70F772533E` |
| taishen_1.3.8_macOS_arm64.dmg | `974AC6C2BD940B1A040652021A4F97210CAB9CB1C9F82875EB1C5DB7826F5C36` |

---

📖 深入了解泰深的设计哲学与技术架构，请阅读[白皮书](WHITEPAPER.md)。

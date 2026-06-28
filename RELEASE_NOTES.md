## 🚀 泰深 v1.2.8 正式发布

专为 DeepSeek 深度调优的 AI 智能助手桌面客户端。macOS 双架构正式支持，导航视觉升级，AI 完成提示音，路径点击等体验全面优化。

### 核心功能
- DeepSeek V4 全模型支持（V4-Pro / V4-Flash）
- 多供应商支持（DeepSeek / OpenAI / Mimo 等自由切换）
- 视觉代理 Myeyes — 模型不支持多模态也能"看图"，IM 渠道全面打通
- FlexDog 动态模型引擎 — 对话中随时切换模型
- Commander 形态 — 全景能力重构，AI 自主规划、调度、验证一条龙
- HTML 高级预览器 + 元素批注系统 — 所见即所得，选中即标注
- 回收站系统 — 误删会话、Skill、子代理随时捞出，永不过期
- macOS 平台正式支持（x64 + arm64 双架构独立安装包）
- Skill 自定义安装与扩展（兼容 agentskills.io 开放标准，支持 subgroup 子分组）
- MCP 服务接入（多源连接，支持 Streamable HTTP / SSE / stdio）
- 插件扩展系统 + 工具自主创建
- IM 远程接入（飞书 / QQ / 微信），全面支持图片发送
- SubAgent 子代理并行调度
- 定时任务调度器 + 全局会话搜索

### v1.2.8 更新亮点
- macOS 双架构独立安装包 — Apple Silicon (M1-M4) 和 Intel 分别出包，各取所需
- 左侧导航图标化 — 技能/MCP/工具&插件/子代理改为图标一排，界面更紧凑
- AI 完成提示音 — AI 回复完毕时播放提示音，设置页可开关（默认开且持久化）
- 文件路径可点击 — 项目相对路径和反引号内文件路径自动渲染为可点击链接
- 未知 /命令 兜底 — 输入未匹配的 /命令 时弹窗询问用户意图，不再默默丢弃
- Skill 系统 subgroup 子分组 — 支持 group 内二级分类，Skill 面板层级更清晰
- Content-Security-Policy 安全加固 — 消除 Electron 安全警告，生产模式执行严格 CSP
- 会话标题生成改进 — 提前生成 + 实时刷新侧边栏，标题不再缺席
- 命令面板优化 — 过滤只取命令名，避免参数干扰导致命令退化为文本
- SubAgent v3.1 修复 — API 类型错误 + 通知队列孤儿双根因修复
- 滚动体验全面优化 — 事件驱动替代定时器，thinking 块首次有内容立即滚动，消除抖动
- AI 制度性闭合 — 追根溯源三关卡嵌入系统 prompt，诊断能力升级

### 安装
- **taishen_setup_1.2.8.exe** — Windows 安装包（推荐）
- **taishen1.2.8免安装版.zip** — 解压即用免安装版
- **taishen_1.2.8_macOS_arm64.dmg** — macOS Apple Silicon (M1-M4) 安装包
- **taishen_1.2.8_macOS_x64.dmg** — macOS Intel 安装包

### 文件校验（SHA256）
| 文件 | SHA256 |
|------|--------|
| taishen_setup_1.2.8.exe | `DF083F45EB61307713D6F11ECA9EA83537D72D4CDEE6EAD73EF809759ED6F104` |
| taishen1.2.8免安装版.zip | `EE1C0153F36E5CD4D8F9C381D1996E212D2890C3B5FA2AB5BCA310115EB2051D` |
| taishen_1.2.8_macOS_arm64.dmg | `15F7797769E4927800D83702C3EDA45BF0437E5EB85B9F708C072AE94711D00F` |
| taishen_1.2.8_macOS_x64.dmg | `39262B56098A7D4FAA449D55F2A21AA1017A09C729DAEB56123D0D63FAE10590` |


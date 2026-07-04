## 🚀 泰深 v1.3.2 正式发布

Qwen 本地模型接入、上下文窗口分档管理、轮次 Undo 上线与多项修复。

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

### v1.3.2

- Provider接入调整，现在本地部署Qwen模型也可以接入。开发者是使用的vllm拉起的Qwen3.5 9B模型进行测试的。
  - Qwen参数里面，max-model-len 建议设置>= 32768。
  - 上下文窗口管理从一刀切的开关升级为数字下拉选择——支持 1M / 256K / 128K / 32K 四档，匹配你实际用的模型。
- 添加了轮次undo按钮，现在可以一键让agent恢复上一轮全部操作。
- 修复记忆索引无非正确删除的bug

### 安装
- **taishen_setup_1.3.2.exe** — Windows 安装包（推荐）
- **taishen_1.3.2免安装.zip** — 解压即用免安装版


### 文件校验（SHA256）
| 文件 | SHA256 |
|------|--------|
| taishen_setup_1.3.2.exe | `8C57A2439AD5B3E21319B4D18387831C0FEE403E30C47CCCD0C8E39E37B6A6B8` |
| taishen_1.3.2免安装.zip | `8F1A1A1E7D106F611E8B96FFFB68F03F480C6D7F2C9ACF1879A85DD364184DF5` |


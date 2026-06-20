## 🚀 泰深 v1.2.4 正式发布

专为 DeepSeek 深度调优的 AI 智能助手桌面客户端，千万级 token 长会话每轮仅 2 分钱。

### 核心功能
- DeepSeek V4 全模型支持（V4-Pro / V4-Flash）
- Skill 自定义安装与扩展（兼容 agentskills.io 开放标准）
- MCP 服务接入（多源连接，支持 Streamable HTTP / SSE / stdio）
- 插件扩展系统 + 工具自主创建
- IM 远程接入（飞书 / QQ / 微信）
- SubAgent 子代理并行调度
- 定时任务调度器 + 全局会话搜索

### v1.2.4 更新亮点
- 命令执行不再卡死，超时自动终结 + 管道继承兜底保护
- Token 效率深度优化：上下文稳态机制将活跃上下文锁定在十万级，千万 token 长会话每轮约 2 分钱
- MCP 安装后自动生效，SSE 重连修复，兼容更多 Streamable HTTP 服务
- 跨会话全量搜索强化 + 会话入口快速定位
- Windows 安装器权限提权 + 进程检测
- 对话成本 Agent 自追溯，实时 cache 命中率 / Token 消耗 / 费用

### 安装
- **taishen_setup_1.2.4.exe** — Windows 安装包（推荐）
- **taishen1.2.4免安装版.zip** — 解压即用免安装版

### 文件校验（SHA256）
| 文件 | SHA256 |
|------|--------|
| taishen_setup_1.2.4.exe | `A52BED7845726CA57D4C306D057D4AADFC4997ED851A0E70812C6475CC897937` |
| taishen1.2.4免安装版.zip | `E5646FD59D1288CE7C4FBA94676D0F0867277CB48D7753C409570CCA020543FE` |

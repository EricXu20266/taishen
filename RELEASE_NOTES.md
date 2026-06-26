## 🚀 泰深 v1.2.7 正式发布

专为 DeepSeek 深度调优的 AI 智能助手桌面客户端。macOS 平台正式适配，多供应商配置精细化管理，稳定性和体验全面提升。

### 核心功能
- DeepSeek V4 全模型支持（V4-Pro / V4-Flash）
- 多供应商支持（DeepSeek / OpenAI / Mimo 等自由切换）
- 视觉代理 Myeyes — 模型不支持多模态也能"看图"，IM 渠道全面打通
- FlexDog 动态模型引擎 — 对话中随时切换模型
- Commander 形态 — 全景能力重构，AI 自主规划、调度、验证一条龙
- HTML 高级预览器 + 元素批注系统 — 所见即所得，选中即标注
- 回收站系统 — 误删会话、Skill、子代理随时捞出，永不过期
- macOS 平台正式支持
- Skill 自定义安装与扩展（兼容 agentskills.io 开放标准）
- MCP 服务接入（多源连接，支持 Streamable HTTP / SSE / stdio）
- 插件扩展系统 + 工具自主创建
- IM 远程接入（飞书 / QQ / 微信），全面支持图片发送
- SubAgent 子代理并行调度
- 定时任务调度器 + 全局会话搜索

### v1.2.7 更新亮点
- 重大更新：macOS 适配全面完成！泰深可以运行在 macOS 上了
  - Windows 用户目录下的 .taishen 文件夹可直接拷贝到 macOS 用户目录，无痛迁移数据
  - 因 API Key 加密方法不同（DPAPI vs Keychain），需为 macOS 准备新的 API Key
- 多 Provider 配置选项重大升级：推理配置、百万上下文从全局下沉到 per-model 级别，不同 Provider、不同模型各自微调推理强度
- 修复了切换/删除 Provider 带来的一系列 bug
- UI 优化：添加了新的视觉元素和动效
- 修复了主页和项目首页无法直接 Ctrl+V 贴图的问题
- 修复了 write_pdf 遇到中文时无法生成 PDF 的问题
- 修复了 v1.2.6 中新上下文管理可能带来的冷启动思考块暴涨的 bug
- 修复了 L1 权限审批死锁问题，Agent 感知补齐，审批流程不打结
- 修复了 customModels 对象泄漏导致 React 渲染崩溃、MCP 编辑表单错位、粘贴图片路径异常等多个小问题

### 安装
- **taishen_setup_1.2.7.exe** — Windows 安装包（推荐）
- **taishen1.2.7免安装版.zip** — 解压即用免安装版
- **泰深-1.2.7.dmg** — macOS 安装包

### 文件校验（SHA256）
| 文件 | SHA256 |
|------|--------|
| taishen_setup_1.2.7.exe | `2E1F27E45A0270EE8DC2D71912FE169A3B06A93AD2E5C709FF88759B69964D59` |
| taishen1.2.7免安装版.zip | `F0C4FA7E99F3209022672BA52FAA412CB054EBC7D6C2CA0746956150A1C28810` |
| taishen-1.2.7.dmg | `06D85C5CB39D14E016C5B1A631393D41A1DC7F743E563FA38DCFDA0C5784E919` |

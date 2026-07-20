## 🚀 泰深 v1.3.7 正式发布

效率工具持续打磨：截图自检、浏览器扩展、批处理加速。同步发布[白皮书](WHITEPAPER.md)——《为 DeepSeek 而生的桌面 AI 工作台》。

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

### v1.3.7

- 添加了一个内置截图工具，现在泰深可以自我截图，如果你配置了myeyes，基本可以实现全自动识图、标注、修改流程。
- 内置浏览器现在支持安装 Chrome 扩展了，你常用的效率工具可以搬进泰深浏览器里用。
- 画布工具栏新增「打开文件夹」按钮，点一下直接打开画布绑定的文件所在目录，不用再去文件面板里翻找了。
- 批处理执行策略上线，对抗一步一停的工作流。
- 修复了 HTML 画布加载大文件时主进程假死的问题，现在打开再大的页面也不会卡住整个窗口。
- 修复了泰案追加模式下内容被覆盖的 Bug。
- 修复了峰谷计费开关Bug。
- 修复了批注文本框退格键冒泡拦截导致其他快捷键失效，以及 HTML 画布刷新按钮不灵光的问题。
- 修复了弹窗卡片不跟随消息流滚动、泰案按钮在无会话时点击无反应等几个小毛病。

### 安装
- **taishen_setup_1.3.7.exe** — Windows 安装包（推荐）
- **taishen_1.3.7免安装.zip** — 解压即用免安装版
- **taishen_1.3.7_macOS_arm64.dmg** — macOS Apple Silicon (M1-M4) 安装包

### 文件校验（SHA256）
| 文件 | SHA256 |
|------|--------|
| taishen_setup_1.3.7.exe | `CDB977AFEE0AAEB6F54374681DFA16A2C1AB10CBD2DAAFD449350F68AB93F3A4` |
| taishen_1.3.7免安装.zip | `6A5763858D1C5781323CC9A7B88426157602AEA06DB933E9BB8DADCF03583BAA` |
| taishen_1.3.7_macOS_arm64.dmg | `C5AB35E7E1EE4BA131802C208CF30A5255F5C6ED0060A79DECB159AE9F2BFE8A` |

---

📖 深入了解泰深的设计哲学与技术架构，请阅读[白皮书](WHITEPAPER.md)。

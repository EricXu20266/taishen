## 🚀 泰深 v1.3.0-beta 正式发布

B测更新，子代理经济学重构。coder子代理上线、Deep Research升级、IM消息推送、多项Bug修复。

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

### v1.3.0-beta

- B测更新：调整了子代理的使用逻辑，尤其是fork分身模式，原因是在1.2.9版本中配置了fork分身使用，开发者在实际测试中发现fork分身即使在使用flash模式下，也有点超出想像的计费了。
  - 经过多轮测试（包含独立子代理和fork分身），开发者得到了一个准确的结论：
    ###任何子代理都不会省钱。
  - 不管是独立子代理或是fork分身，使用中对比98%+缓存命中的主Agent，这些子代理工作消费很高，所以子代理唯一的作用就是：
    ###以token换取时间或是上下文空间。
- 针对以上发现，新增了一个内置 coder子代理，直接操作修改代码，直改不探索，全面优化了fork分身经济学与工作轮次。
- 内置插件 Deep Research 升级，一个全新的深度搜索插件，建议配合anysearch、firecrawl等搜索MCP一起使用，产出深度调研报告。
- 测试更新，IM 远程消息推送能力上线。任务完成后泰深会自动通知你的手机，飞书、QQ、微信三端同步，你可以在设置里面选择具体使用哪个IM渠道通知。
- 修复一个隐藏很深的协议 bug，该bug导致激活skill后正文没完全注入 system prompt，导致复杂类技能激活了跟没激活一样。
- 新增了一个基础环境配置引擎，泰深在某些任务中如遇到环境配置问题，会激活配置问卷咨询用户是否需要配置环境。
- 优化了记忆系统复盘功能。
- 加强了MCP连接稳定性大。
- 行为指导添加了需求补齐模式，现在你给泰深模糊需求时，它会有个基础评测模型进行判断。此点是将开发者蒸馏进去了！
- 补齐了LLM trace日志。
- 文件预览面板搜索功能上线。CSS Highlight API 高亮匹配词，逐个定位，翻长文不再靠肉眼扫描。
- 修复了非 DeepSeek LLM（GPT-4o 等）停止按钮失效的问题。
- 修复了跨会话弹窗互相卡死的死锁问题。以前多开几个会话同时弹窗就可能集体罢工，现在各弹各的，互不干扰。
- 修复了页面 reload 后弹窗丢失、会话死锁的连环问题。
- 修复了绿色版更新默认装到 C 盘的问题。
- 修复了会话内文件超链接异常的bug。

### 安装
- **taishen_setup_1.3.0-beta.exe** — Windows 安装包（推荐）
- **taishen_1.3.0-beta免安装.zip** — 解压即用免安装版
- **taishen_1.3.0-beta_macOS_arm64.dmg** — macOS Apple Silicon (M1-M4) 安装包

### 文件校验（SHA256）
| 文件 | SHA256 |
|------|--------|
| taishen_setup_1.3.0-beta.exe | `2883FB4D652ADC89005BE90F6C17E309C2CCCD318B416C972694FDCF52C95379` |
| taishen_1.3.0-beta免安装.zip | `2A161CE05C6DDDE1E4566EB92B4FA010F28A37B3C979BC2C67ED043E13BB1` |
| taishen_1.3.0-beta_macOS_arm64.dmg | `69CFD2F9DDBD5FD2FB3B25D359E53161EFF72F944CF5B4FD315AE56A6893EC87` |

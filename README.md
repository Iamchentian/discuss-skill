# Discuss Skill

一个完全自包含的结构化议题研讨技能，基于金字塔原理（SCQA 框架），支持本地、对话、飞书云端三种持久化方式。

## 特性

- **核心功能内置**：议题拆解（MECE）、深度追问、verdict 裁决均已内置，无需依赖其他技能
- **三种持久化模式**：本地文件 / 纯对话 / 飞书云端，按会话能力自动检测
- **verdict 质量裁决**：每个议题追问后给出 solid / needs-work / invalid 评级，强制对论据质量负责
- **硬性拆解上限**：递归深度 ≤4 层，子议题 ≤5 个，避免无限递归和信息过载
- **异常处理**：覆盖非法输入、云端失败、结论推翻、上下文超长等边界场景

## 快速开始

### 1. 安装

将 `SKILL.md` 及 `references/`、`assets/` 目录复制到你的智能体技能目录中。

### 2. 触发

使用以下任一触发词：
- `讨论` / `讨论下`
- `/discuss`
- `discuss this`

### 3. 使用示例

```
用户：/discuss 分析为什么最近项目延期严重

技能会自动：
1. 检测持久化模式（本地/对话/云端）
2. 按 MECE 拆解议题为 3-5 个子议题
3. 引导逐个讨论，深度追问后给出 verdict
4. 循环直至所有议题 ✅
5. 生成 SCQA 文档 + 落地规划
```

> 完整的三模式对话示例见 `references/` 目录。

## 文件结构

```
discuss-skill/
├── SKILL.md                              # 主技能文件（核心机制与流程）
├── README.md                             # 使用说明（本文件）
├── CHANGELOG.md                          # 版本变更记录
├── references/                           # 参考文档（供模型加载）
│   ├── local-mode-example.md             # 本地模式示例
│   ├── cloud-mode-example.md             # 飞书云端模式示例
│   ├── chat-mode-example.md              # 纯对话模式示例
│   └── verdict-examples.md              # verdict 三种裁决示例
└── assets/                               # 输出模板
    ├── notes-template.md                 # 讨论过程记录模板
    └── summary-template.md               # SCQA 汇总文档模板
```

## 核心机制（详见 SKILL.md）

完整的工作流程、持久化检测、verdict 系统、异常处理等内容均在 `SKILL.md` 中定义。这里仅做简要索引：

| 主题 | 说明 |
|------|------|
| **触发词** | `讨论` / `/discuss` / `discuss this` |
| **拆解规则** | MECE 检查，子议题 3-5 个，递归深度 ≤4 层 |
| **持久化模式** | 本地 / 对话 / 云端（飞书），默认对话模式兜底 |
| **verdict 裁决** | solid / needs-work / invalid，禁止跳过 |
| **SCQA 文档** | 背景-冲突-问题-解决方案 + 落地规划 + 风险应对 |

## 许可证

MIT License

## 贡献

欢迎提交 Issue 和 Pull Request！版本变更记录见 [CHANGELOG.md](./CHANGELOG.md)。

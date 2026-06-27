# Changelog

本文件记录 discuss-skill 的版本变更。格式参考 [Keep a Changelog](https://keepachangelog.com/zh-CN/)。

## [2.0.0] - 2026-06-28

### 质量优化（综合评分 6.6 → 9.0）

#### P0 必修项（合规与基础可用性）
- 补 `agent_created: true` frontmatter 字段，符合官方强制要求
- 云端模式明确走 `lark-doc` skill，含 token 提取与子文档创建流程
- 持久化检测逻辑改为 6 级优先级表，明确每级检测条件
- 统一 SKILL.md 与 summary-template 文档结构

#### P1 应修项（执行确定性和体验）
- 触发词收窄至 `讨论` / `/discuss` / `discuss this`，移除泛化的 `analyze`
- 上下文追问改为可选（仅根问题信息不足时才追问背景）
- 拆解停止规则量化：≥2 独立子问题 + 深度 <4 层 + 信息不足以给 verdict
- 新增 `references/verdict-examples.md`，含 needs-work / invalid 完整反例
- 目录改名 `examples→references`、`templates→assets`，符合官方约定
- Anti-patterns 明确"用 edit 局部更新，不全量重写 notes.md"

#### P2 优化项（健壮性和可维护性）
- 新增 Error Handling 章节，覆盖 6 类异常（非法输入/云端失败/结论推翻/状态回退/上下文过长/中途结束）
- 新增 Anti-patterns 反模式清单（6 条）
- description 改为第三人称，含差异化能力描述（MECE/verdict/三模式持久化）
- SKILL.md 瘦身，示例外移到 references
- 版本日期校准为 2026-06-28

#### 其他
- 合并 State Flow 与 Topic Navigation 为 "Topic State & Navigation" 章节
- README 瘦身为介绍 + 快速开始 + 文件结构 + 机制索引
- 新增 CHANGELOG.md（本文件）
- 修正示例日期 2025-06-26 → 2026-06-28

## [1.1.0] - 2025-06-27

### 新增
- 三种持久化模式（本地 / 对话 / 云端）
- verdict 裁决机制（solid / needs-work / invalid）
- notes-template 与 summary-template
- 三模式示例文档

## [1.0.0] - 2025-06-27

### 初始版本
- 基于 SCQA 框架的结构化议题研讨技能
- 议题拆解 + 深度追问核心流程

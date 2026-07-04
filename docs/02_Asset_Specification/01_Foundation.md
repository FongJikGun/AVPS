# =================================================================================
# AVPS（AI Visual Production Specification）
# 02_Asset_Specification.md
# Part A：Asset Foundation
#
# Version: 3.0.0
# Status: Stable
# Authority: Specification
# Priority: Highest
# Review: PASS
# Freeze: APPROVED
#
# Description:
# 定义 AVPS 所有资产（Asset）的共同规范。
# 本章节不定义任何具体资产，仅定义资产的基础规则、
# 数据结构、生命周期及治理原则。
# =================================================================================

# 1. Purpose

Asset Foundation 是整个 AVPS 的资产基础规范。

它回答以下问题：

- 什么是 Asset？
- 一个对象如何成为 Asset？
- 所有 Asset 必须遵循哪些共同规则？
- 所有 Asset 必须具备哪些基础结构？

Asset Foundation 不定义任何具体资产。

Character、Outfit、Scene、Prop、World、Configuration 等资产，
均必须遵循本规范。

---

# 2. Asset Philosophy

Asset 是 AVPS 的唯一真源（Single Source of Truth）。

任何视觉内容、镜头、Prompt、生成结果，
均不得成为新的设定来源。

资产负责保存设计。

Prompt 负责表达设计。

AI 负责执行设计。

因此：

Asset 永远位于整个 AVPS 的中心。

---

# 3. Asset Definition

在 AVPS 中，一个对象只有同时满足以下条件，
才能称为 Asset。

## AD-001 唯一身份（Identity）

必须拥有唯一 Asset ID。

Asset ID 在整个系统内不可重复。

---

## AD-002 可引用（Referenceable）

必须能够被其它模块引用。

例如：

- Configuration
- Shot Package
- Prompt Compiler

均应引用 Asset，
而不是复制 Asset 内容。

---

## AD-003 可版本化（Versioned）

所有 Asset 必须具有版本。

任何修改均应记录版本变化。

禁止覆盖历史版本。

---

## AD-004 可验证（Validatable）

Asset 必须能够进行一致性验证。

包括：

- 字段完整性
- 引用合法性
- 数据完整性
- 版本一致性

---

## AD-005 可追踪（Traceable）

Asset 的来源、修改历史、依赖关系必须可追踪。

任何生成结果都应能够回溯至对应 Asset。

---

## AD-006 可复用（Reusable）

Asset 应独立于具体项目流程。

同一 Asset 可以在多个 Shot、
多个 Configuration、
多个 Prompt 中复用。

---

## AD-007 明确类型

所有 Asset 必须声明唯一 Asset Type。

Asset Type 用于标识资产类别，
供 Validation、Compilation、Pipeline 等模块识别。

Asset Type 在资产生命周期内保持不变。

---

# 4. Asset Foundation Structure

所有 Asset 必须遵循统一结构。

```text
Asset
├── Header
├── Metadata
├── Content
├── Relationships
├── Status
├── Validation
└── Version
```

其中：

Header、Metadata、Relationships、Validation、Version
属于所有 Asset 共通结构。

Content
由具体资产自行定义。

---

# 5. Foundation Sections

## 5.1 Header

用于唯一标识 Asset。

必须包含：

- Asset ID
- Asset Type

Header 不保存业务内容。

Header 用于系统识别，不用于描述资产内容。



---

## 5.2 Metadata

用于描述 Asset 的基本信息。

建议至少包含：

- Name
- Description
- Tags
- Status
- Created Time
- Updated Time
- Owner

Metadata 不参与生成。

Owner 表示资产维护者。

Owner 不影响资产引用关系。

仅用于管理。

---

## 5.3 Content

Content 是 Asset 的业务主体。

不同 Asset 拥有不同 Content。

例如：

Character：

Identity

Appearance

Visual DNA

Outfit：

Structure

Modules

States

Scene：

Space

Lighting

Atmosphere

Asset Foundation 不规定 Content 字段。

由各 Asset Data Model 定义。

---

## 5.4 Relationships

定义 Asset 与其它 Asset 的引用关系。

Relationships 不保存资产内容。

只保存引用关系。

例如：

Character

↓

Default Outfit

↓

Default Components

↓

World

Relationships 必须引用 Asset ID。

禁止复制内容。

---

## 5.5 Validation

Validation 用于验证 Asset 是否合法。

包括：

- ID 是否存在
- 引用是否合法
- Version 是否一致
- Metadata 是否完整
- 必填字段是否缺失

Validation 不保存业务数据。

---

## 5.6 Version

Version 用于记录 Asset 的演进。

采用 Semantic Version。

例如：

1.0.0

↓

1.0.1

↓

1.1.0

↓

2.0.0

任何版本修改，
不得覆盖旧版本。

---

# 6. Asset Classification

AVPS 当前定义以下资产类别。

## Identity Assets

用于定义角色身份。

例如：

Character

---

## Visual Assets

用于定义视觉元素。

例如：

Outfit

Component

---

## Environment Assets

用于定义环境。

例如：

Scene

World

---

## Interactive Assets

用于定义交互对象。

例如：

Prop

---

## Configuration Assets

用于定义资产组合。

例如：

Configuration

Asset Foundation 仅定义分类。

具体结构由各 Asset Data Model 定义。

---

# 7. Asset Status

所有 Asset 统一采用以下生命周期状态。

Draft

↓

Review

↓

Approved

↓

Stable

↓

Deprecated

↓

Archived

状态仅表示资产生命周期。

不表示剧情状态。

---

# 8. Asset Principles

所有 Asset 必须遵循以下原则。

## AP-001

唯一身份（Unique Identity）

一个 Asset 对应一个唯一 ID。

---

## AP-002

唯一职责（Single Responsibility）

一个 Asset 仅负责一个领域。

不得承担多个职责。

---

## AP-003

引用优先（Reference First）

共享数据必须引用。

禁止复制。

---

## AP-004

组合优于复制（Composition over Duplication）

复杂对象应由多个 Asset 组合而成。

不得复制已有 Asset。

---

## AP-005

独立演进（Independent Evolution）

每个 Asset 可独立版本化。

修改 Outfit 不应影响 Character。

修改 Scene 不应影响 World。

---

# 9. Completion Criteria

一个 Asset 只有满足以下条件，
并且通过 Review 后，
才可进入 Stable。

□ 已拥有唯一 ID

□ 已定义 Metadata

□ 已完成 Content

□ 已建立 Relationships

□ 已完成 Validation

□ 已建立 Version

否则不得进入 Stable。

---

# 10. Scope

本章节仅定义：

Asset Foundation。

不定义：

- Character Data Model
- Outfit Data Model
- Component Data Model
- Scene Data Model
- Prop Data Model
- World Data Model
- Configuration Data Model

上述内容将在 Part B 中定义。

---

# 11. Summary

Asset Foundation 是整个 AVPS 的资产基础规范。

它不是一种 Asset。

它定义的是：

所有 Asset 必须共同遵循的数据结构、
生命周期、
治理规则及设计原则。

所有 Asset Data Model
必须符合本章节要求。

# =================================================================================
# End of Part A
# =================================================================================

# =================================================================================
# AVPS（AI Visual Production Specification）
# 00_Core_Principles.md
# Version: 3.0.0
# Status: Stable
# Authority: Constitution
# Priority: Highest
#
# Description:
# 定义 AVPS 的最高设计原则。
# 本文档属于整个规范的最高约束层，
# 所有后续 Specification 必须遵循本文档，
# 不允许任何模块违反 Core Principles。
# =================================================================================

# 0. Compliance Rules

所有 AVPS 文档必须遵守以下规则：
1. 不得违反 Core Principles。
2. 若与 Core Principles 冲突，以 Core Principles 为准。
3. 新增规范不得修改 Core Principles 的语义。
4. Core Principles 的修改只能通过 Major Version（如 V4.0.0）发布。
5. 若某项设计无法满足 Core Principles，应重新设计，而不是修改原则。

---

# 1. Purpose

AVPS（AI Visual Production Specification）
是一套用于 AI 视觉内容工业化生产的标准规范。

目标不是生成 Prompt。

目标是建立：

> 可复用（Reusable）
> 可维护（Maintainable）
> 可扩展（Scalable）
> 可编译（Compilable）
> 可版本化（Versioned）

的资产生产体系。

Prompt 只是最终产物之一。

---

# 2. Design Philosophy

AVPS 的核心思想：

> Design Once.
> Reference Everywhere.
> Generate Consistently.

中文：

> 一次设计，全局引用，稳定生成。

所有视觉内容，
必须先完成设计，
再进入生成阶段。

AI 的职责是执行设计，
不是重新设计。

---

# 3. Core Principles

## CP-000
### Specification Supremacy

实现（Implementation）必须遵循规范（Specification）。

任何 AI 模型、工具或平台的限制，
都不得成为修改规范的理由。

当实现无法满足规范时：

应调整实现，
而不是降低规范要求。

---

## CP-001
### Single Source of Truth（SSOT）

任何信息只能存在一个唯一来源。

例如：

Character Name

只能定义一次。

以后：

Shot

Prompt

Video

全部引用。

禁止复制。

---

## CP-002
### Everything Is an Asset

所有可管理对象，
都必须资产化。

包括但不限于：

- Character
- Outfit
- Component
- Weapon
- Scene
- Prop
- Configuration
- Shot
- Prompt Template
- World Bible

资产必须拥有：

- ID
- Metadata
- Version
- Dependency

---

## CP-003
### Everything Is Referenced

所有模块之间：

只允许引用。

禁止复制资产内容。

例如：

正确：

Character ID：

CH-001

错误：

重新写：

黑发、
蓝眼、
皮甲……

统一引用：

CH-001

---

## CP-004
### Design Before Generation

所有生成行为：

必须建立在资产设计完成之后。

流程固定：

Design

↓

Compile

↓

Generate

↓

Post Process

禁止：

边生成边设计。

---

## CP-005
### Prompt Is Compiled

Prompt：

不是创作来源。

Prompt：

只是 Compiler 的输出结果。

Prompt 可以删除。

资产不能删除。

Prompt 可以重新生成。

资产不能重新推断。

---

## CP-006
### AI Executes. Human Defines.

人类负责：

定义规则。

AI负责：

执行规则。

AI不得：

自行新增：

- 世界观
- 人物
- 道具
- 场景
- 设定

若资产缺失：

必须返回：

Need More Information。

不得推断。

---

## CP-007
### Identity Is Immutable

角色身份：

永远稳定。

例如：

CH-001

永远代表：

林寻。

不会因为：

换衣服、

戴面罩、

拿武器、

进入战斗，

变成新的角色。

Identity：

不可变。

---

## CP-008
### Configuration Is Dynamic

角色状态：

来自 Configuration。

例如：

CH-001

可以绑定：

CFG-001

普通形态

↓

CFG-002

战斗形态

↓

CFG-003

觉醒形态

Configuration：

允许变化。

Identity：

不允许变化。

---

## CP-009
### Modularity First

任何满足以下条件的对象：

必须拆分为独立资产。

满足任意一项：

✔ 可替换

✔ 可复用

✔ 可动画

✔ 可升级

✔ 可损坏

✔ 可单独控制

例如：

服装

武器

面罩

披风

背包

机械臂

护肩

全部属于：

Module。

---

## CP-010
### State Is Independent

状态：

不是资产。

状态：

附属于资产。

例如：

Character：

不会：

Damaged。

而是：

Outfit：

Damaged。

Weapon：

Broken。

Mask：

Activated。

Scene：

Destroyed。

状态永远属于：

Asset Instance。

---

## CP-011
### Version Everything

所有资产：

必须版本化。

例如：

Character

v1.0.0

↓

v1.1.0

↓

v2.0.0

禁止：

覆盖旧版本。

---

## CP-012
### Backward Compatibility

任何规范升级：

尽量保持：

向后兼容。

若存在：

Breaking Change

必须：

Major Version。

---

## CP-013
### Determinism（确定性）

相同输入，应尽可能产生相同输出。

也就是说：

- 相同 Asset

- 相同 Configuration

- 相同 World Bible

- 相同 Shot

编译出来的 Prompt 应保持一致，确保生产流程可复现。

---

## CP-014
### Asset Independence（资产独立性）

每个资产都应该可以独立维护、独立版本化、独立测试。

例如：

- 修改武器，不影响角色。

- 修改服装，不影响世界观。

- 修改场景，不影响人物。

这也是我们之前坚持拆分 Character、Outfit、Mask、Weapon 的根本原因。

---

## CP-015
### Model Agnostic（模型无关性）

AVPS 不依赖任何特定 AI 模型。

无论是 ChatGPT、Gemini、Claude、Imagen、Veo、Midjourney，还是未来的新模型，都只是 AVPS 的执行器（Execution Engine）。

因此，规范永远高于模型，实现可以更换，规范保持稳定。

---

# 4. Asset Philosophy

资产：

不是图片。

不是 Prompt。

资产：

是整个系统的唯一数据源。

一个资产必须满足：

Reusable

Composable

Versioned

Traceable

Referenceable

否则：

不能称为：

Asset。

---

# 5. Dependency Rules

依赖关系：

只能单向。

推荐：

World Bible

↓

Character

↓

Outfit

↓

Component

↓

Configuration

↓

Shot

↓

Prompt

↓

Image

↓

Video

禁止：

反向引用。

例如：

Character

引用：

Prompt。

属于错误设计。

---

# 6. Separation of Responsibility

不同模块：

职责必须唯一。

Character：

负责：

身份。

Outfit：

负责：

穿着。

Component：

负责：

外挂组件。

Configuration：

负责：

组合。

Shot：

负责：

镜头。

Prompt：

负责：

编译输出。

Generation：

负责：

执行。

不得交叉。

---

# 7. Source of Change

任何修改：

必须先修改资产。

禁止：

直接修改 Prompt。

正确流程：

Asset

↓

Compiler

↓

Prompt

↓

Generation

而不是：

Prompt

↓

Generation

↓

再回头改资产。

---

# 8. Change Management

新增任何功能：

必须遵循：

RFC

↓

Review

↓

Approve

↓

Specification Update

↓

Version Update

↓

Release

不得：

直接修改正式规范。

---

# 9. Definition of Completion

一个模块只有满足以下条件，

才算完成。

□ 有唯一职责

□ 有唯一输入

□ 有唯一输出

□ 可独立版本管理

□ 可独立测试

□ 可独立替换

否则：

属于未完成设计。

---

# 10. Final Principle

AVPS 的唯一目标：

不是生成更多图片。

而是建立：

可持续演进的 AI 视觉资产生产体系。

Prompt 会变化。

模型会变化。

工具会变化。

资产不会。

因此：

资产，

永远是整个 AVPS 的核心。

# =================================================================================
# End of Document
# =================================================================================
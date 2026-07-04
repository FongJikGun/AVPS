# 90_Design_Decisions

Version: 2.0.0

Status: Stable

---

# 1. Purpose

本文件用于记录 AVPS（AI Visual Production System）的重要设计决策（Design Decisions）。

Design Decision 用于说明：

- 为什么采用当前设计。
- 为什么拒绝其他设计方案。
- 决策所依据的设计原则。
- 决策所带来的架构影响。

本文件属于 **Architecture Decision Record（ADR）**。

本文件**不定义新的规范（Specification）**。

所有正式规范仍以对应 Specification 为唯一依据（Single Source of Truth）。

---

# 2. Scope

本文件用于记录已经完成 Review 并获得确认的重要设计决策，包括但不限于：

- Core Architecture Decisions
- Asset Design Decisions
- Data Model Design Decisions
- Cross-Specification Decisions

本文件不记录：

- Draft Ideas
- Temporary Discussions
- Review Comments
- Implementation Details
- Changelog

---

# 3. Decision Lifecycle

所有 Design Decision 应遵循统一生命周期。

```text
Proposed
    │
    ▼
Review
    │
    ▼
Approved
    │
    ▼
Stable
```

各阶段定义如下：

| Status | Description |
|---------|-------------|
| Proposed | 已提出设计方案，尚未进入正式 Review。 |
| Review | 正在进行 Review，尚未完成决策。 |
| Approved | 设计决策已确认，但对应 Specification 尚未完成 Freeze。 |
| Stable | 对应 Specification 已完成 Freeze，该 Decision 成为长期有效决策。 |
| Deprecated | 已废弃，不建议继续采用。 |
| Superseded | 已被新的 Design Decision 取代。 |

Design Decision 不应直接标记为 **Stable**。

只有当对应 Specification 完成：

- Review PASS
- Freeze Approved

后，

Design Decision 才可升级为 **Stable**。

---

# 4. Decision Template

所有 Design Decision 必须采用统一格式。

```md
# DD-XXX Decision Title

## Status

Proposed | Review | Approved | Stable | Deprecated | Superseded

---

## Related Specification

- 00_Core_Principles.md
- 01_Architecture.md
- ...

---

## Related Principles

- CP-XXX
- AP-XXX（如适用）

---

## Decision

说明最终设计决策。

---

## Rationale

说明采用此设计的原因。

---

## Alternatives Considered

### Alternative A

说明方案。

**Decision：Rejected**

### Alternative B

说明方案。

**Decision：Rejected**

---

## Consequences

说明采用该设计后的影响。

---

## Notes

补充说明（可选）。
```

---

# 5. Decision Index

| ID | Title | Status | Related Specification |
|----|-------|--------|----------------------|
| DD-001 | Character Asset Responsibility | Stable | 01_Architecture / 02_Data_Models |
| DD-002 | Character References as Optional Field | Stable | 02_Data_Models |
| DD-003 | Required / Optional Field Classification | Stable | 02_Data_Models |
| DD-004 | Outfit Asset Responsibility | Approved | 01_Architecture / 02_Data_Models |

---

# 6. Decision Records

以下章节记录所有已确认的 Design Decisions。

Decision 按 Decision ID 升序排列。

新增 Decision 时：

- 不修改既有 Decision ID。
- 不重新排序。
- 保持历史可追溯性。
- 若 Design Decision 被取代，应更新其 Status 为 **Superseded**，并新增新的 Decision，而不是覆盖原有内容。

---

# DD-001 Character Asset Responsibility

## Status

Stable

---

## Related Specification

- 00_Core_Principles.md
- 01_Architecture.md
- 02_Asset_Specification_02_Data_Models.md

---

## Related Principles

- Everything Is an Asset
- Identity Is Immutable
- Single Responsibility
- Asset-Centric Architecture

---

## Decision

Character Asset 为独立 Asset。

Character 仅负责角色身份（Identity）及其长期稳定属性。

Character 不承担：

- Outfit
- Component Definition
- Configuration
- Runtime State
- Scene
- Shot
- Prompt

Character 与其他 Asset 之间仅通过 Reference 建立关联。

---

## Rationale

Character 是整个视觉资产体系中的 Identity Asset。

若 Character 同时承担 Outfit、Configuration 或 Runtime State 等职责，将导致：

- Asset 职责混乱
- 耦合增加
- 可复用性下降
- Version 管理复杂化

保持 Character 专注于 Identity，可使其他 Asset 独立演进，并符合 Asset-Centric Architecture。

---

## Alternatives Considered

### Alternative A：Character 包含 Outfit

Character 直接保存 Outfit 数据。

**Decision：Rejected**

原因：

- Character 与 Outfit 高度耦合。
- Outfit 无法独立版本管理。
- 不利于 Outfit 复用。

---

### Alternative B：Character 包含 Runtime State

Character 同时保存当前状态。

**Decision：Rejected**

原因：

- 混淆 Canonical Data 与 Runtime Data。
- 违反 Identity Is Immutable。
- Character 将承担运行时职责。

---

## Consequences

采用本决策后：

- Character 成为独立 Identity Asset。
- Outfit、Configuration、State 均保持独立。
- 各 Asset 通过 Reference 建立关联。
- Character 生命周期独立于其他 Asset。

---

## Notes

本 Decision 为 Character Data Model 的核心设计原则。

未来所有 Character 相关 Specification 均应遵循本决策。

---

# DD-002 Character References as Optional Field

## Status

Stable

---

## Related Specification

- 02_Asset_Specification_02_Data_Models.md

---

## Related Principles

- Everything Is Referenced
- Asset Independence
- Progressive Asset Construction

---

## Decision

Character References 定义为 Optional Field。

Character 可以在没有任何 Reference 的情况下独立成立。

当 Character References 存在时，应仅保存 Canonical Reference。

---

## Rationale

Character 的成立不应依赖其他 Asset。

若 Character References 定义为 Required，将导致：

- Asset 创建顺序受到限制。
- Character 无法独立建立。
- 增加跨 Asset 耦合。

Character 应先建立 Identity，再逐步建立 Canonical Relationship。

---

## Alternatives Considered

### Alternative A：Character References 为 Required

Character 建立时必须引用其他 Asset。

**Decision：Rejected**

原因：

- 增加创建顺序依赖。
- Character 无法独立存在。
- 不符合 Asset Independence。

---

### Alternative B：Character References 保存 Runtime Reference

Character 保存运行时引用。

**Decision：Rejected**

原因：

- Runtime Data 不属于 Character。
- 混淆 Canonical Relationship 与 Runtime Configuration。

---

## Consequences

采用本决策后：

- Character 可单独创建。
- Character 可逐步补充 Canonical Relationship。
- Character References 成为可扩展能力，而非成立条件。
- Data Model 的 Required / Optional 分类更加一致。

---

## Notes

本 Decision 同时确立：

Character References 的职责为保存长期稳定（Canonical）的 Asset Reference，而非运行时引用。

---

# DD-003 Required / Optional Field Classification

## Status

Stable

---

## Related Specification

- 02_Asset_Specification_02_Data_Models.md
- 99_Review_Checklist.md

---

## Related Principles

- Design Before Generation
- Single Source of Truth
- Validation Consistency

---

## Decision

所有 Asset Data Model 必须将字段划分为以下两类：

- Required Fields
- Optional Fields

字段分类必须依据 **Asset 的核心职责（Core Responsibility）** 进行判断，而不是依据项目需求、实现方式或使用频率。

统一判定原则如下：

> 如果删除该字段，Asset 是否仍然成立？

- 若答案为 **否**，则该字段应定义为 **Required Field**。
- 若答案为 **是**，仅能力或信息减少，则该字段应定义为 **Optional Field**。

---

## Rationale

建立统一的字段分类原则，可以：

- 保持所有 Data Model 一致性。
- 降低不同 Asset 间的设计差异。
- 建立统一 Validation 标准。
- 避免因项目需求而错误提升字段等级。

字段分类应反映 Asset 本质，而不是项目实现。

---

## Alternatives Considered

### Alternative A：依据项目需求决定 Required

某些项目需要时定义为 Required。

**Decision：Rejected**

原因：

- Required 标准因项目而改变。
- Data Model 无法保持稳定。
- Validation 标准不统一。

---

### Alternative B：依据使用频率决定 Required

经常使用的字段定义为 Required。

**Decision：Rejected**

原因：

- 使用频率并不代表 Asset 成立条件。
- 容易造成职责混乱。
- 不符合 Core Responsibility 原则。

---

## Consequences

采用本决策后：

- 所有 Asset Data Model 使用统一分类标准。
- Character、Outfit、Scene、World 等 Data Model 保持一致。
- Required / Optional Review 可以统一执行。
- Validation Fail 的判定依据保持一致。

---

## Notes

本 Decision 为所有 Asset Data Model 的统一设计原则。

后续新增任何 Data Model 均应遵循本 Decision。

---

# DD-004 Outfit Asset Responsibility

## Status

Approved

---

## Related Specification

- 00_Core_Principles.md
- 01_Architecture.md
- 02_Asset_Specification_02_Data_Models.md

---

## Related Principles

- Everything Is an Asset
- Everything Is Referenced
- Single Responsibility
- Asset-Centric Architecture
- Modularity First

---

## Decision

Outfit Asset 为独立 Asset。

Outfit 仅负责角色的可替换视觉层（Replaceable Visual Layer）。

Outfit 不负责：

- Character Identity
- Runtime Configuration
- Runtime State
- Scene
- Shot

Outfit 不属于 Character 的内部组成。

Character 与 Outfit 应保持独立，并通过 Reference 建立关联。

---

## Rationale

将 Outfit 设计为独立 Asset，可以：

- 保持 Single Responsibility。
- 支持多个 Outfit 复用同一个 Character。
- 支持 Outfit 独立版本管理。
- 降低 Character 与 Outfit 的耦合。
- 符合 Asset-Centric Architecture。
- 提高 Asset 的可组合性与可复用性。

---

## Alternatives Considered

### Alternative A：Outfit 作为 Character 的内部结构

Character 直接保存 Outfit 数据。

**Decision：Rejected**

原因：

- Character 职责扩大。
- Outfit 无法独立管理。
- 不利于资产复用。
- Character 修改频率增加。

---

### Alternative B：Outfit 属于 Configuration

Configuration 保存 Outfit 定义。

**Decision：Rejected**

原因：

- Outfit 成为运行时组合的一部分。
- 无法表达长期稳定（Canonical）的 Outfit。
- 混淆 Asset 与 Composition 的职责。

---

## Consequences

采用本决策后：

- Character 负责 Identity。
- Outfit 负责可替换视觉层。
- Configuration 负责组合 Character、Outfit 及其他 Asset。
- State 负责运行时变化。

Asset 依赖关系如下：

```text
Character
     │
     ▼
Outfit

Configuration
     │
     ├── Character
     ├── Outfit
     └── Other Assets

State
     ▼
Runtime Changes
```

各 Asset 保持独立。

所有关联均采用 Reference。

不得形成循环依赖。

---

## Notes

当前 Status 为 **Approved**。

待 **Chapter 5：Outfit Data Model** 完成：

- Review PASS
- Freeze Approved

后，

本 Decision 应更新为：

```text
Status

Stable
```


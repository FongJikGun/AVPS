# Specification Pattern

## Purpose

本规范定义 AVPS 所有 Specification 的统一组织方式。

所有 Specification 应围绕一个 Core Object 展开。

不得按功能模块随意组织章节。

---

## Core Object Pattern

一份 Specification 应对应一个 Core Object。

例如：

| Specification | Core Object |
|--------------|-------------|
| Foundation | Asset Foundation |
| Data Models | Asset Data Model |
| Relationships | Relationship |
| Lifecycle | Asset Lifecycle |
| Validation | Asset Validation |
| Governance | Asset Governance |

---

## Common Chapter Pattern

所有 Specification 应采用统一章节结构：

1. Purpose
2. Philosophy
3. Structure
4. Core Components / Types
5. Rules
6. Constraints
7. Validation
8. Lifecycle
9. Governance
10. Extension
11. Cross Specification References
12. Summary

允许根据 Core Object 调整章节名称，

但整体组织方式应保持一致。

---

## Design Principles

所有 Specification：

- 保持 Single Responsibility。
- 围绕一个 Core Object。
- 不重复其他 Specification。
- 通过 Cross Specification References 建立联系。
- 保持长期稳定（Canonical）。

---

## Specification Dependencies

Specification 应建立明确的依赖关系。

下层 Specification 可以引用上层 Specification。

上层 Specification 不应依赖下层 Specification。

推荐依赖方向：

Core Principles
        ↓
Architecture
        ↓
Specification Patterns
        ↓
Foundation
        ↓
Data Models
        ↓
Relationships
        ↓
Lifecycle
        ↓
Validation
        ↓
Governance

不得形成循环依赖。

---

## Reference Baseline

每个 Specification 的开发周期应建立固定的 Reference Baseline。

Reference Baseline 由所有已 Freeze 的 Specification 组成。

Reference Baseline 是当前开发周期唯一的 Source of Truth。

Working Specification 应符合全部 Reference Baseline。

Reference Baseline 默认不可修改。

如需修改，应作为下一版本（Version Upgrade）处理。

---

## Review Workflow

所有 Specification 应遵循统一开发流程：

Reference Baseline
        ↓
Read Baseline
        ↓
Read Working Specification
        ↓
Consistency Review
        ↓
Chapter Development
        ↓
Chapter Review
        ↓
Final Review
        ↓
Freeze

Review 期间：

- 优先保证与 Baseline 一致。
- 不重复定义已有 Specification。
- 所有修改建议仅针对 Working Specification。
- Freeze 后，Working Specification 将加入下一轮 Reference Baseline。
# =================================================================================
# AVPS（AI Visual Production Specification）
# 99_Review_Checklist.md
#
# Version : 3.0.0
# Status  : Stable
# Authority : Governance
# Priority : Highest
#
# Description:
# 定义 AVPS 所有规范文档（Specification）的统一 Review 标准。
# 所有 Specification 在进入 Stable 前，
# 必须通过本 Checklist。
# =================================================================================

# 1. Purpose

本规范用于统一 AVPS 所有 Specification 的 Review 流程。

任何 Specification：

- Core Principles
- Architecture
- Asset Specification
- Pipeline
- Prompt Compiler
- Shot Package
- Generation
- Post Production

均必须遵循本 Checklist。

Review 的目的不是检查文笔。

Review 的目的是验证：

该 Specification 是否已经成为可长期维护的稳定规范。

---

# 2. Review Principles

所有 Review 必须遵循以下原则。

## RP-001

Review Specification。

不 Review 实例数据。

---

## RP-002

Review Structure。

不 Review 风格。

---

## RP-003

Review Consistency。

不 Review 实现方式。

---

## RP-004

Review Boundary。

确保职责清晰。

不得跨层。

---

## RP-005

Freeze Only When Stable。

未通过 Review 的 Specification
不得进入 Stable。

---

## RP-006

Review Canonical Responsibility。

确保每个 Specification 仅拥有唯一 Canonical Responsibility。

Specification 之间应通过 Canonical Reference 建立协作关系。

不得：

- 重复定义其他 Specification。
- 承担其他 Specification 的职责。
- 与其他 Specification 发生职责重叠。

Review 应验证整个 Specification System 的职责边界，而不仅限于当前文档。

---

# 3. Universal Review Checklist

所有 Specification 必须完成以下 Review。

---

## Review 1：Responsibility（职责）

确认：

该文档是否回答了：

> "我负责什么？"

检查项：

□ 是否定义自身职责

□ 是否没有承担其它模块职责

□ 是否没有职责重叠

□ 是否符合 Single Responsibility Principle

Review Result：

PASS / FAIL

---

## Review 2：Architecture Consistency（架构一致性）

确认：

是否符合：

- 00_Core_Principles.md
- 01_Architecture.md

检查项：

□ 是否符合 SSOT

□ 是否符合 Reference First

□ 是否符合 Design Before Generation

□ 是否符合 Prompt Is Compiled

□ 是否符合 AI Executes

□ 是否符合 Modularity First

Review Result：

PASS / FAIL

---

## Review 3：Boundary（边界）

确认：

是否进入了下一层职责。

检查项：

□ 是否提前定义下一层内容

□ 是否修改上一层定义

□ 是否跨层设计

□ 是否出现重复定义

Review Result：

PASS / FAIL

---

## Review 4：Completeness（完整性）

确认：

当前 Scope 是否完整。

检查项：

□ 是否覆盖当前模块全部职责

□ 是否没有遗漏关键结构

□ 是否没有缺失必须章节

□ 是否没有未定义核心概念

Review Result：

PASS / FAIL

---

## Review 5：Consistency（内部一致性）

确认：

文档内部是否一致。

检查项：

□ 名称是否统一

□ Terminology 是否统一

□ 命名规则是否统一

□ 数据结构是否统一

□ 编号是否连续

Review Result：

PASS / FAIL

---

## Review 6：Extensibility（可扩展性）

确认：

未来新增内容是否无需推翻现有设计。

检查项：

□ 是否支持新增模块

□ 是否支持新增 Asset

□ 是否支持新增 Pipeline

□ 是否支持未来版本升级

Review Result：

PASS / FAIL

---

## Review 7：Dependency（依赖关系）

确认：

依赖是否正确。

检查项：

□ 是否依赖上层

□ 是否没有反向依赖

□ 是否没有循环依赖

□ 是否没有非法引用

Review Result：

PASS / FAIL

---

## Review 8：Maintainability（可维护性）

确认：

未来维护成本是否可接受。

检查项：

□ 是否容易扩展

□ 是否容易 Review

□ 是否容易修改

□ 是否容易版本管理

Review Result：

PASS / FAIL

---

---

## Review 9：Cross-Specification Responsibility（跨规范职责）

确认：

当前 Specification 是否与其他 Canonical Specifications 保持清晰职责边界。

检查项：

□ 是否仅负责自身 Canonical Responsibility

□ 是否没有重新定义其他 Specification

□ 是否没有承担其他 Specification 的职责

□ 是否没有与其他 Specification 发生职责重叠

□ 是否通过 Canonical Reference 引用其他 Specification

□ 是否符合 Single Responsibility Principle

Review Result：

PASS / FAIL

---

# 4. Required / Optional Review

本章节适用于所有 Asset Data Model。

用于验证字段分类（Required / Optional）是否合理。

字段分类错误会导致：

- Asset 职责混乱
- Data Model 耦合增加
- Validation 标准不一致

因此，

所有 Data Model 在 Freeze 前，

必须完成以下检查。

Review 时，应依据
《02_Asset_Specification_02_Data_Models》
3.4.2《字段分类原则》进行检查。

---

## Review 1：Required Fields 是否合理

确认：

所有 Required Fields 是否真正属于 Asset 成立所必需。

检查项：

□ 缺少该字段，Asset 是否无法成立？

□ 是否属于 Asset 的身份（Identity）？

□ 是否属于 Asset 的核心职责（Core Responsibility）？

□ 是否不是项目需求导致的必需字段？

若以上任一项为否，

应重新评估是否应改为 Optional。

Review Result：

PASS / FAIL

---

## Review 2：Optional Fields 是否合理

确认：

所有 Optional Fields 是否不会影响 Asset 的合法性。

检查项：

□ 缺少该字段，Asset 是否仍然合法？

□ 是否仅影响能力、信息丰富度或项目需求？

□ 是否允许在生命周期中逐步补充？

□ 是否未承担 Required Fields 的职责？

Review Result：

PASS / FAIL

---

## Review 3：职责边界是否正确

确认：

字段是否属于当前 Asset。

检查项：

□ 是否没有属于其他 Asset 的字段？

□ 是否没有 Runtime Data？

□ 是否没有 State Data？

□ 是否没有 Configuration Data？

□ 是否没有跨模块职责？

Review Result：

PASS / FAIL

---

## Review 4：Foundation 是否被重复定义

确认：

Data Model 是否仅扩展自身 Content。

检查项：

□ 是否没有重新定义 Foundation 字段？

□ 是否没有覆盖 Metadata？

□ 是否没有覆盖 Version？

□ 是否没有覆盖 Validation？

□ 是否没有覆盖 Relationships？

Review Result：

PASS / FAIL

---

# 5. Specification Review Matrix

每份 Specification 必须完成以下矩阵检查。

| Review Item | PASS | FAIL | N/A |
|-------------|:----:|:----:|:---:|
| Responsibility | □ | □ | □ |
| Architecture Consistency | □ | □ | □ |
| Boundary | □ | □ | □ |
| Completeness | □ | □ | □ |
| Internal Consistency | □ | □ | □ |
| Required / Optional | □ | □ | □ |
| Extensibility | □ | □ | □ |
| Dependency | □ | □ | □ |
| Maintainability | □ | □ | □ |
| Cross-Specification Responsibility | □ | □ | □ |

全部 PASS 方可进入 Freeze。

---

# 6. Freeze Criteria

Specification 必须满足：

□ 所有 Mandatory Review PASS

□ 无重大架构问题

□ 无职责冲突

□ 无跨 Specification 职责重叠

□ 无边界冲突

□ 无重复定义

□ 无循环依赖

□ 支持未来扩展

满足以上条件后：

```text
Status : Stable

Review : PASS

Freeze : Approved
```

---

# 7. Review Output Standard

Review 结果必须统一输出。

```text
Specification:
<Specification Name>

Version:
x.x.x

Review Date:
YYYY-MM-DD

Reviewer:
<Reviewer>

Result:
PASS / FAIL

Summary:

Architecture:
PASS / FAIL

Boundary:
PASS / FAIL

Completeness:
PASS / FAIL

Consistency:
PASS / FAIL

Extensibility:
PASS / FAIL

Dependency:
PASS / FAIL

Maintainability:
PASS / FAIL

Cross-Specification Responsibility:
PASS / FAIL

Freeze:
Approved / Rejected
```

---

# 8. Review Severity

所有问题统一分级。

## P0（Critical）

影响：

架构正确性。

必须修复。

禁止 Freeze。

例如：

- 架构冲突
- 职责冲突
- 循环依赖
- SSOT 冲突

---

## P1（Major）

影响：

规范完整性。

建议修复后 Freeze。

例如：

- 章节遗漏
- 命名不一致
- 数据结构冲突

---

## P2（Minor）

影响：

表达一致性。

可在下一版本修复。

例如：

- 描述优化
- 示例调整
- 排版统一

---

# 9. Review Workflow

所有 Specification 必须遵循统一流程。

```text
Draft
    │
    ▼
Self Review
    │
    ▼
Architecture Review
    │
    ▼
Issue Fix
    │
    ▼
Final Review
    │
    ▼
PASS
    │
    ▼
Freeze
    │
    ▼
Stable
```

未完成 Final Review：

不得进入 Stable。

---

# 10. Governance Rules

Review 通过后：

仅允许：

- Bug Fix
- Clarification
- Editorial Update

禁止：

- 修改架构
- 修改职责
- 修改 Scope

如需修改：

必须升级 Major Version。

---

# 11. Summary

本 Checklist 是 AVPS 所有 Specification 的统一 Review 标准。

所有规范文档必须：

- 使用统一 Review 流程
- 使用统一 Severity 分级
- 使用统一 Freeze 标准
- 使用统一 Review 输出格式

Review 的目标不是追求"没有任何修改意见"，

而是确认：

> **该 Specification 已经具备长期稳定、可维护、可扩展的能力。**

# =================================================================================
# END OF FILE
# 99_Review_Checklist.md
# =================================================================================
# 96. Baseline Manifest

Version

1.0.0

Status

Draft

Authority

Governance

---

# 1. Purpose

## 1.1 Overview

Baseline Manifest 定义当前 AVPS Frozen Baseline 的正式发布记录（Release Manifest）。

Manifest 用于声明当前 Frozen Baseline 所包含的 Canonical Specification 及其对应 Version。

Manifest 不定义：

- Specification Structure
- Canonical Responsibility
- High-Level Dependency
- Review Process
- Freeze Workflow
- Specification Content

上述内容应分别由：

- Canonical Specification Registry
- 对应 Canonical Specification
- Review Checklist

负责定义。

---

## 1.2 Objectives

Baseline Manifest 应确保：

- Baseline Release 唯一。
- Baseline Version 可追踪。
- Included Specification 可验证。
- Released Version 可验证。
- Frozen Baseline 可重建。

---

## 1.3 Scope

Manifest 管理：

- Baseline Version
- Release Information
- Included Specifications
- Released Specification Version

Manifest 不管理：

- Specification Structure
- Canonical Responsibility
- High-Level Dependency
- Review
- Freeze
- Specification Content

---

# 2. Manifest Principles

## 2.1 Single Manifest

每一个 Frozen Baseline 应对应唯一 Manifest。

Manifest 应作为该 Baseline 的唯一发布记录。

---

## 2.2 Release Authority

所有 Frozen Baseline Release 应以 Manifest 为准。

Manifest 应作为 Release Information 的唯一权威来源。

---

## 2.3 Baseline Integrity

Manifest 中包含的所有 Specification：

- 应存在于 Canonical Specification Registry。
- 應屬於同一 Frozen Baseline。
- 應具有唯一 Released Version。

---

## 2.4 Version Consistency

Manifest 中引用的所有 Specification Version 應保持一致。

不得：

- 混用不同 Baseline 的 Version。
- 引用不存在的 Version。

---

## 2.5 Reference First

Manifest 應遵循 Reference First Principle。

Manifest 不應重複定義 Registry 或 Canonical Specification 已定義的資訊。

---

# 3. Baseline Information

Baseline Version

3.0.0

Baseline Type

Frozen Baseline

Release Status

Stable

Release Date

YYYY-MM-DD

Released By

Governance

---

# 4. Included Specifications

Manifest 應列出當前 Frozen Baseline 所包含的 Canonical Specification。

| Specification | Released Version |
|---------------|------------------|
| 00_Core_Principles | 3.0.0 |
| 01_Architecture | 3.0.0 |
| 02_Asset_Specification_01_Foundation | 3.0.0 |
| 02_Asset_Specification_02_Data_Models | 3.0.0 |
| 02_Asset_Specification_03_Relationships | 3.0.0 |
| 02_Asset_Specification_04_Lifecycle | 3.0.0 |
| 02_Asset_Specification_05_Validation | 3.0.0 |
| 02_Asset_Specification_06_Governance | 3.0.0 |
| 90_Design_Decisions | 2.0.0 |
| 95_Canonical_Specification_Registry | 1.0.0 |
| 99_Review_Checklist | 3.1.0 |
| 99_Specification_Patterns | 3.0.0 |

> **说明**
>
> Manifest 仅记录已正式纳入当前 Frozen Baseline 的 Specification。
>
> Draft、Reviewing 或尚未完成 Freeze 的 Specification 不应出现在 Manifest 中。

---

# 5. Manifest Rules

## 5.1 Included Specification

Included Specification：

- 應存在於 Canonical Specification Registry。
- 應完成 Freeze。
- 應屬於當前 Frozen Baseline。
- 應具有正式 Released Version。

---

## 5.2 Version Integrity

每個 Included Specification：

- 應具有唯一 Released Version。
- 應屬於當前 Baseline Version。

不得：

- 缺失 Version。
- 重複 Version。
- 混用不同 Baseline Version。

---

## 5.3 Manifest Consistency

Manifest 應保持：

- Baseline Consistency
- Version Consistency
- Release Consistency

---

# 6. Manifest Update

Manifest 僅應於以下情況更新：

- 發布新的 Frozen Baseline。
- 新增 Included Specification。
- 移除 Included Specification。
- Included Specification Version 更新。

Manifest 更新不得修改：

- Registry Structure。
- Canonical Responsibility。
- High-Level Dependency。

---

# 7. Relationship with Registry

Canonical Specification Registry 定義：

- Canonical Specifications
- Canonical Responsibilities
- High-Level Dependencies

Baseline Manifest 定義：

- Baseline Release
- Included Specifications
- Released Versions

Registry 定義系統結構。

Manifest 定義發布內容。

兩者職責不得重疊。

---

# 8. Review Usage

Freeze Review 應：

- 引用 Canonical Specification Registry。
- 確認 Baseline Manifest。
- Review Working Specification。

Manifest 用於確認：

- Baseline Version。
- Included Specifications。
- Released Specification Versions。

Manifest 不替代 Specification Review。

---

# 9. Future Evolution

Manifest 應支持：

- Baseline Evolution
- Version Management
- Long-term Traceability

每次發布新的 Frozen Baseline 時，應更新 Manifest。

---

# 10. Summary

Baseline Manifest 為 AVPS Frozen Baseline 提供統一發布記錄。

Manifest 定義：

- Baseline Version
- Release Information
- Included Specifications
- Released Specification Versions

Manifest 不定義：

- Specification Structure
- Canonical Responsibility
- High-Level Dependency
- Review
- Freeze
- Specification Content

Baseline Manifest 應作為 AVPS Frozen Baseline 的唯一發布記錄（Authoritative Release Manifest）。
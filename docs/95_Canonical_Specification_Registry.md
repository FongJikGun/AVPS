# 95. Canonical Specification Registry

Version

3.2.0

Status

Draft

Authority

Governance

---

# 1. Purpose

## 1.1 Overview

Canonical Specification Registry 定义 AVPS Specification System 的统一结构索引（Structural Index）。

Registry 用于定义整个 AVPS 的：

- Canonical Specifications
- Specification Category
- Canonical Responsibilities
- High-Level Dependencies

Registry 不定义：

- Version
- Status
- Review
- Freeze
- Release
- Specification Content

上述动态信息应由 Baseline Manifest 管理。

Registry 应作为 AVPS Specification System 的唯一结构权威。

---

## 1.2 Objectives

Registry 应确保：

- Canonical Specification 唯一。
- Canonical Responsibility 唯一。
- High-Level Dependency 清晰。
- Specification Structure 长期稳定。
- Cross-Specification Relationship 可追踪。

---

## 1.3 Scope

Registry 管理：

- Canonical Specifications
- Specification Category
- Canonical Responsibilities
- High-Level Dependencies

Registry 不管理：

- Version
- Release
- Review
- Freeze
- Specification Content

---

# 2. Registry Principles

## 2.1 Single Registry

整个 AVPS 应仅存在一个 Canonical Specification Registry。

所有 Canonical Specification 均应注册于 Registry。

---

## 2.2 Structural Authority

Registry 应作为 AVPS Specification Structure 的唯一结构索引。

整个 AVPS Architecture 应以 Registry 为准。

---

## 2.3 Single Responsibility

每个 Registry Entry 应对应唯一 Canonical Responsibility。

不得：

- 一个 Specification 拥有多个 Canonical Responsibility。
- 多个 Specification 共用同一 Canonical Responsibility。
- 一个 Specification 承担其他 Specification 的 Canonical Responsibility。

---

## 2.4 Dependency Consistency

Registry 中定义的 High-Level Dependency 应保持一致。

不得出现：

- Circular Dependency
- Reverse Dependency
- Undefined Dependency

---

## 2.5 Long-term Stability

Registry 应保持长期稳定。

Version、Review、Freeze 及 Release 等动态变化不应影响 Registry Structure。

---

# 3. Registry Entry

每个 Registry Entry 应包含：

- Specification
- Category
- Canonical Responsibility
- High-Level Dependency

Registry Entry 不应包含：

- Version
- Status
- Review
- Freeze
- Release Date

---

# 4. Canonical Specification Registry

| Specification | Category | Canonical Responsibility | High-Level Dependency |
|---------------|----------|--------------------------|-----------------------|
| 00_Core_Principles | Core | Core Principles | None |
| 01_Architecture | Core | Architecture | Core Principles |
| 02_Asset_Specification_01_Foundation | Asset | Asset Foundation | Core |
| 02_Asset_Specification_02_Data_Models | Asset | Asset Data Models | Asset Specifications |
| 02_Asset_Specification_03_Relationships | Asset | Asset Relationships | Asset Specifications |
| 02_Asset_Specification_04_Lifecycle | Asset | Asset Lifecycle | Asset Specifications |
| 02_Asset_Specification_05_Validation | Asset | Asset Validation | Asset Specifications |
| 02_Asset_Specification_06_Governance | Asset | Asset Governance | Asset Specifications |
| 03_Pipeline_Specification | Pipeline | Canonical Pipeline | Core, Asset Specifications |
| 04_Naming_Convention | Governance | Canonical Naming | Core, Architecture, Asset Specifications, Pipeline |
| 90_Design_Decisions | Governance | Architecture Decisions | Core |
| 96_Baseline_Manifest | Governance | Baseline Release Management | Canonical Specification Registry |
| 99_Review_Checklist | Governance | Review Framework | Core |
| 99_Specification_Patterns | Governance | Specification Patterns | Core |

---

# 5. Registry Rules

## 5.1 Unique Entry

每个 Canonical Specification 应具有唯一 Registry Entry。

不得存在重复 Registry Entry。

---

## 5.2 Canonical Responsibility

每个 Specification 应具有唯一 Canonical Responsibility。

Canonical Responsibility 应保持长期稳定。

---

## 5.3 High-Level Dependency

所有 High-Level Dependency 应：

- 保持单向。
- 保持一致。
- 保持可追踪。

不得形成：

- Circular Dependency
- Dependency Conflict
- Undefined Dependency

---

## 5.4 Registry Independence

Registry 与 Specification Lifecycle 无关。

Specification 可以处于：

- Planned
- Draft
- Reviewing
- Stable
- Deprecated

只要已建立为 Canonical Specification，均应注册于 Registry。

---

# 6. Registry Usage

Registry 应用于：

- Architecture Review
- Dependency Review
- Cross-Specification Review
- Responsibility Review

Registry 用于确认：

- Specification Position
- Specification Category
- Canonical Responsibility
- High-Level Dependency

Registry 不用于确认：

- Version
- Release
- Freeze
- Review Result

---

# 7. Registry Maintenance

Registry 应仅在 Canonical Specification Structure 发生变化时更新。

包括：

- 新增 Canonical Specification。
- 移除 Canonical Specification。
- Canonical Responsibility 调整。
- High-Level Dependency 调整。

Version、Review、Freeze 及 Release 更新不应修改 Registry。

---

# 8. Relationship with Baseline Manifest

Registry 定义：

- Specification Structure

Manifest 定义：

- Baseline Release

Registry 与 Manifest 应保持一致，但职责不得重叠。

---

# 9. Future Evolution

Registry 应支持：

- Specification Expansion
- Architecture Evolution
- Long-term Maintainability

新增 Canonical Specification 时，应同步更新 Registry。

---

# 10. Summary

Canonical Specification Registry 为 AVPS Specification System 提供统一结构索引。

Registry 定义：

- Canonical Specifications
- Specification Category
- Canonical Responsibilities
- High-Level Dependencies

Registry 不定义：

- Version
- Release
- Review
- Freeze
- Specification Content

Canonical Specification Registry 应作为 AVPS Specification System 的唯一结构权威（Authoritative Structural Registry）。

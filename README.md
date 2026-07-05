# AVPS

AI Visual Production Specification

---

# 项目简介

AVPS（AI Visual Production Specification）是一套面向 AI Visual Production 的规范体系。

整个系统采用 Asset-Centric Architecture，以 Specification 为核心，统一定义 Asset、Pipeline、Governance 与 Review Framework，为长期维护、持续扩展及跨 Specification 协作提供一致性的架构基础。

---

# Repository Policy

本 Repository 是 AVPS 的唯一官方规范仓库（Single Source of Truth，SSOT）。

除非特别说明：

- 所有 Specification 均以 Repository 当前内容为准。
- 所有 Baseline 均以 96_Baseline_Manifest 为准。
- 所有 Architecture 均以 01_Architecture 为准。
- 所有 Cross-Specification Review 均以 GitHub Repository 当前版本为准。

---

# 当前状态

Repository Status: Development

Current Frozen Baseline: v3.1.0

Release Status: Stable

Current Working Specification: 04_Naming_Convention

---

# Repository Structure

```text
docs/

00_Core_Principles.md
01_Architecture.md

02_Asset_Specification/
    01_Foundation.md
    02_Data_Models.md
    03_Relationships.md
    04_Lifecycle.md
    05_Validation.md
    06_Governance.md

03_Pipeline_Specification.md
04_Naming_Convention

90_Design_Decisions.md
95_Canonical_Specification_Registry.md
96_Baseline_Manifest.md

99_Review_Checklist.md
99_Specification_Patterns.md
```

---

# 核心设计原则

AVPS 遵循以下核心原则：

- Single Responsibility
- Reference First
- Asset-Centric
- Specification Driven
- Consistency First
- Long-term Maintainability

---

# Governance

Governance Specification 包括：

- 90_Design_Decisions
- 95_Canonical_Specification_Registry
- 96_Baseline_Manifest
- 99_Review_Checklist
- 99_Specification_Patterns

---

# 开发流程

Specification Development

↓

Part Review

↓

Full Specification Review

↓

Freeze

↓

Update Baseline Manifest

↓

Next Specification

---

# Version Management

所有正式版本均通过 Baseline Manifest 管理。

所有 Canonical Specification 统一登记于 Canonical Specification Registry。

---

# License

目前仅用于 AVPS Specification Development。

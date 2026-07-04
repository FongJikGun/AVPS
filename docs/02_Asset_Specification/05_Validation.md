# =================================================================================
# AVPS（AI Visual Production Specification）
# 02_Asset_Specification_05_Validation.md
# Part E：Validation
#
# Version : 3.0.0
# Status  : Stable
# Authority : Specification
# Priority : Highest
# Review : PASS
# Freeze : APPROVED
#
# Description:
# 定义 AVPS 所有 Canonical Validation 的统一规范。
# 本规范不定义任何具体 Asset、Relationship、Data Model 或 Lifecycle，
# 也不定义 Runtime State、Business Workflow 或 Execution Logic。
# 本规范仅定义 Validation 的设计原则、验证结构、验证模型、
# 验证规则、约束、流程、治理、扩展及跨规范集成规范。
# =================================================================================


# 1. Purpose

## 1.1 Overview

本规范定义 AVPS Canonical Validation 的统一规范。

Validation Specification 为所有 Canonical Validation 提供统一的设计原则、验证模型、验证规则、验证流程及治理规范。

本规范作为 AVPS Canonical Validation 的唯一权威规范（Authoritative Specification）。

---

## 1.2 Objectives

Validation Specification 的目标包括：

- 建立统一 Validation Framework。
- 建立统一 Validation Model。
- 建立统一 Validation Rules。
- 建立统一 Validation Process。
- 建立统一 Validation Governance。
- 保持 Validation Consistency。

---

## 1.3 Scope

本规范适用于：

- Canonical Asset Validation。
- Canonical Relationship Validation。
- Canonical Lifecycle Validation。
- Canonical AVPS Specification Validation。

本规范不定义：

- Asset Definition。
- Data Model Definition。
- Relationship Definition。
- Lifecycle Definition。
- Runtime Validation。
- Business Workflow Validation。

---

## 1.4 Design Principles

Validation Specification 应遵循：

- Canonical Consistency。
- Single Responsibility。
- Reference First。
- Progressive Layering。
- Backward Compatibility。
- Long-term Maintainability。

---

## 1.5 Expected Outcomes

Validation Specification 建立统一 Canonical Validation Framework。

所有 AVPS Validation：

- 应遵循统一 Validation Principles。
- 应遵循统一 Validation Process。
- 应遵循统一 Validation Governance。
- 应保持 Validation Consistency。

Validation Specification 为后续 Validation Specification 提供统一设计基础。

---

# 2. Validation Philosophy

## 2.1 Philosophy Overview

Validation Philosophy 定义 Canonical Validation 的统一设计哲学。

Validation Philosophy 为 Validation Specification 提供统一设计原则，并指导 Validation Framework 的整体设计。

Validation Philosophy 不定义：

- Validation Structure
- Validation Types
- Validation Rules
- Validation Process

Validation Philosophy 仅定义 Canonical Validation 的设计理念。

---

## 2.2 Canonical Validation

Validation 应建立于 Canonical AVPS Specification。

所有 Validation：

- 应具有统一 Validation Semantics。
- 应具有统一 Validation Behavior。
- 应遵循统一 Validation Principles。
- 应保持 Canonical Consistency。

Validation 不应依赖具体 Implementation。

---

## 2.3 Validation Independence

Validation 应保持独立性。

Validation：

- 不重新定义 Asset。
- 不重新定义 Data Model。
- 不重新定义 Relationship。
- 不重新定义 Lifecycle。

Validation 仅负责验证 Canonical AVPS Specifications 是否符合规范。

---

## 2.4 Consistency First

Validation 应始终保持一致性。

所有 Validation：

- 应遵循统一 Validation Framework。
- 应采用统一 Validation Criteria。
- 应产生统一 Validation Result。
- 应保持 Validation Consistency。

Validation 不应因实现方式不同而改变语义。

---

## 2.5 Reference First

Validation 应遵循 Reference First 原则。

Validation：

- 应引用 Canonical AVPS Specifications。
- 应验证 Canonical AVPS Specifications。
- 不应复制 Canonical AVPS Specifications。
- 不应重新定义 Canonical AVPS Specifications。

所有 Validation 均应建立于 Canonical Reference。

---

## 2.6 Progressive Validation

Validation 应遵循 Progressive Layering。

Validation 应建立于：

- Core Principles
- Architecture
- Foundation
- Data Models
- Relationships
- Lifecycle

Validation 应基于上述 Canonical AVPS Specifications 逐层进行验证。

---

## 2.7 Long-term Maintainability

Validation 应支持长期维护。

Validation 应：

- 保持 Backward Compatibility。
- 保持 Extensibility。
- 保持 Traceability。
- 保持 Long-term Maintainability。

Validation Philosophy 为后续 Validation Structure 提供统一设计基础。

---

# 3. Validation Structure

## 3.1 Structure Overview

Validation Structure 定义 Canonical Validation 的统一结构。

Validation Structure 为所有 Validation 提供一致的组织方式，并确保 Validation Framework 的结构一致性。

Validation Structure 不定义：

- Validation Types
- Validation Rules
- Validation Process
- Validation Governance

Validation Structure 仅定义 Canonical Validation 的结构组成。

---

## 3.2 Structural Principles

Validation Structure 应遵循统一结构原则。

Validation Structure 应：

- 保持 Canonical Consistency。
- 保持 Structural Integrity。
- 保持 Clear Responsibility。
- 保持 Long-term Maintainability。

所有 Validation 应遵循统一 Validation Structure。

---

## 3.3 Structural Components

Canonical Validation 应由以下组成：

- Validation Scope
- Validation Criteria
- Validation Rules
- Validation Result
- Validation Metadata

所有 Validation Components 应保持明确且唯一。

---

## 3.4 Structural Relationships

Validation Components 应保持统一关系。

Validation：

- 应建立于 Canonical AVPS Specification。
- 应引用 Canonical Reference。
- 应产生 Canonical Validation Result。
- 应保持 Component Consistency。

Validation Components 不应形成冲突关系。

---

## 3.5 Structural Hierarchy

Validation Structure 应保持统一层级。

Validation 应建立于：

- Core Principles
- Architecture
- Foundation
- Data Models
- Relationships
- Lifecycle

Validation Structure 应遵循 Canonical AVPS Specification Hierarchy。

---

## 3.6 Structural Consistency

所有 Validation Structure：

- 应保持一致性。
- 应保持可验证性。
- 应保持可扩展性。
- 应保持可追踪性。

Validation Structure 不应因具体 Implementation 而改变。

---

## 3.7 Structural Integrity

Validation Structure 应保持完整性。

Validation：

- 不得缺少必要 Structural Components。
- 不得破坏 Canonical Structure。
- 不得违反 Canonical Validation Principles。

Validation Structure 为后续 Validation Types 提供统一结构基础。

---

# 4. Validation Types

## 4.1 Types Overview

Validation Types 定义 Canonical Validation 的统一分类。

Validation Types 为所有 Validation 提供一致的分类方式，并确保不同 Validation 的职责边界清晰。

Validation Types 不定义：

- Validation Rules
- Validation Constraints
- Validation Process
- Validation Governance

Validation Types 仅定义 Canonical Validation 的分类体系。

---

## 4.2 Validation Categories

Canonical Validation 包括以下类型：

- Foundation Validation
- Data Model Validation
- Relationship Validation
- Lifecycle Validation
- Specification Validation

所有 Validation 均应属于明确的 Validation Type。

所有 Canonical Validation Type 应遵循统一 Validation Framework。

---

## 4.3 Foundation Validation

Foundation Validation 用于验证 Canonical Asset Foundation 是否符合 Foundation Specification。

Foundation Validation：

- 应引用 Foundation Specification。
- 不应重新定义 Foundation。

---

## 4.4 Data Model Validation

Data Model Validation 用于验证 Canonical Data Models 是否符合 Data Model Specification。

Data Model Validation：

- 应引用 Data Model Specification。
- 不应重新定义 Data Models。

---

## 4.5 Relationship Validation

Relationship Validation 用于验证 Canonical Relationships 是否符合 Relationship Specification。

Relationship Validation：

- 应引用 Relationship Specification。
- 不应重新定义 Relationships。

---

## 4.6 Lifecycle Validation

Lifecycle Validation 用于验证 Canonical Lifecycle 是否符合 Lifecycle Specification。

Lifecycle Validation：

- 应引用 Lifecycle Specification。
- 不应重新定义 Lifecycle。

---

## 4.7 Specification Validation

Specification Validation 用于验证 AVPS Canonical AVPS Specificationss 是否符合统一规范。

Specification Validation：

- 应建立于 Canonical AVPS Specifications。
- 应遵循统一 Validation Framework。
- 应保持 Validation Consistency。

Specification Validation 不应重新定义任何 Canonical AVPS Specifications。

Specification Validation 应通过 Reference 引用 Canonical AVPS Specifications。

---

# 5. Validation Rules

## 5.1 Rules Overview

Validation Rules 定义 Canonical Validation 的统一行为规范。

Validation Rules 为所有 Validation 提供一致的执行规则，并确保 Validation Framework 的行为一致性。

Validation Rules 不定义：

- Validation Constraints
- Validation Process
- Validation Governance
- Validation Extension

Validation Rules 仅定义 Canonical Validation 的行为规范。

---

## 5.2 Validation Principles

所有 Validation 应遵循统一 Validation Principles。

Validation 应：

- 保持 Canonical Consistency。
- 保持 Deterministic Behavior。
- 保持 Repeatability。
- 保持 Traceability。
- 保持 Verifiability。

Validation 不应因不同实现而产生不同结果。

---

## 5.3 Reference Rules

所有 Validation：

- 应引用 Canonical AVPS Specifications。
- 应验证 Canonical AVPS Specifications。
- 不应复制 Canonical AVPS Specifications。
- 不应修改 Canonical AVPS Specifications。

Validation 应始终遵循 Reference First Principle。

---

## 5.4 Validation Execution Rules

所有 Validation：

- 应按照统一 Validation Framework 执行。
- 应采用统一 Validation Criteria。
- 应产生统一 Validation Result。
- 应保持 Validation Consistency。

Validation Execution 应保持可重复且可预测。

---

## 5.5 Validation Result Rules

所有 Validation Result：

- 应具有明确结果。
- 应具有唯一语义。
- 应支持 Traceability。
- 应支持 Audit。

Validation Result 不应具有歧义。

---

## 5.6 Validation Consistency Rules

所有 Validation：

- 应遵循统一 Validation Rules。
- 应遵循统一 Validation Structure。
- 应遵循统一 Validation Types。
- 应保持跨 Specification 的一致性。

Validation 不应违反 Canonical Validation Principles。

---

## 5.7 Rule Compliance

所有 Validation：

- 应符合 Canonical Validation Rules。
- 应符合 Canonical AVPS Specifications。
- 应支持长期维护。
- 应支持持续演进。

Validation Rules 为后续 Validation Constraints 提供统一规范基础。

---

# 6. Validation Constraints

## 6.1 Constraints Overview

Validation Constraints 定义 Canonical Validation 的统一约束规范。

Validation Constraints 用于确保所有 Validation 保持一致性、完整性及规范符合性。

Validation Constraints 不定义：

- Validation Process
- Validation Governance
- Validation Extension
- Validation Integration

Validation Constraints 仅定义 Canonical Validation 的约束条件。

---

## 6.2 Canonical Constraints

所有 Validation 应遵循 Canonical Constraints。

Validation：

- 不得违反 Canonical AVPS Specifications。
- 不得违反 Canonical Validation Principles。
- 不得违反 Canonical Validation Rules。
- 应保持 Canonical Consistency。

---

## 6.3 Reference Constraints

所有 Validation：

- 应引用 Canonical AVPS Specifications。
- 不得复制 Canonical AVPS Specificationss。
- 不得修改 Canonical AVPS Specificationss。
- 应保持 Reference Integrity。

Validation 不得绕过 Canonical AVPS Reference。

---

## 6.4 Structural Constraints

Validation 应保持统一结构。

Validation：

- 不得缺少必要 Structural Components。
- 不得破坏 Canonical Validation Structure。
- 不得违反 Structural Integrity。

Validation Structure 应保持一致。

---

## 6.5 Execution Constraints

Validation Execution：

- 应保持 Deterministic Behavior。
- 应保持 Repeatability。
- 应保持 Traceability。
- 应保持 Verifiability。

Validation Execution 不得因 Implementation 而改变结果。

---

## 6.6 Result Constraints

Validation Result：

- 应具有唯一语义。
- 应具有明确状态。
- 应支持 Audit。
- 应支持 Traceability。

Validation Result 不得具有歧义。

---

## 6.7 Constraint Compliance

所有 Validation：

- 应符合 Canonical Validation Constraints。
- 应符合 Canonical AVPS Specifications。
- 应保持长期一致性。
- 应支持持续演进。

Validation Constraints 为后续 Validation Process 提供统一规范基础。

---

# 7. Validation Process

## 7.1 Process Overview

Validation Process 定义 Canonical Validation 的统一执行流程。

Validation Process 为所有 Validation 提供一致的执行方式，并确保 Validation Framework 的执行一致性。

Validation Process 不定义：

- Validation Governance
- Validation Extension
- Validation Integration

Validation Process 仅定义 Canonical Validation 的执行流程。

---

## 7.2 Process Principles

Validation Process 应遵循统一执行原则。

Validation Process 应：

- 保持 Canonical Consistency。
- 保持 Deterministic Behavior。
- 保持 Repeatability。
- 保持 Traceability。
- 保持 Process Integrity。

所有 Validation Process 应遵循统一执行规范。

---

## 7.3 Process Flow

Validation Process 应包括以下阶段：

- Validation Preparation
- Validation Execution
- Validation Result Generation
- Validation Result Verification
- Validation Completion

所有 Validation 应遵循统一 Process Flow。

---

## 7.4 Execution Requirements

Validation Execution：

- 应建立于 Canonical AVPS Specifications。
- 应遵循 Canonical Validation Rules。
- 应符合 Validation Constraints。
- 应保持 Validation Consistency。

Validation Execution 不得绕过 Canonical Validation Process。

---

## 7.5 Result Processing

Validation Result：

- 应具有唯一结果。
- 应支持 Traceability。
- 应支持 Audit。
- 应保持 Result Integrity。

Validation Result 应保持一致且可验证。

---

## 7.6 Process Consistency

所有 Validation Process：

- 应遵循统一 Validation Framework。
- 应遵循统一 Validation Structure。
- 应遵循统一 Validation Types。
- 应保持跨 Specification 的一致性。

Validation Process 不应因不同 Implementation 而改变。

---

## 7.7 Process Compliance

所有 Validation：

- 应符合 Canonical Validation Process。
- 应符合 Canonical Validation Rules。
- 应符合 Validation Constraints。
- 应支持持续演进。

Validation Process 为后续 Validation Governance 提供统一管理基础。

---

# 8. Validation Governance

## 8.1 Governance Overview

Validation Governance 定义 Canonical Validation 的统一治理规范。

Validation Governance 用于确保所有 Validation 保持一致性、可管理性及长期可维护性。

Validation Governance 不定义：

- Validation Extension
- Validation Integration

Validation Governance 仅定义 Canonical Validation 的治理要求。

---

## 8.2 Governance Principles

Validation Governance 应遵循统一治理原则。

Validation Governance 应：

- 保持 Canonical Consistency。
- 保持 Governance Integrity。
- 保持 Accountability。
- 保持 Long-term Maintainability。

所有 Validation Governance 应遵循统一治理规范。

---

## 8.3 Governance Scope

Validation Governance 应涵盖：

- Validation Framework
- Validation Process
- Validation Result
- Validation Compliance
- Validation Evolution

Validation Governance 负责治理 Validation Evolution，但不重新定义 Evolution。

Validation Governance 不应重新定义 Canonical Validation。

---

## 8.4 Governance Requirements

所有 Validation：

- 应符合 Canonical Validation Governance。
- 应遵循 Canonical Validation Rules。
- 应符合 Validation Constraints。
- 应遵循 Validation Process。

Validation Governance 应保持一致且可追踪。

---

## 8.5 Governance Compliance

所有 Validation Governance：

- 应支持 Traceability。
- 应支持 Audit。
- 应支持 Continuous Improvement。
- 应支持 Long-term Governance。

Validation Governance 不得绕过 Canonical Validation Principles。

---

## 8.6 Governance Consistency

所有 Validation Governance：

- 应遵循统一 Validation Framework。
- 应保持跨 Specification 的一致性。
- 应保持 Governance Consistency。
- 应保持 Canonical Consistency。

Validation Governance 不应因不同 Implementation 而改变。

---

## 8.7 Governance Integrity

所有 Validation：

- 应符合 Canonical Validation Governance。
- 应符合 Canonical AVPS Specifications。
- 应支持长期维护。
- 应支持持续演进。

Validation Governance 为后续 Validation Extension 提供统一规范基础。

---

# 9. Validation Extension

## 9.1 Extension Overview

Validation Extension 定义 Canonical Validation 的统一扩展规范。

Validation Extension 用于确保所有 Validation 在保持 Canonical Consistency 的前提下支持持续扩展。

Validation Extension 不定义：

- Validation Integration
- Cross Specification References

Validation Extension 仅定义 Canonical Validation 的扩展要求。

---

## 9.2 Extension Principles

Validation Extension 应遵循统一扩展原则。

Validation Extension 应：

- 保持 Canonical Consistency。
- 保持 Backward Compatibility。
- 保持 Extensibility。
- 保持 Long-term Maintainability。

所有 Validation Extension 应遵循统一扩展规范。

---

## 9.3 Extension Scope

Validation Extension 可扩展：

- Validation Framework
- Validation Types
- Validation Rules
- Validation Process
- Validation Governance

Validation Extension 不应重新定义 Canonical Validation。

Validation Extension 应通过 Reference 扩展 Canonical Validation。

---

## 9.4 Extension Requirements

所有 Validation Extension：

- 应建立于 Canonical AVPS Specifications。
- 应遵循 Canonical Validation Principles。
- 应符合 Validation Constraints。
- 应保持 Validation Consistency。

Validation Extension 不得破坏 Canonical Validation Framework。

---

## 9.5 Extension Compatibility

所有 Validation Extension：

- 应保持 Backward Compatibility。
- 应保持 Structural Compatibility。
- 应保持 Semantic Compatibility。
- 应保持 Reference Compatibility。

Validation Extension 不得影响既有 Canonical Validation。

---

## 9.6 Extension Consistency

所有 Validation Extension：

- 应遵循统一 Validation Framework。
- 应保持跨 Specification 的一致性。
- 应保持 Extension Consistency。
- 应保持 Canonical Consistency。

Validation Extension 不应因不同 Implementation 而改变。

---

## 9.7 Extension Integrity

所有 Validation：

- 应符合 Canonical Validation Extension。
- 应符合 Canonical AVPS Specifications。
- 应支持长期维护。
- 应支持持续演进。

Validation Extension 为后续 Validation Integration 提供统一规范基础。

---

# 10. Validation Integration

## 10.1 Integration Overview

Validation Integration 定义 Canonical Validation 的统一集成规范。

Validation Integration 用于确保 Validation 与所有 Canonical AVPS Specifications 保持一致、稳定且可维护的集成关系。

Validation Integration 不定义：

- Cross Specification References
- Specification Summary

Validation Integration 仅定义 Canonical Validation 的集成要求。

---

## 10.2 Integration Principles

Validation Integration 应遵循统一集成原则。

Validation Integration 应：

- 保持 Canonical Consistency。
- 保持 Reference First。
- 保持 Integration Integrity。
- 保持 Long-term Maintainability。

所有 Validation Integration 应遵循统一集成规范。

---

## 10.3 Integration Scope

Validation Integration 应涵盖：

- Core Principles
- Architecture
- Foundation
- Data Models
- Relationships
- Lifecycle

Validation Integration 不应重新定义任何 Canonical AVPS Specification。

---

## 10.4 Integration Requirements

所有 Validation Integration：

- 应建立于 Canonical AVPS Specifications。
- 应通过 Canonical Reference 建立集成。
- 应遵循 Canonical Validation Principles。
- 应保持 Validation Consistency。
- 应通过 Canonical AVPS Specifications 建立集成关系。

Validation Integration 不得绕过 Canonical AVPS Specifications。

---

## 10.5 Integration Compatibility

所有 Validation Integration：

- 应保持 Backward Compatibility。
- 应保持 Structural Compatibility。
- 应保持 Semantic Compatibility。
- 应保持 Reference Compatibility。

Validation Integration 不得破坏既有 Canonical AVPS Specificationss。

---

## 10.6 Integration Consistency

所有 Validation Integration：

- 应遵循统一 Validation Framework。
- 应保持跨 Specification 的一致性。
- 应保持 Integration Consistency。
- 应保持 Canonical Consistency。

Validation Integration 不应因不同 Implementation 而改变。

---

## 10.7 Integration Integrity

所有 Validation：

- 应符合 Canonical Validation Integration。
- 应符合 Canonical AVPS Specifications。
- 应支持长期维护。
- 应支持持续演进。

Validation Integration 为后续 Cross Specification References 提供统一集成基础。

---

# 11. Cross Specification References

## 11.1 Reference Overview

Cross Specification References 定义 Validation Specification 与其他 Canonical AVPS Specifications 的统一引用关系。

Validation Specification 应通过 Canonical Reference 与其他 Specifications 建立一致、稳定且可维护的依赖关系。

Cross Specification References 不定义：

- Canonical Asset
- Data Models
- Relationships
- Lifecycle
- Validation Rules

Cross Specification References 仅定义 Specification 之间的引用关系。

所有引用关系均应通过 Canonical Reference 建立。

---

## 11.2 Core Principles

Validation Specification 应引用：

- 00_Core_Principles

Core Principles 为 Validation 提供统一设计原则。

Validation Specification 不应重新定义 Core Principles。

---

## 11.3 Architecture

Validation Specification 应引用：

- 01_Architecture

Architecture 为 Validation 提供统一架构约束。

Validation Specification 不应重新定义 Architecture。

---

## 11.4 Foundation

Validation Specification 应引用：

- 02_Asset_Specification_01_Foundation

Foundation 为 Validation 提供 Canonical Asset Foundation。

Validation Specification 不应重新定义 Foundation。

---

## 11.5 Data Models

Validation Specification 应引用：

- 02_Asset_Specification_02_Data_Models

Data Models 为 Validation 提供 Canonical Data Model。

Validation Specification 不应重新定义 Data Models。

---

## 11.6 Relationships

Validation Specification 应引用：

- 02_Asset_Specification_03_Relationships

Relationships 为 Validation 提供 Canonical Relationship。

Validation Specification 不应重新定义 Relationships。

---

## 11.7 Lifecycle

Validation Specification 应引用：

- 02_Asset_Specification_04_Lifecycle

Lifecycle 为 Validation 提供 Canonical Lifecycle。

Validation Specification 不应重新定义 Lifecycle。

Validation Specification 应通过 Canonical Reference 建立所有 Cross Specification References，并始终遵循 Reference First Principle。

Validation Specification 不应重新定义任何 Canonical AVPS Specification。

---

# 12. Summary

## 12.1 Specification Summary

Validation Specification 定义 AVPS Canonical Validation 的统一规范。

本规范建立了统一的：

- Validation Philosophy
- Validation Structure
- Validation Types
- Validation Rules
- Validation Constraints
- Validation Process
- Validation Governance
- Validation Extension
- Validation Integration

上述内容共同构成 Canonical Validation Framework。

Validation Specification 为所有 Canonical Validation 提供统一规范基础。

---

## 12.2 Core Principles

Validation Specification 应始终遵循：

- Canonical Consistency
- Single Responsibility
- Reference First
- Progressive Layering
- Backward Compatibility
- Long-term Maintainability

所有 Validation 均应遵循上述核心原则。

---

## 12.3 Specification Position

Validation Specification 建立于 Canonical AVPS Specifications 之上。

Validation Specification：

- 不重新定义 Core Principles。
- 不重新定义 Architecture。
- 不重新定义 Foundation。
- 不重新定义 Data Models。
- 不重新定义 Relationships。
- 不重新定义 Lifecycle。

Validation Specification 仅定义 Canonical Validation。

---

## 12.4 Expected Outcomes

Validation Specification 建立统一 Validation Framework。

所有 Validation：

- 应遵循统一 Validation Principles。
- 应遵循统一 Validation Structure。
- 应遵循统一 Validation Rules。
- 应保持 Canonical Consistency。

Validation Specification 为所有 Validation 提供统一规范依据。

---

## 12.5 Future Evolution

Validation Specification 应支持：

- Continuous Improvement。
- Backward Compatibility。
- Specification Evolution。
- Long-term Maintainability。

未来扩展应遵循 Canonical AVPS Specifications，并保持 Reference First Principle。

---

## 12.6 Final Statement

Validation Specification 为 AVPS Canonical Validation 提供统一、稳定且可维护的规范基础。

所有 Canonical Validation 应建立于本规范，并通过 Canonical Reference 与其他 Canonical AVPS Specifications 保持一致。

Validation Specification 应作为 AVPS Canonical Validation 的唯一权威规范（Authoritative Specification）。

所有 Validation Implementation 均应遵循本规范。

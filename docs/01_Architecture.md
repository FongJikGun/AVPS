# =================================================================================
# AVPS（AI Visual Production Specification）
# 01_Architecture.md
# Version: 3.0.0
# Status: Stable
# Authority: Architecture
# Priority: High
#
# Description:
# 定义 AVPS 的整体系统架构、模块边界、数据流及依赖关系。
# 本文档受《00_Core_Principles.md》约束，
# 是所有 Specification 的系统蓝图（System Blueprint）。
# =================================================================================

# 1. Purpose

Architecture 的职责不是描述制作流程（Pipeline），
而是定义整个 AVPS 的系统结构。

回答四个问题：

1. 系统由哪些模块组成？
2. 每个模块负责什么？
3. 模块之间如何依赖？
4. 数据如何流动？

Architecture 定义结构，
Implementation 定义实现。

---

# 2. Architectural Principles

本架构遵循《00_Core_Principles.md》全部原则。

其中重点遵循：

- CP-000 Specification Supremacy
- CP-001 SSOT
- CP-002 Everything Is an Asset
- CP-003 Everything Is Referenced
- CP-004 Design Before Generation
- CP-005 Prompt Is Compiled

整个 Architecture 必须体现：

> **Asset-Centric（资产中心）**

而不是：

> Pipeline-Centric（流程中心）

---

# 3. System Overview

AVPS 采用 Asset-Centric Architecture。

整个系统围绕 SSOT（Single Source of Truth）运行。

```text
                         AVPS
                           │
         ┌─────────────────┴─────────────────┐
         │                                   │
         ▼                                   ▼
 Core Principles                       Architecture
         │                                   │
         └─────────────────┬─────────────────┘
                           │
                    Pipeline System
                           │
                           ▼
                    Asset Extraction
                           │
                           ▼
                  Asset System（SSOT）
                           │
      ┌────────┬────────┬──┴──────┬────────┬─────┐
      │        │        │         │        │     │
      ▼        ▼        ▼         ▼        ▼     ▼
    World  Character  Outfit  Component  Scene  Prop
      │        │        │         │      │       │
      └────────┴────────┴──┬──────┴──────┴───────┘
                           │
                           ▼
                     Configuration
                           │
                   ┌───────┼───────┐
                   ▼       ▼       ▼
                  Shot   Prompt    QA
                           │
                           ▼
                      Compilation
                           │
                           ▼
                       Execution
                           │
                   ┌───────┼───────┐
                   ▼       ▼       ▼
                 Image   Video   Audio
                           │
                           ▼
                    Post Production
                           │
                           ▼
                     Final Output
```

---

# 4. System Layers

AVPS 分为六层。

```text
Layer 0
Core Principles
（最高原则）

↓

Layer 1
Architecture
（系统蓝图）

↓

Layer 2
Pipeline
（资产编排）

↓

Layer 3
Asset System（SSOT）
（唯一真源）

↓

Layer 4
Compilation
（编译层）

↓

Layer 5
Execution
（执行层）
```

---

## Layer 0｜Core Principles

职责：

定义整个 AVPS 的最高原则。

输出：

- Design Philosophy
- Core Principles
- Compliance Rules

特点：

唯一最高约束。

---

## Layer 1｜Architecture

职责：

定义：

系统组成

模块关系

数据流

依赖关系

Architecture：

不保存资产。

不参与生成。

---

## Layer 2｜Pipeline

Pipeline：

不是系统核心。

Pipeline：

只是编排器（Orchestrator）。

负责：

资产流转。

输入：

Script

输出：

Asset Extraction Tasks

Pipeline：

不保存任何资产。

Pipeline 负责资产流转（Orchestration），
但不拥有任何资产（Ownership）。


---

## Layer 3｜Asset System（SSOT）

整个 AVPS 的核心。

唯一真源。

所有设计：

必须进入 Asset。

任何模块：

不得绕过 Asset。

Asset 包括：

```text
Character

Outfit

Component

Prop

Scene

World Library

Configuration
```

Configuration 是多个资产的组合（Asset Composition），
而不是 Character 的子资产。

Asset：

拥有：

- ID
- Metadata
- Dependency
- Version

---

## Layer 4｜Compilation

Compilation：

负责：

读取 Asset。

生成：

可执行对象。

包括：

- Prompt Compiler
- Shot Package Compiler
- Export Package Compiler

Compilation：

不能修改资产。

只能映射。

---

## Layer 5｜Execution

负责：

真正调用 AI。

例如：

- Gemini
- Imagen
- Veo
- ChatGPT
- Claude
- Midjourney

AI：

属于执行器。

不是系统。

---

# 5. Core Modules

AVPS 由八个核心模块组成。

---

## M01 Core Principles

职责：

定义整个规范的最高原则。

输入：

—

输出：

- Design Philosophy

- Core Principles

- Compliance Rules

---

## M02 Architecture

职责：

定义系统结构。

输入：

Rules

输出：

Architecture

---

## M03 Pipeline

职责：

资产编排。

Pipeline：

负责：

解析

调度

组织

不负责：

保存。

---

## M04 Asset System ⭐

整个 AVPS 的中心（Hub）。

负责：

唯一真源。

包括：

```text
Character

Outfit

Component

Scene

Prop

World Library

Configuration
```

所有系统：

只能引用 Asset。

不得复制。

---

## M05 Compilation System

包括：

Prompt Compiler

Shot Compiler

Export Compiler

作用：

Asset

↓

Executable Objects

---

## M06 Generation Engine

输入：

Prompt

执行：

Image

Video

Audio

Generation：

无状态。

---

## M07 Post Production

负责：

剪辑

配音

字幕

调色

导出

---

## M08 QA System

负责：

一致性验证。

例如：

角色漂移

服装漂移

Prompt冲突

资产缺失

版本冲突

---

# 6. Asset-Centric Data Flow

整个 AVPS 的真正数据流。

```text
Script

↓

Pipeline

↓

Asset Extraction

↓

Asset System（SSOT）
├── World
├── Character
├── Outfit
├── Component
├── Scene
├── Prop

↓

Configuration

↓

Compilation

↓

Execution

↓

Media

↓

Post Production

↓

Final Output
```

重要：

所有数据：

必须进入：

Asset。

禁止：

```text
Script

↓

Prompt
```

直接生成。

---

# 7. Dependency Graph

正确依赖：

```text
Core Principles

↓

Architecture

↓

Pipeline

↓

Asset

↓

Configuration

↓

Compilation

↓

Generation

↓

Post
```

禁止：

```text
Character

↓

Prompt

↓

Character
```

循环引用。

---

# 8. Module Communication

所有模块之间：

只允许：

Reference。

例如：

Shot：

```text
Character：

CH-001
```

禁止：

重新写：

角色描述。

---

# 9. Responsibility Matrix

| Module | 唯一职责 | 输入 | 输出 |
|----------|----------|------|------|
| Core Principles | 定义最高原则 | - | Rules |
| Architecture | 定义系统结构 | Rules | Architecture |
| Pipeline | 编排资产流 | Script | Asset Tasks |
| Asset System | 保存唯一真源 | Parsed Data | Assets |
| Compilation | 编译执行对象 | Assets | Prompt / Shot |
| Generation | AI执行 | Prompt | Media |
| QA | 一致性验证 | Assets + Media | Report |
| Post Production | 后期合成 | Media | Final Output |

---

# 10. Architectural Constraints

## AC-001

Single Responsibility

一个模块：

只有一个职责。

---

## AC-002

No Circular Dependency

禁止：

循环依赖。

---

## AC-003

Reference First

共享数据：

必须引用。

禁止复制。

---

## AC-004

Asset-Centric

Asset：

永远位于系统中心。

任何模块：

不得绕过 Asset。

---

## AC-005

Stateless Execution

Execution：

不能保存状态。

状态：

来自：

Asset。

---

## AC-006

Compiler Isolation

Compiler：

不能修改资产。

Compiler：

只能读取。

---

## AC-007

Implementation Independence

任何 AI：

属于实现。

不是架构。

Architecture：

不得绑定：

任何模型。

---

# 11. Future Extension Points

未来可以新增：

```text
Storyboard System

Animation System

Physics System

Voice System

Localization

Publishing

Asset Marketplace

Automation Engine

Workflow Scheduler
```

所有新增模块必须作为 Asset Consumer，
不得绕过 Asset System。

新增模块：

必须：

- 遵守 Core Principles
- 引用 Asset
- 不修改 Asset
- 保持单向依赖

---

# 12. Milestone Definition

完成本 Architecture 后，

AVPS 已完成：

✅ 系统蓝图

后续所有 Specification：

均建立在本架构之上。

开发顺序固定：

```text
00_Core_Principles.md
        │
        ▼
01_Architecture.md
        │
        ▼
02_Asset_Specification.md   ⭐⭐⭐（系统核心）
        │
        ▼
03_Pipeline_Specification.md
        │
        ▼
04_Naming_Convention.md
        │
        ▼
05_Prompt_Compiler.md
        │
        ▼
06_Shot_Package.md
        │
        ▼
07_Generation.md
        │
        ▼
08_Post_Production.md
```

---

# 13. Architecture Summary

AVPS 不是一个 Prompt 工作流。

AVPS 是一个：

> **以资产为中心（Asset-Centric）**
>
> **以规范为约束（Specification-Driven）**
>
> **以编译为桥梁（Compilation-Based）**
>
> **以 AI 为执行器（Execution-Oriented）**

的工业化视觉生产架构。

Pipeline 只是入口。

**Asset 才是核心。**

所有模块围绕 Asset 协同工作。

这也是 AVPS 与传统 AI Prompt 工作流最大的区别。

# =================================================================================
# End of Document
# =================================================================================
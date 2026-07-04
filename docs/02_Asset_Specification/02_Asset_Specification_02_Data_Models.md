# =================================================================================
# AVPS（AI Visual Production Specification）
# 02_Asset_Specification_02_Data_Models.md
#
# Version : 3.0.0
# Status  : Stable
# Authority : Specification
# Priority : Highest
# Review: PASS
# Freeze: APPROVED
#
# Description:
# 定义 AVPS 各类资产的数据模型（Data Model）。
# 本文档基于《02_Asset_Specification_01_Foundation.md》，
# 不定义具体资产实例，仅定义各种 Asset 的标准数据模型。=================================================================================

# 目录
1. Purpose

2. Data Model Philosophy

3. Common Data Model Template

4. Character Data Model

5. Outfit Data Model

6. Component Data Model

7. Scene Data Model

8. Prop Data Model

9. World Data Model

10. Configuration Data Model

11. Cross Model Rules

12. Summary

# 1. Purpose

本规范定义 AVPS 各类 Asset 的数据模型。

Asset Foundation 定义：

「什么是 Asset」。

Data Models 定义：

「每一种 Asset 应该包含哪些数据结构」。

本规范不保存任何项目数据。

本规范不定义任何 Asset Instance。

---

# 2. Data Model Philosophy

所有 Data Model 必须遵循：

- 00_Core_Principles.md
- 01_Architecture.md
- 02_Asset_Specification_01_Foundation.md

所有 Data Model：

- 必须符合 Asset Foundation。
- 必须保持单一职责。
- 必须可独立版本化。
- 必须支持引用关系。
- 必须支持 Validation。
- 必须支持未来扩展。

任何 Data Model：

不得修改 Foundation 定义。

只能增加自身业务结构。

---

# 3. Common Data Model Template

所有 Asset Data Model 必须采用统一结构。

```text
Asset Data Model
├── Purpose
├── Scope
├── Data Structure
├── Required Fields
├── Optional Fields
├── Relationships
├── Constraints
├── Validation Rules
└── Extension Points
```

---

## 3.1 Purpose

说明：

该 Asset 的职责。

回答：

"它负责什么？"

---

## 3.2 Scope

说明：

该 Asset 的边界。

回答：

"它不负责什么？"

---

## 3.3 Data Structure

定义：

该 Asset 的整体数据结构。

仅定义结构。

不填写实例数据。

---

## 3.4 Required Fields

定义：

所有实例必须存在的字段。

缺失则 Validation Failed。

---

### 3.4.1 Required Fields 与 Optional Fields

所有 Asset Data Model 必须将字段划分为以下两类：

#### Required Fields（必需字段）

Required Fields 是 Asset 成立所必须具备的最小信息集合。

缺少任意 Required Field，

Asset Validation 必须失败，

该 Asset 视为无效（Invalid）。

只有当字段对 Asset 的身份（Identity）、
合法性（Validity）或核心职责（Core Responsibility）不可或缺时，
才能定义为 Required Field。

---

#### Optional Fields（可选字段）

Optional Fields 用于扩展 Asset 的能力、
信息丰富度或项目需求。

缺少 Optional Fields 不影响 Asset 的合法性。

Optional Fields 可以为空，
也可以在 Asset 生命周期中逐步补充。

Optional Fields 不得承担 Required Fields 的职责。

---

### 3.4.2 字段分类原则

字段是否属于 Required Fields 或 Optional Fields，

应依据 Asset 的本质职责（Core Responsibility）进行判断。

判断一个字段是否属于 Required，

只需回答以下问题：

> 如果删除这个字段，这个 Asset 还成立吗？

- 如果答案是「不能成立」，则该字段应定义为 Required Field。
- 如果答案是「仍然成立，只是能力或信息减少」，则该字段应定义为 Optional Field。

字段分类不得依据项目需求、实现方式或使用频率决定。

所有 Asset Data Model 均应遵循本原则。

---

## 3.5 Optional Fields

定义：

可选字段。

允许为空。

---

## 3.6 Relationships

定义：

允许引用哪些 Asset。

以及引用规则。

---

## 3.7 Constraints

定义：

该 Asset 的设计约束。

例如：

- 是否允许多个引用。
- 是否允许循环引用。
- 是否允许修改。

---

## 3.8 Validation Rules

定义：

该 Asset 的校验规则。

包括：

- 字段完整性
- 引用合法性
- 数据一致性
- 版本一致性

---

## 3.9 Extension Points

定义：

未来允许扩展的位置。

不得破坏已有结构。

---

# 4. Character Data Model

## 4.1 Purpose

Character Data Model 用于定义 Character Asset 的标准数据模型。

Character Asset 的职责是定义角色的核心身份（Identity）、
基础外观（Immutable Appearance）以及视觉识别特征（Visual DNA）。

Character Asset 是角色的唯一身份资产（Identity Asset）。

Character Asset 不保存：

- Outfit
- Component
- Scene
- Prop
- Configuration
- State

上述内容均由对应 Asset 独立管理。

Character Data Model 定义的是：

> 一个角色"是谁（Who）"，

而不是：

> 一个角色"当前是什么样（Current Configuration）"。

Character Data Model 必须符合：

- 00_Core_Principles.md
- 01_Architecture.md
- 02_Asset_Specification_01_Foundation.md

---

## 4.2 Scope

Character Data Model 的 Scope 为：

定义角色在整个 AVPS 生命周期内保持稳定的基础信息。

Character Data Model 负责：

- Character Identity
- Immutable Appearance
- Visual DNA
- Character References

Character Data Model 不负责：

- Outfit Design
- Weapon Design
- Accessories
- Scene Placement
- Character State
- Runtime Configuration
- Shot Information
- Prompt Information

Character Data Model 不保存任何运行时数据（Runtime Data）。

Character Data Model 不参与镜头调度。

Character Data Model 不参与 AI 生成。

Character Data Model 仅作为整个系统的 Character Asset Schema。

---

## 4.3 Data Structure

Character Data Model 建立于 Asset Foundation 之上。

Foundation 中定义的：

- Header
- Metadata
- Relationships
- Status
- Validation
- Version

全部继承。

Character Data Model 仅定义 Character 专属 Content。

标准结构如下：

```text
Character Asset
│
├── Header                    (Inherited)
├── Metadata                  (Inherited)
├── Content
│   ├── Identity
│   ├── Immutable Appearance
│   ├── Visual DNA
│   └── Character References
├── Relationships             (Inherited)
├── Status                    (Inherited)
├── Validation                (Inherited)
└── Version                   (Inherited)
```

其中：

### Identity

定义角色不可变的身份信息。

负责回答：

> 这个角色是谁？

Identity 不受：

- Outfit
- State
- Configuration

影响。

---

### Immutable Appearance

定义角色不可变的基础外观。

Immutable Appearance 仅包含基础生理特征。

例如：

- Face Structure
- Hair
- Eyes
- Body Type
- Height Class
- Skin Tone

Immutable Appearance 不包含：

- Clothes
- Armor
- Accessories
- Weapons

---

### Visual DNA

Visual DNA 定义角色长期保持一致的视觉识别特征。

Visual DNA 的目标不是描述外观，

而是保证角色在不同：

- Outfit
- State
- Scene
- Configuration

下仍具有稳定辨识度。

Visual DNA 属于 Character 的核心组成部分。

---

### Character References

Character References 定义 Character 的默认引用关系。

仅保存默认引用。

不保存运行时配置。

例如：

- Default Outfit
- Default Prop

所有引用均必须使用 Asset ID。

不得复制 Asset 内容。

---

## 4.4 Required Fields

Character Asset 必须包含以下字段。

缺少任意 Required Field，

Character Asset Validation 必须失败。

---

### RF-001 Identity

Character Asset 必须包含 Identity。

Identity 用于定义角色的唯一身份。

Identity 为 Character 的核心字段。

不得缺失。

---

### RF-002 Immutable Appearance

Character Asset 必须包含 Immutable Appearance。

Immutable Appearance 用于定义角色不可变的基础外观。

不得包含：

- Outfit
- Accessories
- Weapons
- Runtime State

---

### RF-003 Visual DNA

Character Asset 必须包含 Visual DNA。

Visual DNA 用于定义角色长期保持一致的视觉识别特征。

Visual DNA 应独立于：

- Outfit
- Configuration
- Scene
- Runtime State

---

### RF-004 Inherited Foundation Fields

除 Character 专属字段外，

Character Asset 必须继承 Asset Foundation 定义的全部基础字段。

包括：

- Header
- Metadata
- Relationships
- Status
- Validation
- Version

上述字段不得删除。

不得重新定义。

Character Data Model 仅扩展 Character 专属 Content。

不得修改 Foundation。

---

## 4.5 Optional Fields

Character Asset 可以包含以下 Optional Fields。

Optional Fields 用于扩展 Character 的能力。

缺失 Optional Fields 不影响 Character Asset 的合法性。

---

### OF-001 Character References

Character References 用于定义 Character 与其他长期稳定资产之间的关联。该关联为 Canonical（规范）关系，而非运行时组合关系。

Character References 为可选字段（Optional）。

Character 创建时可以为空。

当相关资产建立后，

可以逐步补充。

Character References：

- 必须引用 Asset ID。
- 不得复制 Asset 内容。
- 不得引用 Runtime Asset。
- 不得引用 Composition Asset（例如 Configuration）。

---

### OF-002 Biography

Biography 用于记录 Character 的背景设定。

Biography 不参与：

- Asset Identity
- Validation
- AI Generation

Biography 属于辅助描述信息。

允许为空。

---

### OF-003 Personality Profile

Personality Profile 用于描述 Character 的性格特征。

该字段仅作为长期设定参考。

不得保存：

- Runtime Emotion
- Temporary State

允许为空。

---

### OF-004 Extension Fields

用于扩展 Character 专属 Content，不得修改或覆盖 Foundation 定义的 Metadata。

扩展字段：

- 不得修改 Required Fields。
- 不得覆盖 Foundation 定义。
- 必须保持向后兼容。

---

## 4.6 Relationships

Character Asset 可以与其他 Asset 建立长期稳定（Canonical）的引用关系。

Relationships 用于建立 Asset 之间的关联。

Relationships：

- 必须引用 Asset ID。
- 不得复制 Asset 内容。
- 不得引用 Runtime Data。
- 不得建立循环依赖。
- 不得引用 Composition Asset（例如 Configuration）。

Relationship 仅定义关联规则。

具体引用内容由 Asset Instance 定义。

---

### CR-001 Outfit Relationship

Character 可以引用 Outfit Asset。

用于建立 Character 与 Canonical Outfit Asset 的长期引用关系。

Character 可以不存在 Outfit Relationship。

当建立该 Relationship 时，
必须引用 Outfit Asset ID。

---

### CR-002 Component Relationship

Character 可以引用 Component Asset。

用于建立长期稳定的角色组件。

例如：

- 固定义体
- 固定尾巴
- 固定翅膀

Character 不保存 Component 内容。

仅保存 Component Asset ID。

---

### CR-003 World Relationship

Character 可以引用 World Asset。

用于建立 Character 与 World Asset 的长期设定关系。

Character 不保存 World 内容。

仅保存 World Asset ID。

---

### CR-004 Relationship Constraints

所有 Relationship 必须遵循以下规则：

- 必须使用 Asset ID 引用。
- 一个 Relationship 不得保存业务数据。
- 不得形成循环依赖。
- 不得引用 Runtime Asset。
- 不得引用 Configuration Asset。

---

## 4.7 Constraints

Character Asset 必须遵循以下约束。

所有约束用于保证 Character Asset 的一致性、
独立性与长期稳定性。

违反任意 Constraint，

Asset 不符合 Character Data Model。

---

### CC-001 Identity Immutability

Character Identity 必须保持稳定。

Identity 一经建立，

不得因 Outfit、Configuration、State 或 Runtime Data 而改变。

---

### CC-002 Immutable Appearance

Immutable Appearance 必须仅包含角色的基础外观。

不得包含任何
非 Character 固有属性。

---

### CC-003 Visual DNA Stability

Visual DNA 必须保持长期稳定。

Visual DNA 不得依赖：

- Outfit
- Scene
- Configuration
- Runtime State

Visual DNA 的目标是保证 Character 在不同表现形式下仍具有一致的辨识度。

---

### CC-004 Reference Integrity

Character 的所有 Relationship 必须：

- 保持长期稳定（Canonical）
- 保持单向引用（Reference）
- 不得形成循环依赖
- 不得引用 Runtime Asset
- 不得引用 Composition Asset（例如 Configuration）

Character 仅负责 Identity Asset。

---

### CC-005 Single Responsibility

Character 仅负责描述角色本身。

不得承担以下职责：

- Outfit Definition
- Component Definition
- Scene Definition
- Configuration Definition
- State Definition
- Shot Definition

---

### CC-006 Foundation Compliance

Character Data Model 必须继承 Foundation。

不得：

- 修改 Foundation 定义。
- 覆盖 Foundation 字段。
- 重新定义 Foundation 的 Header、Metadata、Relationships、Status、Validation、Version。

Character Data Model 仅扩展 Character 专属 Content。

---

## 4.8 Validation Rules

Character Asset 在进入正式使用前，

必须通过 Character Validation。

Character Validation 用于验证：

- Required Fields
- Optional Fields（如存在）
- Relationships
- Constraints
- Foundation Compliance

Validation 不定义新的规范。

Validation 仅验证 Character Asset 是否符合本 Data Model。

---

### CV-001 Required Fields Validation

验证 Character 是否包含所有 Required Fields。

检查项：

- Identity
- Immutable Appearance
- Visual DNA
- Foundation Inheritance

缺少任意 Required Field，

Validation Failed。

---

### CV-002 Optional Fields Validation

若 Optional Fields 存在，

必须符合其定义。

检查项：

- Character References
- Biography
- Personality Profile
- Extension Fields

Optional Fields 可以为空。

但存在时必须合法。

---

### CV-003 Relationship Validation

验证所有 Relationship。

检查项：

- 是否引用合法 Asset ID
- 是否符合 Character Data Model 定义的 Relationship Rules
- 是否不存在非法 Relationship

---

### CV-004 Constraint Validation

验证 Character 是否符合所有 Constraints。

检查项：

- Identity Immutability
- Immutable Appearance
- Visual DNA Stability
- Relationship Consistency
- Single Responsibility
- Foundation Compliance

违反任意 Constraint，

Validation Failed。

---

### CV-005 Foundation Validation

验证 Character 是否正确继承 Foundation。

检查项：

- Header
- Metadata
- Relationships
- Status
- Validation
- Version

不得修改 Foundation 定义。

不得覆盖 Foundation 字段。

Foundation Validation 应以
《02_Asset_Specification_01_Foundation》
为唯一依据。

---

## 4.9 Extension Points

Character Data Model 支持未来扩展。

所有扩展必须保持：

- 向后兼容（Backward Compatibility）
- 架构一致性（Architecture Consistency）
- Foundation 兼容性（Foundation Compliance）

扩展不得破坏既有 Character Data Model。

---

### EP-001 Content Extension

Character 可扩展新的 Character 专属 Content。

新增 Content：

- 必须符合 Character 职责。
- 不得修改已有 Required Fields。
- 不得覆盖已有 Optional Fields。
- 不得改变已有字段的语义（Semantic）。

---

### EP-002 Relationship Extension

Character 可新增与未来 Asset 的长期稳定引用关系。

新增 Relationship：

- 必须采用 Reference。
- 必须保持 Canonical。
- 不得引用 Runtime Asset。
- 不得形成循环依赖。

---

### EP-003 Validation Extension

Character 可新增 Validation Rules。

新增 Validation：

- 必须基于已有规范。
- 不得降低已有 Validation 的严格程度。

---

### EP-004 Version Compatibility

Character Data Model 的未来版本：

- 必须保持向后兼容。
- 不得删除已有 Required Fields。
- 不得修改 Foundation 定义。

如需进行破坏性修改，

必须升级 Major Version。

---

### EP-005 Extension Principles

所有扩展必须遵循以下原则：

- 不修改 Foundation。
- 不破坏 Character Identity。
- 不改变 Character 职责。
- 不引入 Runtime Data。
- 不影响其他 Asset 的独立性。

---

# 5. Outfit Data Model

## 5.1 Purpose

Outfit Data Model 用于定义 Outfit Asset 的标准数据模型。

Outfit Asset 的职责是定义角色的可替换视觉层（Replaceable Visual Layer）。

Outfit Asset 用于描述角色的穿戴、装备及其他长期稳定的可替换外观。

Outfit Asset 是角色的标准视觉资产（Visual Asset）。

Outfit Data Model 定义的是：

> 一个角色「穿什么（What the Character Wears）」。

而不是：

> 一个角色「是谁（Who the Character Is）」。

Outfit Data Model 必须符合：

- 00_Core_Principles.md
- 01_Architecture.md
- 02_Asset_Specification_01_Foundation.md

---

## 5.2 Scope

Outfit Data Model 的 Scope 为：

定义角色在整个 AVPS 生命周期内保持稳定的可替换视觉内容（Replaceable Visual Content）。

Outfit Data Model 负责定义：

- 角色的穿戴（Wearables）
- 角色的装备（Equipment）
- Outfit 的长期视觉定义
- Outfit 与其他 Asset 的 Canonical Relationship

Outfit Data Model 不负责：

- Character Identity
- Character 的基础外观（Immutable Appearance）
- Character 的视觉识别特征（Visual DNA）
- Runtime Configuration
- Runtime State
- Scene
- Shot
- Prompt
- AI Generation

上述内容均由对应 Asset 独立管理。

Outfit Data Model 仅描述：

> 一个角色「穿什么（What the Character Wears）」。

不描述：

> 一个角色「是谁（Who the Character Is）」。

也不描述：

> 一个角色「当前处于什么状态（Current State）」。

Outfit Asset 应保持独立。

其职责边界由本 Data Model 定义。

与其他 Asset 的关联方式，
由 Relationships 定义。

---

## 5.3 Data Structure

Outfit Data Model 建立于 Asset Foundation 之上。

Foundation 中定义的：

- Header
- Metadata
- Relationships
- Status
- Validation
- Version

全部继承。

Outfit Data Model 仅定义 Outfit 专属 Content。

标准结构如下：

```text
Outfit Asset
│
├── Header                    (Inherited)
├── Metadata                  (Inherited)
├── Content
│   ├── Identity
│   ├── Visual Definition
│   ├── Outfit Composition
│   └── Outfit References
├── Relationships             (Inherited)
├── Status                    (Inherited)
├── Validation                (Inherited)
└── Version                   (Inherited)
```

其中：

### Identity

定义 Outfit 的唯一身份信息。

负责回答：

> 这是哪一个 Outfit？

Identity 不受：

- Character
- Configuration
- State

影响。

---

### Visual Definition

定义 Outfit 的长期稳定视觉特征。

Visual Definition 仅包含 Outfit 自身的视觉定义。

例如：

- Clothing Style
- Materials
- Color Scheme
- Design Features

Visual Definition 不包含：

- Character Identity
- Runtime State
- Scene Information

---

### Outfit Composition

定义 Outfit 的组成结构。

Outfit Composition 用于描述 Outfit 包含哪些长期稳定的组成部分。

Outfit Composition 不保存：

- Runtime Configuration
- Runtime State

Outfit Composition 仅描述 Outfit 本身。

---

### Outfit References

Outfit References 定义 Outfit 与其他长期稳定 Asset 的规范引用关系（Canonical References）。

仅保存 Canonical Reference。

不保存运行时配置。

例如：

- Default Components
- Compatible Character

所有引用均必须使用 Asset ID。

不得复制 Asset 内容。

---

## 5.4 Required Fields

Required Fields 定义 Outfit Asset 成立所必需的数据。

若缺少任一 Required Field，

Outfit Asset 将无法正确建立其身份、职责或核心视觉定义。

Required Fields 的判定原则应遵循：

> 移除该字段后，
> 若 Outfit Asset 不再成立，则该字段属于 Required Field。

所有 Required Fields 应：

- 直接支持 Outfit Asset 的核心职责。
- 保持长期稳定（Canonical）。
- 独立于 Runtime Configuration。
- 独立于 Runtime State。
- 符合 Foundation 定义的 Field 规范。

Required Fields 仅包含 Outfit Asset 自身必需的信息。

不得要求：

- Character 必须存在。
- Component 必须存在。
- Configuration 必须存在。
- Scene 必须存在。

任何依赖其他 Asset 的关联，

均应通过 Canonical Reference 建立，

而非作为 Outfit 成立的前置条件。

具体 Required Fields 将依据本章定义的 Data Structure 分类：

- Identity
- Visual Definition
- Outfit Composition

---

### RF-001 Identity

Outfit Asset 必须包含 Identity。

Identity 用于定义 Outfit 的唯一身份。

Identity 为 Outfit 的核心字段。

不得缺失。

---

### RF-002 Visual Definition

Outfit Asset 必须包含 Visual Definition。

Visual Definition 用于定义 Outfit 的长期稳定视觉特征。

不得包含：

- Character Identity
- Runtime State
- Scene Information

---

### RF-003 Outfit Composition

Outfit Asset 必须包含 Outfit Composition。

Outfit Composition 用于定义 Outfit 的长期稳定组成结构。

Outfit Composition 不得保存：

- Runtime Configuration
- Runtime State

---

### RF-004 Inherited Foundation Fields

除 Outfit 专属字段外，

Outfit Asset 必须继承 Foundation 定义的全部基础字段。

包括：

- Header
- Metadata
- Relationships
- Status
- Validation
- Version

上述字段不得删除。

不得重新定义。

Outfit Data Model 仅扩展 Outfit 专属 Content。

不得修改 Foundation。

---

## 5.5 Optional Fields

Optional Fields 定义 Outfit Asset 可选择包含的数据。

Optional Fields 用于扩展 Outfit Asset 的能力，

但不是 Outfit Asset 成立的必要条件。

若缺少 Optional Field，

Outfit Asset 仍然有效。

Optional Fields 的判定原则应遵循：

> 移除该字段后，
> 若 Outfit Asset 仍然成立，
> 仅能力、信息或可复用性降低，
> 则该字段属于 Optional Field。

所有 Optional Fields 应：

- 保持与 Outfit Asset 职责一致。
- 保持长期稳定（Canonical）。
- 独立于 Runtime Configuration。
- 独立于 Runtime State。
- 符合 Foundation 定义的 Field 规范。

Optional Fields 不得：

- 改变 Outfit Asset 的核心职责。
- 覆盖 Required Fields。
- 修改 Foundation 定义。

具体 Optional Fields 包括：

- Outfit References
- Description
- Tags
- Extension Fields

---

### OF-001 Outfit References

Outfit References 为 Optional Field。

用于保存 Outfit 的 Canonical Relationships。

Outfit 可以不存在任何 References。

References 的定义规则应遵循：

5.6 Relationships。

---

### OF-002 Description

Description 为 Optional Field。

Description 用于补充说明 Outfit 的设计目的或使用说明。

Description 不参与 Asset Identity。

Description 不影响 Validation。

---

### OF-003 Tags

Tags 为 Optional Field。

Tags 用于资产分类、检索及管理。

Tags 不影响 Outfit Asset 的语义。

Tags 不参与 Asset Identity。

---

### OF-004 Extension Fields

Extension Fields 为 Optional Field。

Extension Fields 用于支持未来扩展。

所有 Extension Fields：

- 不得修改 Required Fields。
- 不得覆盖 Foundation 字段。
- 不得改变 Outfit Asset 的核心职责。
- 必须保持向后兼容（Backward Compatibility）。

---

## 5.6 Relationships

Relationships 定义 Outfit Asset 与其他 Asset 的长期稳定（Canonical）引用关系。

Relationships 用于建立 Asset 之间的关联。

Relationships：

- 必须引用 Asset ID。
- 不得复制 Asset 内容。
- 不得引用 Runtime Data。
- 不得建立循环依赖。
- 不得引用 Composition Asset（例如 Configuration）。

Relationship 仅定义关联规则。

具体引用内容由 Asset Instance 定义。

---

### OR-001 Character Relationship

Outfit 可以引用 Character Asset。

用于建立 Outfit 与 Canonical Character Asset 的长期引用关系。

Outfit 可以不存在 Character Relationship。

当建立该 Relationship 时，

必须引用 Character Asset ID。

---

### OR-002 Component Relationship

Outfit 可以引用 Component Asset。

用于建立 Outfit 与长期稳定 Component 的引用关系。

例如：

- Clothing Component
- Armor Component
- Accessory Component

Outfit 不保存 Component 内容。

仅保存 Component Asset ID。

---

### OR-003 Prop Relationship

Outfit 可以引用 Prop Asset。

用于建立 Outfit 与长期稳定 Prop 的引用关系。

例如：

- Default Weapon
- Default Shield
- Default Equipment

Outfit 不保存 Prop 内容。

仅保存 Prop Asset ID。

---

### OR-004 Relationship Constraints

所有 Relationship 必须遵循以下规则：

- 必须使用 Asset ID 引用。
- 一个 Relationship 不得保存业务数据。
- 不得形成循环依赖。
- 不得引用 Runtime Asset。
- 不得引用 Configuration Asset（例如 Configuration）。

---

## 5.7 Constraints

Constraints 定义 Outfit Asset 必须遵循的业务规则与一致性要求。

Constraints 用于确保 Outfit Asset 在整个 AVPS 中保持一致、完整及可复用。

所有 Constraints 均适用于 Outfit Asset 的 Canonical Data。

不适用于：

- Runtime Configuration
- Runtime State
- Temporary Composition

---

### OC-001 Identity Integrity

Outfit Identity 必须唯一。

Identity 一经建立，不得用于表示其他 Outfit Asset。

Identity 的变更应遵循 Asset Versioning 规范。

---

### OC-002 Responsibility Boundary

Outfit Asset 仅负责定义角色的可替换视觉层（Replaceable Visual Layer）。

Outfit Asset 不得承担：

- Character Identity
- Runtime Configuration
- Runtime State
- Scene Information
- Shot Information

任何超出 Outfit 职责范围的数据，

均应由对应 Asset 管理。

---

### OC-003 Canonical Data Only

Outfit Asset 仅保存长期稳定（Canonical）的数据。

不得保存：

- Runtime Data
- Temporary Data
- Generated Results
- Session-specific Data

---

### OC-004 Reference Integrity

所有 References 必须引用合法的 Asset ID。

不得：

- 引用不存在的 Asset。
- 复制其他 Asset 内容。
- 建立循环依赖。
- 引用 Runtime Asset。

---

### OC-005 Outfit Composition Consistency

Outfit Composition 必须描述 Outfit 的长期稳定组成结构。

Outfit Composition 不得：

- 保存 Runtime Configuration。
- 保存 Runtime State。
- 修改其他 Asset 的定义。

Outfit Composition 应保持独立，并符合 Outfit Asset 的职责边界。

---

### OC-006 Foundation Compliance

Outfit Asset 必须继承 Foundation 定义。

不得：

- 删除 Foundation Required Fields。
- 修改 Foundation 的语义。
- 覆盖 Foundation 的 Validation Rules。

Outfit Data Model 仅允许扩展 Outfit 专属 Content。

不得修改 Foundation 的基础规范。

---

## 5.8 Validation Rules

Validation Rules 定义 Outfit Asset 必须满足的数据完整性与一致性要求。

Validation 用于验证 Outfit Asset 是否符合本规范。

Validation 不修改数据。

Validation 仅负责检查数据是否合法。

Validation 应在 Asset 创建、更新及发布时执行。

---

### OV-001 Required Field Validation

所有 Required Fields 必须存在。

若缺少任何 Required Field，

Validation 应返回 Failed。

---

### OV-002 Identity Validation

Identity 必须符合 Identity 规范。

Validation 应检查：

- Identity 是否存在。
- Identity 是否唯一。
- Identity 是否符合命名规范。

重复 Identity 不得通过 Validation。

---

### OV-003 Visual Definition Validation

Visual Definition 必须完整。

Validation 应检查：

- Required Visual Definition 是否存在。
- 不得包含 Runtime Data。
- 不得包含 Character Identity。
- 不得包含 Scene Information。

---

### OV-004 Composition Validation

Outfit Composition 必须符合 Outfit Data Model。

Validation 应检查：

- Outfit Composition 是否存在。
- Outfit Composition 是否符合定义。
- 不得包含 Runtime Configuration。
- 不得包含 Runtime State。

---

### OV-005 Relationship Validation

所有 Relationships 必须合法。

Validation 应检查：

- Reference 是否使用合法 Asset ID。
- Reference 是否指向存在的 Asset。
- 不得形成循环依赖。
- 不得引用 Runtime Asset。
- 不得引用 Configuration Asset。

---

### OV-006 Foundation Validation

Outfit Asset 必须符合 Foundation。

Validation 应检查：

- Foundation Required Fields 是否完整。
- Foundation Metadata 是否合法。
- Foundation Validation Rules 是否满足。

不得覆盖 Foundation Validation。

---

### OV-007 Specification Compliance

Outfit Asset 必须符合：

- 00_Core_Principles
- 01_Architecture
- 02_Asset_Specification_01_Foundation
- 02_Asset_Specification_02_Data_Models

任何违反上述规范的 Outfit Asset，

均不得通过 Validation。

---

## 5.9 Extension Points

Extension Points 定义 Outfit Data Model 在未来允许扩展的位置。

所有扩展必须保持：

- Backward Compatibility（向后兼容）
- Architecture Consistency（架构一致性）
- Foundation Compliance（Foundation 一致性）

扩展不得破坏既有 Outfit Data Model。

---

### EP-001 Content Extension

Outfit 可扩展新的 Outfit 专属 Content。

新增 Content：

- 必须符合 Outfit 职责。
- 不得修改已有 Required Fields。
- 不得覆盖已有 Optional Fields。
- 不得改变已有字段的语义（Semantic）。

---

### EP-002 Relationship Extension

Outfit 可新增与未来 Asset 的长期稳定（Canonical）引用关系。

新增 Relationship：

- 必须采用 Reference。
- 必须保持 Canonical。
- 不得引用 Runtime Asset。
- 不得形成循环依赖。

---

### EP-003 Validation Extension

Outfit 可新增 Validation Rules。

新增 Validation：

- 必须基于已有规范。
- 不得降低已有 Validation 的严格程度。
- 不得覆盖 Foundation Validation。

---

### EP-004 Version Compatibility

Outfit Data Model 的未来版本：

- 必须保持向后兼容。
- 不得删除已有 Required Fields。
- 不得修改 Foundation 定义。

如需进行破坏性修改，

必须升级 Major Version。

---

### EP-005 Extension Principles

所有扩展必须遵循以下原则：

- 不修改 Foundation。
- 不改变 Outfit 职责。
- 不引入 Runtime Data。
- 不破坏 Canonical Relationships。
- 不影响其他 Asset 的独立性。

---

# 6. Component Data Model

## 6.1 Purpose

Component Data Model 用于定义 Component Asset 的标准数据模型。

Component Asset 的职责是定义可复用的视觉组成单元（Reusable Visual Component）。

Component Asset 用于描述可独立管理、可重复组合及可跨 Asset 复用的视觉组件。

Component Asset 是系统的标准组件资产（Component Asset）。

Component Data Model 定义的是：

> 一个可复用组件「是什么（What the Component Is）」。

而不是：

> 一个角色「是谁（Who the Character Is）」。

也不是：

> 一个角色「穿什么（What the Character Wears）」。

Component Data Model 必须符合：

- 00_Core_Principles.md
- 01_Architecture.md
- 02_Asset_Specification_01_Foundation.md

---

## 6.2 Scope

Component Data Model 的 Scope 为：

定义可独立管理、可重复组合及可跨 Asset 复用的长期稳定组件（Reusable Canonical Components）。

Component Data Model 负责定义：

- Component 的身份（Identity）
- Component 的长期稳定定义
- Component 的组成特征
- Component 与其他 Asset 的 Canonical Relationships

Component Data Model 不负责：

- Character Identity
- Outfit Definition
- Runtime Configuration
- Runtime State
- Scene
- Shot
- Prompt
- AI Generation

上述内容均由对应 Asset 独立管理。

Component Data Model 仅描述：

> 一个可复用组件「是什么（What the Component Is）」。

不描述：

> 一个角色「是谁（Who the Character Is）」。

也不描述：

> 一个角色「穿什么（What the Character Wears）」。

更不描述：

> 一个组件「当前如何被使用（How the Component Is Currently Used）」。

Component Asset 应保持独立。

Component 与 Character、Outfit、Prop、Configuration、State 等 Asset，

均通过 Reference 建立关联，

不得承担其他 Asset 的职责。

---

## 6.3 Data Structure

Component Data Model 建立于 Asset Foundation 之上。

Foundation 中定义的：

- Header
- Metadata
- Relationships
- Status
- Validation
- Version

全部继承。

Component Data Model 仅定义 Component 专属 Content。

标准结构如下：

```text
Component Asset
│
├── Header                    (Inherited)
├── Metadata                  (Inherited)
├── Content
│   ├── Identity
│   ├── Component Definition
│   ├── Component Composition
│   └── Component References
├── Relationships             (Inherited)
├── Status                    (Inherited)
├── Validation                (Inherited)
└── Version                   (Inherited)
```

其中：

### Identity

定义 Component 的唯一身份信息。

负责回答：

> 这是哪一个 Component？

Identity 不受：

- Character
- Outfit
- Configuration
- State

影响。

---

### Component Definition

定义 Component 的长期稳定定义。

Component Definition 仅包含 Component 自身的规范定义。

例如：

- Component Type
- Visual Characteristics
- Structural Properties
- Functional Purpose

Component Definition 不包含：

- Runtime Configuration
- Runtime State
- Scene Information

---

### Component Composition

定义 Component 的组成结构。

Component Composition 用于描述 Component 的长期稳定组成结构。

Component Composition 不保存：

- Runtime Configuration
- Runtime State

Component Composition 仅描述 Component 本身。

---

### Component References

Component References 定义 Component 与其他长期稳定 Asset 的规范引用关系（Canonical References）。

仅保存 Canonical References。

不保存运行时配置。

例如：

- Compatible Outfit
- Compatible Character
- Dependent Component

所有引用均必须使用 Asset ID。

不得复制 Asset 内容。

---

## 6.4 Required Fields

Required Fields 定义 Component Asset 成立所必需的数据。

若缺少任一 Required Field，

Component Asset 将无法正确建立其身份、职责或核心定义。

Required Fields 的判定原则应遵循：

> 移除该字段后，
> 若 Component Asset 不再成立，
> 则该字段属于 Required Field。

所有 Required Fields 应：

- 直接支持 Component Asset 的核心职责。
- 保持长期稳定（Canonical）。
- 独立于 Runtime Configuration。
- 独立于 Runtime State。
- 符合 Foundation 定义的 Field 规范。

Required Fields 仅包含 Component Asset 自身必需的信息。

不得要求：

- Character 必须存在。
- Outfit 必须存在。
- Scene 必须存在。
- Configuration 必须存在。

任何依赖其他 Asset 的关联，

均应通过 Canonical Reference 建立，

而非作为 Component 成立的前置条件。

具体 Required Fields 将依据本章定义的 Data Structure 分类：

- Identity
- Component Definition
- Component Composition

---

### RF-001 Identity

Component Asset 必须包含 Identity。

Identity 用于定义 Component 的唯一身份。

Identity 为 Component 的核心字段。

不得缺失。

---

### RF-002 Component Definition

Component Asset 必须包含 Component Definition。

Component Definition 用于定义 Component 的长期稳定规范。

不得包含：

- Runtime Configuration
- Runtime State
- Scene Information

---

### RF-003 Component Composition

Component Asset 必须包含 Component Composition。

Component Composition 用于定义 Component 的长期稳定组成结构。

Component Composition 不得保存：

- Runtime Configuration
- Runtime State

---

### RF-004 Inherited Foundation Fields

除 Component 专属字段外，

Component Asset 必须继承 Foundation 定义的全部基础字段。

包括：

- Header
- Metadata
- Relationships
- Status
- Validation
- Version

上述字段不得删除。

不得重新定义。

Component Data Model 仅扩展 Component 专属 Content。

不得修改 Foundation。

---

## 6.5 Optional Fields

Optional Fields 定义 Component Asset 可选择包含的数据。

Optional Fields 用于扩展 Component Asset 的能力，

但不是 Component Asset 成立的必要条件。

若缺少 Optional Field，

Component Asset 仍然有效。

Optional Fields 的判定原则应遵循：

> 移除该字段后，
> 若 Component Asset 仍然成立，
> 仅能力、信息或可复用性降低，
> 则该字段属于 Optional Field。

所有 Optional Fields 应：

- 保持与 Component Asset 职责一致。
- 保持长期稳定（Canonical）。
- 独立于 Runtime Configuration。
- 独立于 Runtime State。
- 符合 Foundation 定义的 Field 规范。

Optional Fields 不得：

- 改变 Component Asset 的核心职责。
- 覆盖 Required Fields。
- 修改 Foundation 定义。

具体 Optional Fields 包括：

- Component References
- Description
- Tags
- Extension Fields

---

### OF-001 Component References

Component References 为 Optional Field。

用于保存 Component 的 Canonical Relationships。

Component 可以不存在任何 References。

References 的定义规则应遵循：

6.6 Relationships。

---

### OF-002 Description

Description 为 Optional Field。

Description 用于补充说明 Component 的设计目的、功能或使用说明。

Description 不参与 Asset Identity。

Description 不影响 Validation。

---

### OF-003 Tags

Tags 为 Optional Field。

Tags 用于资产分类、检索及管理。

Tags 不影响 Component Asset 的语义。

Tags 不参与 Asset Identity。

---

### OF-004 Extension Fields

Extension Fields 为 Optional Field。

Extension Fields 用于支持未来扩展。

所有 Extension Fields：

- 不得修改 Required Fields。
- 不得覆盖 Foundation 字段。
- 不得改变 Component Asset 的核心职责。
- 必须保持向后兼容（Backward Compatibility）。

---

## 6.6 Relationships

Relationships 定义 Component Asset 与其他 Asset 的长期稳定（Canonical）引用关系。

Relationships 用于建立 Asset 之间的关联。

Relationships：

- 必须引用 Asset ID。
- 不得复制 Asset 内容。
- 不得引用 Runtime Data。
- 不得建立循环依赖。
- 不得引用 Composition Asset（例如 Configuration）。

Relationship 仅定义关联规则。

具体引用内容由 Asset Instance 定义。

---

### COR-001 Character Relationship

Component 可以引用 Character Asset。

用于建立 Component 与 Canonical Character Asset 的长期引用关系。

Component 可以不存在 Character Relationship。

当建立该 Relationship 时，

必须引用 Character Asset ID。

---

### COR-002 Outfit Relationship

Component 可以引用 Outfit Asset。

用于建立 Component 与 Canonical Outfit Asset 的长期引用关系。

例如：

- Default Outfit
- Compatible Outfit

Component 不保存 Outfit 内容。

仅保存 Outfit Asset ID。

---

### COR-003 Component Relationship

Component 可以引用其他 Component Asset。

用于建立 Component 之间的长期引用关系。

例如：

- Parent Component
- Child Component
- Dependency Component

Component 不保存其他 Component 的内容。

仅保存 Component Asset ID。

---

### COR-004 Relationship Constraints

所有 Relationship 必须遵循以下规则：

- 必须使用 Asset ID 引用。
- 一个 Relationship 不得保存业务数据。
- 不得形成循环依赖。
- 不得引用 Runtime Asset。
- 不得引用 Configuration Asset（例如 Configuration）。

---

## 6.7 Constraints

Constraints 定义 Component Asset 必须遵循的业务规则与一致性要求。

Constraints 用于确保 Component Asset 在整个 AVPS 中保持一致、完整及可复用。

所有 Constraints 均适用于 Component Asset 的 Canonical Data。

不适用于：

- Runtime Configuration
- Runtime State
- Temporary Composition

---

### CC-001 Identity Integrity

Component Identity 必须唯一。

Identity 一经建立，不得用于表示其他 Component Asset。

Identity 的变更应遵循 Asset Versioning 规范。

---

### CC-002 Responsibility Boundary

Component Asset 仅负责定义可复用的视觉组成单元（Reusable Visual Component）。

Component Asset 不得承担：

- Character Identity
- Outfit Definition
- Runtime Configuration
- Runtime State
- Scene Information
- Shot Information

任何超出 Component 职责范围的数据，

均应由对应 Asset 管理。

---

### CC-003 Canonical Data Only

Component Asset 仅保存长期稳定（Canonical）的数据。

不得保存：

- Runtime Data
- Temporary Data
- Generated Results
- Session-specific Data

---

### CC-004 Reference Integrity

所有 References 必须引用合法的 Asset ID。

不得：

- 引用不存在的 Asset。
- 复制其他 Asset 内容。
- 建立循环依赖。
- 引用 Runtime Asset。

---

### CC-005 Component Composition Consistency

Component Composition 必须描述 Component 的长期稳定组成结构。

Component Composition 不得：

- 保存 Runtime Configuration。
- 保存 Runtime State。
- 修改其他 Asset 的定义。

Component Composition 应保持独立，并符合 Component Asset 的职责边界。

---

### CC-006 Foundation Compliance

Component Asset 必须继承 Foundation 定义。

不得：

- 删除 Foundation Required Fields。
- 修改 Foundation 的语义。
- 覆盖 Foundation 的 Validation Rules。

Component Data Model 仅允许扩展 Component 专属 Content。

不得修改 Foundation 的基础规范。

---

## 6.8 Validation Rules

Validation Rules 定义 Component Asset 必须满足的数据完整性与一致性要求。

Validation 用于验证 Component Asset 是否符合本规范。

Validation 不修改数据。

Validation 仅负责检查数据是否合法。

Validation 应在 Asset 创建、更新及发布时执行。

---

### CV-001 Required Field Validation

所有 Required Fields 必须存在。

若缺少任何 Required Field，

Validation 应返回 Failed。

---

### CV-002 Identity Validation

Identity 必须符合 Identity 规范。

Validation 应检查：

- Identity 是否存在。
- Identity 是否唯一。
- Identity 是否符合命名规范。

重复 Identity 不得通过 Validation。

---

### CV-003 Component Definition Validation

Component Definition 必须完整。

Validation 应检查：

- Required Component Definition 是否存在。
- 不得包含 Runtime Data。
- 不得包含 Scene Information。
- 不得包含 Runtime Configuration。

---

### CV-004 Component Composition Validation

Component Composition 必须符合 Component Data Model。

Validation 应检查：

- Component Composition 是否存在。
- Component Composition 是否符合定义。
- 不得包含 Runtime Configuration。
- 不得包含 Runtime State。

---

### CV-005 Relationship Validation

所有 Relationships 必须合法。

Validation 应检查：

- Reference 是否使用合法 Asset ID。
- Reference 是否指向存在的 Asset。
- 不得形成循环依赖。
- 不得引用 Runtime Asset。
- 不得引用 Configuration Asset。

---

### CV-006 Foundation Validation

Component Asset 必须符合 Foundation。

Validation 应检查：

- Foundation Required Fields 是否完整。
- Foundation Metadata 是否合法。
- Foundation Validation Rules 是否满足。

不得覆盖 Foundation Validation。

---

### CV-007 Specification Compliance

Component Asset 必须符合：

- 00_Core_Principles
- 01_Architecture
- 02_Asset_Specification_01_Foundation
- 02_Asset_Specification_02_Data_Models

任何违反上述规范的 Component Asset，

均不得通过 Validation。

---

## 6.9 Extension Points

Extension Points 定义 Component Data Model 在未来允许扩展的位置。

所有扩展必须保持：

- Backward Compatibility（向后兼容）
- Architecture Consistency（架构一致性）
- Foundation Compliance（Foundation 一致性）

扩展不得破坏既有 Component Data Model。

---

### EP-001 Content Extension

Component 可扩展新的 Component 专属 Content。

新增 Content：

- 必须符合 Component 职责。
- 不得修改已有 Required Fields。
- 不得覆盖已有 Optional Fields。
- 不得改变已有字段的语义（Semantic）。

---

### EP-002 Relationship Extension

Component 可新增与未来 Asset 的长期稳定（Canonical）引用关系。

新增 Relationship：

- 必须采用 Reference。
- 必须保持 Canonical。
- 不得引用 Runtime Asset。
- 不得形成循环依赖。

---

### EP-003 Validation Extension

Component 可新增 Validation Rules。

新增 Validation：

- 必须基于已有规范。
- 不得降低已有 Validation 的严格程度。
- 不得覆盖 Foundation Validation。

---

### EP-004 Version Compatibility

Component Data Model 的未来版本：

- 必须保持向后兼容。
- 不得删除已有 Required Fields。
- 不得修改 Foundation 定义。

如需进行破坏性修改，

必须升级 Major Version。

---

### EP-005 Extension Principles

所有扩展必须遵循以下原则：

- 不修改 Foundation。
- 不改变 Component 职责。
- 不引入 Runtime Data。
- 不破坏 Canonical Relationships。
- 不影响其他 Asset 的独立性。

---

# 7. Scene Data Model

## 7.1 Purpose

Scene Data Model 用于定义 Scene Asset 的标准数据模型。

Scene Asset 的职责是定义可复用的场景环境（Reusable Scene Environment）。

Scene Asset 用于描述长期稳定的空间、环境及场景组成。

Scene Asset 是系统的标准场景资产（Scene Asset）。

Scene Data Model 定义的是：

> 一个场景「是什么（What the Scene Is）」。

而不是：

> 一个角色「是谁（Who the Character Is）」。

也不是：

> 一个角色「穿什么（What the Character Wears）」。

更不是：

> 一个场景「当前发生了什么（What Is Happening in the Scene）」。

Scene Data Model 必须符合：

- 00_Core_Principles.md
- 01_Architecture.md
- 02_Asset_Specification_01_Foundation.md

---

## 7.2 Scope

Scene Data Model 的 Scope 为：

定义长期稳定、可复用的场景环境（Reusable Canonical Scenes）。

Scene Data Model 负责定义：

- Scene 的身份（Identity）
- Scene 的长期稳定定义
- Scene 的环境组成
- Scene 与其他 Asset 的 Canonical Relationships

Scene Data Model 不负责：

- Character Identity
- Outfit Definition
- Component Definition
- Runtime Configuration
- Runtime State
- Shot
- Prompt
- AI Generation

上述内容均由对应 Asset 独立管理。

Scene Data Model 仅描述：

> 一个场景「是什么（What the Scene Is）」。

不描述：

> 一个角色「是谁（Who the Character Is）」。

也不描述：

> 一个角色「穿什么（What the Character Wears）」。

更不描述：

> 一个场景「当前发生了什么（What Is Happening in the Scene）」。

Scene Asset 应保持独立。

Scene 与 Character、Outfit、Component、Prop、Configuration、State 等 Asset，

均通过 Reference 建立关联，

不得承担其他 Asset 的职责。

---

## 7.3 Data Structure

Scene Data Model 建立于 Asset Foundation 之上。

Foundation 中定义的：

- Header
- Metadata
- Relationships
- Status
- Validation
- Version

全部继承。

Scene Data Model 仅定义 Scene 专属 Content。

标准结构如下：

```text
Scene Asset
│
├── Header                    (Inherited)
├── Metadata                  (Inherited)
├── Content
│   ├── Identity
│   ├── Scene Definition
│   ├── Scene Composition
│   └── Scene References
├── Relationships             (Inherited)
├── Status                    (Inherited)
├── Validation                (Inherited)
└── Version                   (Inherited)
```

其中：

### Identity

定义 Scene 的唯一身份信息。

负责回答：

> 这是哪一个 Scene？

Identity 不受：

- Character
- Outfit
- Configuration
- State

影响。

---

### Scene Definition

定义 Scene 的长期稳定定义。

Scene Definition 仅包含 Scene 自身的规范定义。

例如：

- Environment Type
- Spatial Characteristics
- Visual Style
- Functional Purpose

Scene Definition 不包含：

- Runtime Configuration
- Runtime State
- Shot Information

---

### Scene Composition

定义 Scene 的组成结构。

Scene Composition 用于描述 Scene 的长期稳定组成结构。

Scene Composition 不保存：

- Runtime Configuration
- Runtime State

Scene Composition 仅描述 Scene 本身。

---

### Scene References

Scene References 定义 Scene 与其他长期稳定 Asset 的规范引用关系（Canonical References）。

仅保存 Canonical References。

不保存运行时配置。

例如：

- Default World
- Default Props
- Compatible Characters

所有引用均必须使用 Asset ID。

不得复制 Asset 内容。

---

## 7.4 Required Fields

Required Fields 定义 Scene Asset 成立所必需的数据。

若缺少任一 Required Field，

Scene Asset 将无法正确建立其身份、职责或核心定义。

Required Fields 的判定原则应遵循：

> 移除该字段后，
> 若 Scene Asset 不再成立，
> 则该字段属于 Required Field。

所有 Required Fields 应：

- 直接支持 Scene Asset 的核心职责。
- 保持长期稳定（Canonical）。
- 独立于 Runtime Configuration。
- 独立于 Runtime State。
- 符合 Foundation 定义的 Field 规范。

Required Fields 仅包含 Scene Asset 自身必需的信息。

不得要求：

- Character 必须存在。
- Outfit 必须存在。
- Component 必须存在。
- Configuration 必须存在。

任何依赖其他 Asset 的关联，

均应通过 Canonical Reference 建立，

而非作为 Scene 成立的前置条件。

具体 Required Fields 将依据本章定义的 Data Structure 分类：

- Identity
- Scene Definition
- Scene Composition

---

### RF-001 Identity

Scene Asset 必须包含 Identity。

Identity 用于定义 Scene 的唯一身份。

Identity 为 Scene 的核心字段。

不得缺失。

---

### RF-002 Scene Definition

Scene Asset 必须包含 Scene Definition。

Scene Definition 用于定义 Scene 的长期稳定规范。

不得包含：

- Runtime Configuration
- Runtime State
- Shot Information

---

### RF-003 Scene Composition

Scene Asset 必须包含 Scene Composition。

Scene Composition 用于定义 Scene 的长期稳定组成结构。

Scene Composition 不得保存：

- Runtime Configuration
- Runtime State

---

### RF-004 Inherited Foundation Fields

除 Scene 专属字段外，

Scene Asset 必须继承 Foundation 定义的全部基础字段。

包括：

- Header
- Metadata
- Relationships
- Status
- Validation
- Version

上述字段不得删除。

不得重新定义。

Scene Data Model 仅扩展 Scene 专属 Content。

不得修改 Foundation。

---

## 7.5 Optional Fields

Optional Fields 定义 Scene Asset 可选择包含的数据。

Optional Fields 用于扩展 Scene Asset 的能力，

但不是 Scene Asset 成立的必要条件。

若缺少 Optional Field，

Scene Asset 仍然有效。

Optional Fields 的判定原则应遵循：

> 移除该字段后，
> 若 Scene Asset 仍然成立，
> 仅能力、信息或可复用性降低，
> 则该字段属于 Optional Field。

所有 Optional Fields 应：

- 保持与 Scene Asset 职责一致。
- 保持长期稳定（Canonical）。
- 独立于 Runtime Configuration。
- 独立于 Runtime State。
- 符合 Foundation 定义的 Field 规范。

Optional Fields 不得：

- 改变 Scene Asset 的核心职责。
- 覆盖 Required Fields。
- 修改 Foundation 定义。

具体 Optional Fields 包括：

- Scene References
- Description
- Tags
- Extension Fields

---

### OF-001 Scene References

Scene References 为 Optional Field。

用于保存 Scene 的 Canonical Relationships。

Scene 可以不存在任何 References。

References 的定义规则应遵循：

7.6 Relationships。

---

### OF-002 Description

Description 为 Optional Field。

Description 用于补充说明 Scene 的设计目的、使用场景或环境说明。

Description 不参与 Asset Identity。

Description 不影响 Validation。

---

### OF-003 Tags

Tags 为 Optional Field。

Tags 用于资产分类、检索及管理。

Tags 不影响 Scene Asset 的语义。

Tags 不参与 Asset Identity。

---

### OF-004 Extension Fields

Extension Fields 为 Optional Field。

Extension Fields 用于支持未来扩展。

所有 Extension Fields：

- 不得修改 Required Fields。
- 不得覆盖 Foundation 字段。
- 不得改变 Scene Asset 的核心职责。
- 必须保持向后兼容（Backward Compatibility）。

---

## 7.6 Relationships

Relationships 定义 Scene Asset 与其他 Asset 的长期稳定（Canonical）引用关系。

Relationships 用于建立 Asset 之间的关联。

Relationships：

- 必须引用 Asset ID。
- 不得复制 Asset 内容。
- 不得引用 Runtime Data。
- 不得建立循环依赖。
- 不得引用 Composition Asset（例如 Configuration）。

Relationship 仅定义关联规则。

具体引用内容由 Asset Instance 定义。

---

### SR-001 World Relationship

Scene 可以引用 World Asset。

用于建立 Scene 与 Canonical World Asset 的长期引用关系。

Scene 可以不存在 World Relationship。

当建立该 Relationship 时，

必须引用 World Asset ID。

---

### SR-002 Prop Relationship

Scene 可以引用 Prop Asset。

用于建立 Scene 与长期稳定 Prop Asset 的引用关系。

例如：

- Default Props
- Environment Props
- Fixed Props

Scene 不保存 Prop 内容。

仅保存 Prop Asset ID。

---

### SR-003 Character Relationship

Scene 可以引用 Character Asset。

用于建立 Scene 与 Canonical Character Asset 的长期引用关系。

例如：

- Default Character
- Compatible Character

Scene 不保存 Character 内容。

仅保存 Character Asset ID。

---

### SR-004 Relationship Constraints

所有 Relationship 必须遵循以下规则：

- 必须使用 Asset ID 引用。
- 一个 Relationship 不得保存业务数据。
- 不得形成循环依赖。
- 不得引用 Runtime Asset。
- 不得引用 Configuration Asset（例如 Configuration）。

---

## 7.7 Constraints

Constraints 定义 Scene Asset 必须遵循的业务规则与一致性要求。

Constraints 用于确保 Scene Asset 在整个 AVPS 中保持一致、完整及可复用。

所有 Constraints 均适用于 Scene Asset 的 Canonical Data。

不适用于：

- Runtime Configuration
- Runtime State
- Temporary Composition

---

### SC-001 Identity Integrity

Scene Identity 必须唯一。

Identity 一经建立，不得用于表示其他 Scene Asset。

Identity 的变更应遵循 Asset Versioning 规范。

---

### SC-002 Responsibility Boundary

Scene Asset 仅负责定义可复用的场景环境（Reusable Scene Environment）。

Scene Asset 不得承担：

- Character Identity
- Outfit Definition
- Component Definition
- Runtime Configuration
- Runtime State
- Shot Information

任何超出 Scene 职责范围的数据，

均应由对应 Asset 管理。

---

### SC-003 Canonical Data Only

Scene Asset 仅保存长期稳定（Canonical）的数据。

不得保存：

- Runtime Data
- Temporary Data
- Generated Results
- Session-specific Data

---

### SC-004 Reference Integrity

所有 References 必须引用合法的 Asset ID。

不得：

- 引用不存在的 Asset。
- 复制其他 Asset 内容。
- 建立循环依赖。
- 引用 Runtime Asset。

---

### SC-005 Scene Composition Consistency

Scene Composition 必须描述 Scene 的长期稳定组成结构。

Scene Composition 不得：

- 保存 Runtime Configuration。
- 保存 Runtime State。
- 修改其他 Asset 的定义。

Scene Composition 应保持独立，并符合 Scene Asset 的职责边界。

---

### SC-006 Foundation Compliance

Scene Asset 必须继承 Foundation 定义。

不得：

- 删除 Foundation Required Fields。
- 修改 Foundation 的语义。
- 覆盖 Foundation 的 Validation Rules。

Scene Data Model 仅允许扩展 Scene 专属 Content。

不得修改 Foundation 的基础规范。

---

## 7.8 Validation Rules

Validation Rules 定义 Scene Asset 必须满足的数据完整性与一致性要求。

Validation 用于验证 Scene Asset 是否符合本规范。

Validation 不修改数据。

Validation 仅负责检查数据是否合法。

Validation 应在 Asset 创建、更新及发布时执行。

---

### SV-001 Required Field Validation

所有 Required Fields 必须存在。

若缺少任何 Required Field，

Validation 应返回 Failed。

---

### SV-002 Identity Validation

Identity 必须符合 Identity 规范。

Validation 应检查：

- Identity 是否存在。
- Identity 是否唯一。
- Identity 是否符合命名规范。

重复 Identity 不得通过 Validation。

---

### SV-003 Scene Definition Validation

Scene Definition 必须完整。

Validation 应检查：

- Required Scene Definition 是否存在。
- 不得包含 Runtime Data。
- 不得包含 Shot Information。
- 不得包含 Runtime Configuration。

---

### SV-004 Scene Composition Validation

Scene Composition 必须符合 Scene Data Model。

Validation 应检查：

- Scene Composition 是否存在。
- Scene Composition 是否符合定义。
- 不得包含 Runtime Configuration。
- 不得包含 Runtime State。

---

### SV-005 Relationship Validation

所有 Relationships 必须合法。

Validation 应检查：

- Reference 是否使用合法 Asset ID。
- Reference 是否指向存在的 Asset。
- 不得形成循环依赖。
- 不得引用 Runtime Asset。
- 不得引用 Configuration Asset。

---

### SV-006 Foundation Validation

Scene Asset 必须符合 Foundation。

Validation 应检查：

- Foundation Required Fields 是否完整。
- Foundation Metadata 是否合法。
- Foundation Validation Rules 是否满足。

不得覆盖 Foundation Validation。

---

### SV-007 Specification Compliance

Scene Asset 必须符合：

- 00_Core_Principles
- 01_Architecture
- 02_Asset_Specification_01_Foundation
- 02_Asset_Specification_02_Data_Models

任何违反上述规范的 Scene Asset，

均不得通过 Validation。

---

## 7.9 Extension Points

Extension Points 定义 Scene Data Model 在未来允许扩展的位置。

所有扩展必须保持：

- Backward Compatibility（向后兼容）
- Architecture Consistency（架构一致性）
- Foundation Compliance（Foundation 一致性）

扩展不得破坏既有 Scene Data Model。

---

### EP-001 Content Extension

Scene 可扩展新的 Scene 专属 Content。

新增 Content：

- 必须符合 Scene 职责。
- 不得修改已有 Required Fields。
- 不得覆盖已有 Optional Fields。
- 不得改变已有字段的语义（Semantic）。

---

### EP-002 Relationship Extension

Scene 可新增与未来 Asset 的长期稳定（Canonical）引用关系。

新增 Relationship：

- 必须采用 Reference。
- 必须保持 Canonical。
- 不得引用 Runtime Asset。
- 不得形成循环依赖。

---

### EP-003 Validation Extension

Scene 可新增 Validation Rules。

新增 Validation：

- 必须基于已有规范。
- 不得降低已有 Validation 的严格程度。
- 不得覆盖 Foundation Validation。

---

### EP-004 Version Compatibility

Scene Data Model 的未来版本：

- 必须保持向后兼容。
- 不得删除已有 Required Fields。
- 不得修改 Foundation 定义。

如需进行破坏性修改，

必须升级 Major Version。

---

### EP-005 Extension Principles

所有扩展必须遵循以下原则：

- 不修改 Foundation。
- 不改变 Scene 职责。
- 不引入 Runtime Data。
- 不破坏 Canonical Relationships。
- 不影响其他 Asset 的独立性。

---

# 8. Prop Data Model

## 8.1 Purpose

Prop Data Model 用于定义 Prop Asset 的标准数据模型。

Prop Asset 的职责是定义可复用的道具资产（Reusable Prop Asset）。

Prop Asset 用于描述可独立管理、可跨 Character、Outfit、Scene 复用的长期稳定道具。

Prop Asset 是系统的标准道具资产（Prop Asset）。

Prop Data Model 定义的是：

> 一个道具「是什么（What the Prop Is）」。

而不是：

> 一个角色「是谁（Who the Character Is）」。

也不是：

> 一个角色「穿什么（What the Character Wears）」。

更不是：

> 一个道具「当前如何被使用（How the Prop Is Currently Used）」。

Prop Data Model 必须符合：

- 00_Core_Principles.md
- 01_Architecture.md
- 02_Asset_Specification_01_Foundation.md

---

## 8.2 Scope

Prop Data Model 的 Scope 为：

定义长期稳定、可复用的道具资产（Reusable Canonical Props）。

Prop Data Model 负责定义：

- Prop 的身份（Identity）
- Prop 的长期稳定定义
- Prop 的组成结构
- Prop 与其他 Asset 的 Canonical Relationships

Prop Data Model 不负责：

- Character Identity
- Outfit Definition
- Scene Definition
- Runtime Configuration
- Runtime State
- Shot
- Prompt
- AI Generation

上述内容均由对应 Asset 独立管理。

Prop Data Model 仅描述：

> 一个道具「是什么（What the Prop Is）」。

不描述：

> 一个角色「是谁（Who the Character Is）」。

也不描述：

> 一个角色「穿什么（What the Character Wears）」。

更不描述：

> 一个道具「当前如何被使用（How the Prop Is Currently Used）」。

Prop Asset 应保持独立。

Prop 与 Character、Outfit、Component、Scene、Configuration、State 等 Asset，

均通过 Reference 建立关联，

不得承担其他 Asset 的职责。

---

## 8.3 Data Structure

Prop Data Model 建立于 Asset Foundation 之上。

Foundation 中定义的：

- Header
- Metadata
- Relationships
- Status
- Validation
- Version

全部继承。

Prop Data Model 仅定义 Prop 专属 Content。

标准结构如下：

```text
Prop Asset
│
├── Header                    (Inherited)
├── Metadata                  (Inherited)
├── Content
│   ├── Identity
│   ├── Prop Definition
│   ├── Prop Composition
│   └── Prop References
├── Relationships             (Inherited)
├── Status                    (Inherited)
├── Validation                (Inherited)
└── Version                   (Inherited)
```

其中：

### Identity

定义 Prop 的唯一身份信息。

负责回答：

> 这是哪一个 Prop？

Identity 不受：

- Character
- Outfit
- Configuration
- State

影响。

---

### Prop Definition

定义 Prop 的长期稳定定义。

Prop Definition 仅包含 Prop 自身的规范定义。

例如：

- Prop Type
- Visual Characteristics
- Physical Properties
- Functional Purpose

Prop Definition 不包含：

- Runtime Configuration
- Runtime State
- Scene Information

---

### Prop Composition

定义 Prop 的组成结构。

Prop Composition 用于描述 Prop 的长期稳定组成结构。

Prop Composition 不保存：

- Runtime Configuration
- Runtime State

Prop Composition 仅描述 Prop 本身。

---

### Prop References

Prop References 定义 Prop 与其他长期稳定 Asset 的规范引用关系（Canonical References）。

仅保存 Canonical References。

不保存运行时配置。

例如：

- Default Character
- Compatible Outfit
- Compatible Scene

所有引用均必须使用 Asset ID。

不得复制 Asset 内容。

---

## 8.4 Required Fields

Required Fields 定义 Prop Asset 成立所必需的数据。

若缺少任一 Required Field，

Prop Asset 将无法正确建立其身份、职责或核心定义。

Required Fields 的判定原则应遵循：

> 移除该字段后，
> 若 Prop Asset 不再成立，
> 则该字段属于 Required Field。

所有 Required Fields 应：

- 直接支持 Prop Asset 的核心职责。
- 保持长期稳定（Canonical）。
- 独立于 Runtime Configuration。
- 独立于 Runtime State。
- 符合 Foundation 定义的 Field 规范。

Required Fields 仅包含 Prop Asset 自身必需的信息。

不得要求：

- Character 必须存在。
- Outfit 必须存在。
- Scene 必须存在。
- Configuration 必须存在。

任何依赖其他 Asset 的关联，

均应通过 Canonical Reference 建立，

而非作为 Prop 成立的前置条件。

具体 Required Fields 将依据本章定义的 Data Structure 分类：

- Identity
- Prop Definition
- Prop Composition

---

### RF-001 Identity

Prop Asset 必须包含 Identity。

Identity 用于定义 Prop 的唯一身份。

Identity 为 Prop 的核心字段。

不得缺失。

---

### RF-002 Prop Definition

Prop Asset 必须包含 Prop Definition。

Prop Definition 用于定义 Prop 的长期稳定规范。

不得包含：

- Runtime Configuration
- Runtime State
- Scene Information

---

### RF-003 Prop Composition

Prop Asset 必须包含 Prop Composition。

Prop Composition 用于定义 Prop 的长期稳定组成结构。

Prop Composition 不得保存：

- Runtime Configuration
- Runtime State

---

### RF-004 Inherited Foundation Fields

除 Prop 专属字段外，

Prop Asset 必须继承 Foundation 定义的全部基础字段。

包括：

- Header
- Metadata
- Relationships
- Status
- Validation
- Version

上述字段不得删除。

不得重新定义。

Prop Data Model 仅扩展 Prop 专属 Content。

不得修改 Foundation。

---

## 8.5 Optional Fields

Optional Fields 定义 Prop Asset 可选择包含的数据。

Optional Fields 用于扩展 Prop Asset 的能力，

但不是 Prop Asset 成立的必要条件。

若缺少 Optional Field，

Prop Asset 仍然有效。

Optional Fields 的判定原则应遵循：

> 移除该字段后，
> 若 Prop Asset 仍然成立，
> 仅能力、信息或可复用性降低，
> 则该字段属于 Optional Field。

所有 Optional Fields 应：

- 保持与 Prop Asset 职责一致。
- 保持长期稳定（Canonical）。
- 独立于 Runtime Configuration。
- 独立于 Runtime State。
- 符合 Foundation 定义的 Field 规范。

Optional Fields 不得：

- 改变 Prop Asset 的核心职责。
- 覆盖 Required Fields。
- 修改 Foundation 定义。

具体 Optional Fields 包括：

- Prop References
- Description
- Tags
- Extension Fields

---

### OF-001 Prop References

Prop References 为 Optional Field。

用于保存 Prop 的 Canonical Relationships。

Prop 可以不存在任何 References。

References 的定义规则应遵循：

8.6 Relationships。

---

### OF-002 Description

Description 为 Optional Field。

Description 用于补充说明 Prop 的设计目的、用途或使用说明。

Description 不参与 Asset Identity。

Description 不影响 Validation。

---

### OF-003 Tags

Tags 为 Optional Field。

Tags 用于资产分类、检索及管理。

Tags 不影响 Prop Asset 的语义。

Tags 不参与 Asset Identity。

---

### OF-004 Extension Fields

Extension Fields 为 Optional Field。

Extension Fields 用于支持未来扩展。

所有 Extension Fields：

- 不得修改 Required Fields。
- 不得覆盖 Foundation 字段。
- 不得改变 Prop Asset 的核心职责。
- 必须保持向后兼容（Backward Compatibility）。

---

## 8.6 Relationships

Relationships 定义 Prop Asset 与其他 Asset 的长期稳定（Canonical）引用关系。

Relationships 用于建立 Asset 之间的关联。

Relationships：

- 必须引用 Asset ID。
- 不得复制 Asset 内容。
- 不得引用 Runtime Data。
- 不得建立循环依赖。
- 不得引用 Composition Asset（例如 Configuration）。

Relationship 仅定义关联规则。

具体引用内容由 Asset Instance 定义。

---

### PR-001 Character Relationship

Prop 可以引用 Character Asset。

用于建立 Prop 与 Canonical Character Asset 的长期引用关系。

Prop 可以不存在 Character Relationship。

当建立该 Relationship 时，

必须引用 Character Asset ID。

---

### PR-002 Outfit Relationship

Prop 可以引用 Outfit Asset。

用于建立 Prop 与 Canonical Outfit Asset 的长期引用关系。

例如：

- Default Outfit
- Compatible Outfit

Prop 不保存 Outfit 内容。

仅保存 Outfit Asset ID。

---

### PR-003 Scene Relationship

Prop 可以引用 Scene Asset。

用于建立 Prop 与 Canonical Scene Asset 的长期引用关系。

例如：

- Default Scene
- Compatible Scene

Prop 不保存 Scene 内容。

仅保存 Scene Asset ID。

---

### PR-004 Relationship Constraints

所有 Relationship 必须遵循以下规则：

- 必须使用 Asset ID 引用。
- 一个 Relationship 不得保存业务数据。
- 不得形成循环依赖。
- 不得引用 Runtime Asset。
- 不得引用 Configuration Asset（例如 Configuration）。

---

## 8.7 Constraints

Constraints 定义 Prop Asset 必须遵循的业务规则与一致性要求。

Constraints 用于确保 Prop Asset 在整个 AVPS 中保持一致、完整及可复用。

所有 Constraints 均适用于 Prop Asset 的 Canonical Data。

不适用于：

- Runtime Configuration
- Runtime State
- Temporary Composition

---

### PC-001 Identity Integrity

Prop Identity 必须唯一。

Identity 一经建立，不得用于表示其他 Prop Asset。

Identity 的变更应遵循 Asset Versioning 规范。

---

### PC-002 Responsibility Boundary

Prop Asset 仅负责定义可复用的道具资产（Reusable Prop Asset）。

Prop Asset 不得承担：

- Character Identity
- Outfit Definition
- Scene Definition
- Runtime Configuration
- Runtime State
- Shot Information

任何超出 Prop 职责范围的数据，

均应由对应 Asset 管理。

---

### PC-003 Canonical Data Only

Prop Asset 仅保存长期稳定（Canonical）的数据。

不得保存：

- Runtime Data
- Temporary Data
- Generated Results
- Session-specific Data

---

### PC-004 Reference Integrity

所有 References 必须引用合法的 Asset ID。

不得：

- 引用不存在的 Asset。
- 复制其他 Asset 内容。
- 建立循环依赖。
- 引用 Runtime Asset。

---

### PC-005 Prop Composition Consistency

Prop Composition 必须描述 Prop 的长期稳定组成结构。

Prop Composition 不得：

- 保存 Runtime Configuration。
- 保存 Runtime State。
- 修改其他 Asset 的定义。

Prop Composition 应保持独立，并符合 Prop Asset 的职责边界。

---

### PC-006 Foundation Compliance

Prop Asset 必须继承 Foundation 定义。

不得：

- 删除 Foundation Required Fields。
- 修改 Foundation 的语义。
- 覆盖 Foundation 的 Validation Rules。

Prop Data Model 仅允许扩展 Prop 专属 Content。

不得修改 Foundation 的基础规范。

---

## 8.8 Validation Rules

Validation Rules 定义 Prop Asset 必须满足的数据完整性与一致性要求。

Validation 用于验证 Prop Asset 是否符合本规范。

Validation 不修改数据。

Validation 仅负责检查数据是否合法。

Validation 应在 Asset 创建、更新及发布时执行。

---

### PV-001 Required Field Validation

所有 Required Fields 必须存在。

若缺少任何 Required Field，

Validation 应返回 Failed。

---

### PV-002 Identity Validation

Identity 必须符合 Identity 规范。

Validation 应检查：

- Identity 是否存在。
- Identity 是否唯一。
- Identity 是否符合命名规范。

重复 Identity 不得通过 Validation。

---

### PV-003 Prop Definition Validation

Prop Definition 必须完整。

Validation 应检查：

- Required Prop Definition 是否存在。
- 不得包含 Runtime Data。
- 不得包含 Scene Information。
- 不得包含 Runtime Configuration。

---

### PV-004 Prop Composition Validation

Prop Composition 必须符合 Prop Data Model。

Validation 应检查：

- Prop Composition 是否存在。
- Prop Composition 是否符合定义。
- 不得包含 Runtime Configuration。
- 不得包含 Runtime State。

---

### PV-005 Relationship Validation

所有 Relationships 必须合法。

Validation 应检查：

- Reference 是否使用合法 Asset ID。
- Reference 是否指向存在的 Asset。
- 不得形成循环依赖。
- 不得引用 Runtime Asset。
- 不得引用 Configuration Asset。

---

### PV-006 Foundation Validation

Prop Asset 必须符合 Foundation。

Validation 应检查：

- Foundation Required Fields 是否完整。
- Foundation Metadata 是否合法。
- Foundation Validation Rules 是否满足。

不得覆盖 Foundation Validation。

---

### PV-007 Specification Compliance

Prop Asset 必须符合：

- 00_Core_Principles
- 01_Architecture
- 02_Asset_Specification_01_Foundation
- 02_Asset_Specification_02_Data_Models

任何违反上述规范的 Prop Asset，

均不得通过 Validation。

---

## 8.9 Extension Points

Extension Points 定义 Prop Data Model 在未来允许扩展的位置。

所有扩展必须保持：

- Backward Compatibility（向后兼容）
- Architecture Consistency（架构一致性）
- Foundation Compliance（Foundation 一致性）

扩展不得破坏既有 Prop Data Model。

---

### EP-001 Content Extension

Prop 可扩展新的 Prop 专属 Content。

新增 Content：

- 必须符合 Prop 职责。
- 不得修改已有 Required Fields。
- 不得覆盖已有 Optional Fields。
- 不得改变已有字段的语义（Semantic）。

---

### EP-002 Relationship Extension

Prop 可新增与未来 Asset 的长期稳定（Canonical）引用关系。

新增 Relationship：

- 必须采用 Reference。
- 必须保持 Canonical。
- 不得引用 Runtime Asset。
- 不得形成循环依赖。

---

### EP-003 Validation Extension

Prop 可新增 Validation Rules。

新增 Validation：

- 必须基于已有规范。
- 不得降低已有 Validation 的严格程度。
- 不得覆盖 Foundation Validation。

---

### EP-004 Version Compatibility

Prop Data Model 的未来版本：

- 必须保持向后兼容。
- 不得删除已有 Required Fields。
- 不得修改 Foundation 定义。

如需进行破坏性修改，

必须升级 Major Version。

---

### EP-005 Extension Principles

所有扩展必须遵循以下原则：

- 不修改 Foundation。
- 不改变 Prop 职责。
- 不引入 Runtime Data。
- 不破坏 Canonical Relationships。
- 不影响其他 Asset 的独立性。

---

# 9. World Data Model

## 9.1 Purpose

World Data Model 用于定义 World Asset 的标准数据模型。

World Asset 的职责是定义可复用的世界设定（Reusable World Definition）。

World Asset 用于描述长期稳定的世界观、规则体系及全局环境设定。

World Asset 是系统的标准世界资产（World Asset）。

World Data Model 定义的是：

> 一个世界「是什么（What the World Is）」。

而不是：

> 一个角色「是谁（Who the Character Is）」。

也不是：

> 一个场景「是什么（What the Scene Is）」。

更不是：

> 一个世界「当前发生了什么（What Is Currently Happening in the World）」。

World Data Model 必须符合：

- 00_Core_Principles.md
- 01_Architecture.md
- 02_Asset_Specification_01_Foundation.md

---

## 9.2 Scope

World Data Model 的 Scope 为：

定义长期稳定、可复用的世界设定（Reusable Canonical World）。

World Data Model 负责定义：

- World 的身份（Identity）
- World 的长期稳定定义
- World 的组成结构
- World 与其他 Asset 的 Canonical Relationships

World Data Model 不负责：

- Character Identity
- Outfit Definition
- Component Definition
- Scene Definition
- Runtime Configuration
- Runtime State
- Shot
- Prompt
- AI Generation

上述内容均由对应 Asset 独立管理。

World Data Model 仅描述：

> 一个世界「是什么（What the World Is）」。

不描述：

> 一个角色「是谁（Who the Character Is）」。

也不描述：

> 一个场景「当前发生了什么（What Is Happening in the Scene）」。

更不描述：

> 一个世界「当前发生了什么（What Is Currently Happening in the World）」。

World Asset 应保持独立。

World 与 Character、Outfit、Component、Scene、Prop、Configuration、State 等 Asset，

均通过 Reference 建立关联，

不得承担其他 Asset 的职责。

---

## 9.3 Data Structure

World Data Model 建立于 Asset Foundation 之上。

Foundation 中定义的：

- Header
- Metadata
- Relationships
- Status
- Validation
- Version

全部继承。

World Data Model 仅定义 World 专属 Content。

标准结构如下：

```text
World Asset
│
├── Header                    (Inherited)
├── Metadata                  (Inherited)
├── Content
│   ├── Identity
│   ├── World Definition
│   ├── World Composition
│   └── World References
├── Relationships             (Inherited)
├── Status                    (Inherited)
├── Validation                (Inherited)
└── Version                   (Inherited)
```

其中：

### Identity

定义 World 的唯一身份信息。

负责回答：

> 这是哪一个 World？

Identity 不受：

- Character
- Scene
- Configuration
- State

影响。

---

### World Definition

定义 World 的长期稳定定义。

World Definition 仅包含 World 自身的规范定义。

例如：

- World Type
- Physical Rules
- Cultural Characteristics
- Environmental Features

World Definition 不包含：

- Runtime Configuration
- Runtime State
- Story Progress

---

### World Composition

定义 World 的组成结构。

World Composition 用于描述 World 的长期稳定组成结构。

World Composition 不保存：

- Runtime Configuration
- Runtime State

World Composition 仅描述 World 本身。

---

### World References

World References 定义 World 与其他长期稳定 Asset 的规范引用关系（Canonical References）。

仅保存 Canonical References。

不保存运行时配置。

例如：

- Default Scenes
- Default Characters
- Default Props

所有引用均必须使用 Asset ID。

不得复制 Asset 内容。

---

## 9.4 Required Fields

Required Fields 定义 World Asset 成立所必需的数据。

若缺少任一 Required Field，

World Asset 将无法正确建立其身份、职责或核心定义。

Required Fields 的判定原则应遵循：

> 移除该字段后，
> 若 World Asset 不再成立，
> 则该字段属于 Required Field。

所有 Required Fields 应：

- 直接支持 World Asset 的核心职责。
- 保持长期稳定（Canonical）。
- 独立于 Runtime Configuration。
- 独立于 Runtime State。
- 符合 Foundation 定义的 Field 规范。

Required Fields 仅包含 World Asset 自身必需的信息。

不得要求：

- Character 必须存在。
- Scene 必须存在。
- Prop 必须存在。
- Configuration 必须存在。

任何依赖其他 Asset 的关联，

均应通过 Canonical Reference 建立，

而非作为 World 成立的前置条件。

具体 Required Fields 将依据本章定义的 Data Structure 分类：

- Identity
- World Definition
- World Composition

---

### RF-001 Identity

World Asset 必须包含 Identity。

Identity 用于定义 World 的唯一身份。

Identity 为 World 的核心字段。

不得缺失。

---

### RF-002 World Definition

World Asset 必须包含 World Definition。

World Definition 用于定义 World 的长期稳定规范。

不得包含：

- Runtime Configuration
- Runtime State
- Story Progress

---

### RF-003 World Composition

World Asset 必须包含 World Composition。

World Composition 用于定义 World 的长期稳定组成结构。

World Composition 不得保存：

- Runtime Configuration
- Runtime State

---

### RF-004 Inherited Foundation Fields

除 World 专属字段外，

World Asset 必须继承 Foundation 定义的全部基础字段。

包括：

- Header
- Metadata
- Relationships
- Status
- Validation
- Version

上述字段不得删除。

不得重新定义。

World Data Model 仅扩展 World 专属 Content。

不得修改 Foundation。

---

## 9.5 Optional Fields

Optional Fields 定义 World Asset 可选择包含的数据。

Optional Fields 用于扩展 World Asset 的能力，

但不是 World Asset 成立的必要条件。

若缺少 Optional Field，

World Asset 仍然有效。

Optional Fields 的判定原则应遵循：

> 移除该字段后，
> 若 World Asset 仍然成立，
> 仅能力、信息或可复用性降低，
> 则该字段属于 Optional Field。

所有 Optional Fields 应：

- 保持与 World Asset 职责一致。
- 保持长期稳定（Canonical）。
- 独立于 Runtime Configuration。
- 独立于 Runtime State。
- 符合 Foundation 定义的 Field 规范。

Optional Fields 不得：

- 改变 World Asset 的核心职责。
- 覆盖 Required Fields。
- 修改 Foundation 定义。

具体 Optional Fields 包括：

- World References
- Description
- Tags
- Extension Fields

---

### OF-001 World References

World References 为 Optional Field。

用于保存 World 的 Canonical Relationships。

World 可以不存在任何 References。

References 的定义规则应遵循：

9.6 Relationships。

---

### OF-002 Description

Description 为 Optional Field。

Description 用于补充说明 World 的设计目的、世界观或设定说明。

Description 不参与 Asset Identity。

Description 不影响 Validation。

---

### OF-003 Tags

Tags 为 Optional Field。

Tags 用于资产分类、检索及管理。

Tags 不影响 World Asset 的语义。

Tags 不参与 Asset Identity。

---

### OF-004 Extension Fields

Extension Fields 为 Optional Field。

Extension Fields 用于支持未来扩展。

所有 Extension Fields：

- 不得修改 Required Fields。
- 不得覆盖 Foundation 字段。
- 不得改变 World Asset 的核心职责。
- 必须保持向后兼容（Backward Compatibility）。

---

## 9.6 Relationships

Relationships 定义 World Asset 与其他 Asset 的长期稳定（Canonical）引用关系。

Relationships 用于建立 Asset 之间的关联。

Relationships：

- 必须引用 Asset ID。
- 不得复制 Asset 内容。
- 不得引用 Runtime Data。
- 不得建立循环依赖。
- 不得引用 Composition Asset（例如 Configuration）。

Relationship 仅定义关联规则。

具体引用内容由 Asset Instance 定义。

---

### WR-001 Scene Relationship

World 可以引用 Scene Asset。

用于建立 World 与 Canonical Scene Asset 的长期引用关系。

例如：

- Default Scene
- Available Scene

World 不保存 Scene 内容。

仅保存 Scene Asset ID。

---

### WR-002 Character Relationship

World 可以引用 Character Asset。

用于建立 World 与 Canonical Character Asset 的长期引用关系。

例如：

- Default Character
- Native Character

World 不保存 Character 内容。

仅保存 Character Asset ID。

---

### WR-003 Prop Relationship

World 可以引用 Prop Asset。

用于建立 World 与 Canonical Prop Asset 的长期引用关系。

例如：

- Default Prop
- Native Prop

World 不保存 Prop 内容。

仅保存 Prop Asset ID。

---

### WR-004 Relationship Constraints

所有 Relationship 必须遵循以下规则：

- 必须使用 Asset ID 引用。
- 一个 Relationship 不得保存业务数据。
- 不得形成循环依赖。
- 不得引用 Runtime Asset。
- 不得引用 Configuration Asset（例如 Configuration）。

---

## 9.7 Constraints

Constraints 定义 World Asset 必须遵循的业务规则与一致性要求。

Constraints 用于确保 World Asset 在整个 AVPS 中保持一致、完整及可复用。

所有 Constraints 均适用于 World Asset 的 Canonical Data。

不适用于：

- Runtime Configuration
- Runtime State
- Temporary Composition

---

### WC-001 Identity Integrity

World Identity 必须唯一。

Identity 一经建立，不得用于表示其他 World Asset。

Identity 的变更应遵循 Asset Versioning 规范。

---

### WC-002 Responsibility Boundary

World Asset 仅负责定义可复用的世界设定（Reusable World Definition）。

World Asset 不得承担：

- Character Identity
- Outfit Definition
- Component Definition
- Scene Definition
- Runtime Configuration
- Runtime State
- Story Progress

任何超出 World 职责范围的数据，

均应由对应 Asset 管理。

---

### WC-003 Canonical Data Only

World Asset 仅保存长期稳定（Canonical）的数据。

不得保存：

- Runtime Data
- Temporary Data
- Generated Results
- Session-specific Data

---

### WC-004 Reference Integrity

所有 References 必须引用合法的 Asset ID。

不得：

- 引用不存在的 Asset。
- 复制其他 Asset 内容。
- 建立循环依赖。
- 引用 Runtime Asset。

---

### WC-005 World Composition Consistency

World Composition 必须描述 World 的长期稳定组成结构。

World Composition 不得：

- 保存 Runtime Configuration。
- 保存 Runtime State。
- 修改其他 Asset 的定义。

World Composition 应保持独立，并符合 World Asset 的职责边界。

---

### WC-006 Foundation Compliance

World Asset 必须继承 Foundation 定义。

不得：

- 删除 Foundation Required Fields。
- 修改 Foundation 的语义。
- 覆盖 Foundation 的 Validation Rules。

World Data Model 仅允许扩展 World 专属 Content。

不得修改 Foundation 的基础规范。

---

## 9.8 Validation Rules

Validation Rules 定义 World Asset 必须满足的数据完整性与一致性要求。

Validation 用于验证 World Asset 是否符合本规范。

Validation 不修改数据。

Validation 仅负责检查数据是否合法。

Validation 应在 Asset 创建、更新及发布时执行。

---

### WV-001 Required Field Validation

所有 Required Fields 必须存在。

若缺少任何 Required Field，

Validation 应返回 Failed。

---

### WV-002 Identity Validation

Identity 必须符合 Identity 规范。

Validation 应检查：

- Identity 是否存在。
- Identity 是否唯一。
- Identity 是否符合命名规范。

重复 Identity 不得通过 Validation。

---

### WV-003 World Definition Validation

World Definition 必须完整。

Validation 应检查：

- Required World Definition 是否存在。
- 不得包含 Runtime Data。
- 不得包含 Story Progress。
- 不得包含 Runtime Configuration。

---

### WV-004 World Composition Validation

World Composition 必须符合 World Data Model。

Validation 应检查：

- World Composition 是否存在。
- World Composition 是否符合定义。
- 不得包含 Runtime Configuration。
- 不得包含 Runtime State。

---

### WV-005 Relationship Validation

所有 Relationships 必须合法。

Validation 应检查：

- Reference 是否使用合法 Asset ID。
- Reference 是否指向存在的 Asset。
- 不得形成循环依赖。
- 不得引用 Runtime Asset。
- 不得引用 Configuration Asset。

---

### WV-006 Foundation Validation

World Asset 必须符合 Foundation。

Validation 应检查：

- Foundation Required Fields 是否完整。
- Foundation Metadata 是否合法。
- Foundation Validation Rules 是否满足。

不得覆盖 Foundation Validation。

---

### WV-007 Specification Compliance

World Asset 必须符合：

- 00_Core_Principles
- 01_Architecture
- 02_Asset_Specification_01_Foundation
- 02_Asset_Specification_02_Data_Models

任何违反上述规范的 World Asset，

均不得通过 Validation。

---

## 9.9 Extension Points

Extension Points 定义 World Data Model 在未来允许扩展的位置。

所有扩展必须保持：

- Backward Compatibility（向后兼容）
- Architecture Consistency（架构一致性）
- Foundation Compliance（Foundation 一致性）

扩展不得破坏既有 World Data Model。

---

### EP-001 Content Extension

World 可扩展新的 World 专属 Content。

新增 Content：

- 必须符合 World 职责。
- 不得修改已有 Required Fields。
- 不得覆盖已有 Optional Fields。
- 不得改变已有字段的语义（Semantic）。

---

### EP-002 Relationship Extension

World 可新增与未来 Asset 的长期稳定（Canonical）引用关系。

新增 Relationship：

- 必须采用 Reference。
- 必须保持 Canonical。
- 不得引用 Runtime Asset。
- 不得形成循环依赖。

---

### EP-003 Validation Extension

World 可新增 Validation Rules。

新增 Validation：

- 必须基于已有规范。
- 不得降低已有 Validation 的严格程度。
- 不得覆盖 Foundation Validation。

---

### EP-004 Version Compatibility

World Data Model 的未来版本：

- 必须保持向后兼容。
- 不得删除已有 Required Fields。
- 不得修改 Foundation 定义。

如需进行破坏性修改，

必须升级 Major Version。

---

### EP-005 Extension Principles

所有扩展必须遵循以下原则：

- 不修改 Foundation。
- 不改变 World 职责。
- 不引入 Runtime Data。
- 不破坏 Canonical Relationships。
- 不影响其他 Asset 的独立性。

---

# 10. Configuration Data Model

## 10.1 Purpose

Configuration Data Model 用于定义 Configuration Asset 的标准数据模型。

Configuration Asset 的职责是定义可复用的运行配置（Reusable Canonical Configuration）。

Configuration Asset 用于描述多个 Canonical Asset 在特定使用场景下的组合方式及配置规则。

Configuration Asset 是系统的标准配置资产（Configuration Asset）。

Configuration Data Model 定义的是：

> 一个配置「是什么（What the Configuration Is）」。

而不是：

> 一个角色「是谁（Who the Character Is）」。

也不是：

> 一个场景「是什么（What the Scene Is）」。

更不是：

> 一个配置「当前运行状态如何（Current Runtime State）」。

Configuration Data Model 必须符合：

- 00_Core_Principles.md
- 01_Architecture.md
- 02_Asset_Specification_01_Foundation.md

---

## 10.2 Scope

Configuration Data Model 的 Scope 为：

定义长期稳定、可复用的资产组合配置（Reusable Canonical Configuration）。

Configuration Data Model 负责定义：

- Configuration 的身份（Identity）
- Configuration 的长期稳定定义
- Configuration 的资产组合结构
- Configuration 与其他 Asset 的 Canonical Relationships

Configuration Data Model 不负责：

- Character Identity
- Outfit Definition
- Component Definition
- Scene Definition
- World Definition
- Runtime State
- Shot
- Prompt
- AI Generation

上述内容均由对应 Asset 独立管理。

Configuration Data Model 仅描述：

> 一个配置「是什么（What the Configuration Is）」。

不描述：

> 一个角色「是谁（Who the Character Is）」。

也不描述：

> 一个配置「当前运行状态如何（Current Runtime State）」。

Configuration Asset 应保持独立。

Configuration 与 Character、Outfit、Component、Scene、Prop、World、State 等 Asset，

均通过 Reference 建立关联，

不得承担其他 Asset 的职责。

---

## 10.3 Data Structure

Configuration Data Model 建立于 Asset Foundation 之上。

Foundation 中定义的：

- Header
- Metadata
- Relationships
- Status
- Validation
- Version

全部继承。

Configuration Data Model 仅定义 Configuration 专属 Content。

标准结构如下：

```text
Configuration Asset
│
├── Header                    (Inherited)
├── Metadata                  (Inherited)
├── Content
│   ├── Identity
│   ├── Configuration Definition
│   ├── Configuration Composition
│   └── Configuration References
├── Relationships             (Inherited)
├── Status                    (Inherited)
├── Validation                (Inherited)
└── Version                   (Inherited)
```

其中：

### Identity

定义 Configuration 的唯一身份信息。

负责回答：

> 这是哪一个 Configuration？

Identity 不受：

- Runtime State
- Session
- Execution

影响。

---

### Configuration Definition

定义 Configuration 的长期稳定定义。

Configuration Definition 仅包含 Configuration 自身的规范定义。

例如：

- Configuration Type
- Asset Selection Rules
- Composition Rules
- Usage Purpose

Configuration Definition 不包含：

- Runtime State
- Session Data
- Execution Result

---

### Configuration Composition

定义 Configuration 的资产组合结构。

Configuration Composition 用于描述 Configuration 的长期稳定资产组合结构。

Configuration Composition 不保存：

- Runtime State
- Execution Result

Configuration Composition 仅描述 Configuration 本身。

---

### Configuration References

Configuration References 定义 Configuration 与其他长期稳定 Asset 的规范引用关系（Canonical References）。

仅保存 Canonical References。

不保存运行时状态。

例如：

- Character
- Outfit
- Scene
- World
- Props

所有引用均必须使用 Asset ID。

不得复制 Asset 内容。

---

## 10.4 Required Fields

Required Fields 定义 Configuration Asset 成立所必需的数据。

若缺少任一 Required Field，

Configuration Asset 将无法正确建立其身份、职责或核心定义。

Required Fields 的判定原则应遵循：

> 移除该字段后，
> 若 Configuration Asset 不再成立，
> 则该字段属于 Required Field。

所有 Required Fields 应：

- 直接支持 Configuration Asset 的核心职责。
- 保持长期稳定（Canonical）。
- 独立于 Runtime State。
- 符合 Foundation 定义的 Field 规范。

Required Fields 仅包含 Configuration Asset 自身必需的信息。

不得要求：

- Character 必须存在。
- Outfit 必须存在。
- Scene 必须存在。
- World 必须存在。

任何依赖其他 Asset 的关联，

均应通过 Canonical Reference 建立，

而非作为 Configuration 成立的前置条件。

具体 Required Fields 将依据本章定义的 Data Structure 分类：

- Identity
- Configuration Definition
- Configuration Composition

---

### RF-001 Identity

Configuration Asset 必须包含 Identity。

Identity 用于定义 Configuration 的唯一身份。

Identity 为 Configuration 的核心字段。

不得缺失。

---

### RF-002 Configuration Definition

Configuration Asset 必须包含 Configuration Definition。

Configuration Definition 用于定义 Configuration 的长期稳定规范。

不得包含：

- Runtime State
- Session Data
- Execution Result

---

### RF-003 Configuration Composition

Configuration Asset 必须包含 Configuration Composition。

Configuration Composition 用于定义 Configuration 的长期稳定组合结构。

Configuration Composition 不得保存：

- Runtime State
- Execution Result

---

### RF-004 Inherited Foundation Fields

除 Configuration 专属字段外，

Configuration Asset 必须继承 Foundation 定义的全部基础字段。

包括：

- Header
- Metadata
- Relationships
- Status
- Validation
- Version

上述字段不得删除。

不得重新定义。

Configuration Data Model 仅扩展 Configuration 专属 Content。

不得修改 Foundation。

---

## 10.5 Optional Fields

Optional Fields 定义 Configuration Asset 可选择包含的数据。

Optional Fields 用于扩展 Configuration Asset 的能力，

但不是 Configuration Asset 成立的必要条件。

若缺少 Optional Field，

Configuration Asset 仍然有效。

Optional Fields 的判定原则应遵循：

> 移除该字段后，
> 若 Configuration Asset 仍然成立，
> 仅能力、信息或可复用性降低，
> 则该字段属于 Optional Field。

所有 Optional Fields 应：

- 保持与 Configuration Asset 职责一致。
- 保持长期稳定（Canonical）。
- 独立于 Runtime State。
- 符合 Foundation 定义的 Field 规范。

Optional Fields 不得：

- 改变 Configuration Asset 的核心职责。
- 覆盖 Required Fields。
- 修改 Foundation 定义。

具体 Optional Fields 包括：

- Configuration References
- Description
- Tags
- Extension Fields

---

### OF-001 Configuration References

Configuration References 为 Optional Field。

用于保存 Configuration 的 Canonical Relationships。

Configuration 可以不存在任何 References。

References 的定义规则应遵循：

10.6 Relationships。

---

### OF-002 Description

Description 为 Optional Field。

Description 用于补充说明 Configuration 的设计目的、适用场景或配置说明。

Description 不参与 Asset Identity。

Description 不影响 Validation。

---

### OF-003 Tags

Tags 为 Optional Field。

Tags 用于资产分类、检索及管理。

Tags 不影响 Configuration Asset 的语义。

Tags 不参与 Asset Identity。

---

### OF-004 Extension Fields

Extension Fields 为 Optional Field。

Extension Fields 用于支持未来扩展。

所有 Extension Fields：

- 不得修改 Required Fields。
- 不得覆盖 Foundation 字段。
- 不得改变 Configuration Asset 的核心职责。
- 必须保持向后兼容（Backward Compatibility）。

---

## 10.6 Relationships

Relationships 定义 Configuration Asset 与其他 Asset 的长期稳定（Canonical）引用关系。

Relationships 用于建立 Asset 之间的关联。

Relationships：

- 必须引用 Asset ID。
- 不得复制 Asset 内容。
- 不得引用 Runtime Data。
- 不得建立循环依赖。

Relationship 仅定义关联规则。

具体引用内容由 Asset Instance 定义。

---

### CFR-001 Character Relationship

Configuration 可以引用 Character Asset。

用于建立 Configuration 与 Canonical Character Asset 的长期引用关系。

Configuration 不保存 Character 内容。

仅保存 Character Asset ID。

---

### CFR-002 Outfit Relationship

Configuration 可以引用 Outfit Asset。

用于建立 Configuration 与 Canonical Outfit Asset 的长期引用关系。

Configuration 不保存 Outfit 内容。

仅保存 Outfit Asset ID。

---

### CFR-003 Environment Relationship

Configuration 可以引用：

- Scene Asset
- World Asset
- Prop Asset
- Component Asset

用于建立 Configuration 与各类 Canonical Asset 的长期引用关系。

Configuration 不保存上述 Asset 内容。

仅保存对应 Asset ID。

---

### CFR-004 Relationship Constraints

所有 Relationship 必须遵循以下规则：

- 必须使用 Asset ID 引用。
- 一个 Relationship 不得保存业务数据。
- 不得形成循环依赖。
- 不得引用 Runtime Asset。

---

## 10.7 Constraints

Constraints 定义 Configuration Asset 必须遵循的业务规则与一致性要求。

Constraints 用于确保 Configuration Asset 在整个 AVPS 中保持一致、完整及可复用。

所有 Constraints 均适用于 Configuration Asset 的 Canonical Data。

不适用于：

- Runtime State
- Session Data
- Temporary Runtime Data

---

### CFC-001 Identity Integrity

Configuration Identity 必须唯一。

Identity 一经建立，

不得用于表示其他 Configuration Asset。

Identity 的变更应遵循 Asset Versioning 规范。

---

### CFC-002 Responsibility Boundary

Configuration Asset 仅负责定义可复用的资产组合配置（Reusable Canonical Configuration）。

Configuration Asset 不得承担：

- Character Identity
- Outfit Definition
- Component Definition
- Scene Definition
- World Definition
- Runtime State

任何超出 Configuration 职责范围的数据，

均应由对应 Asset 管理。

---

### CFC-003 Canonical Data Only

Configuration Asset 仅保存长期稳定（Canonical）的配置数据。

不得保存：

- Runtime State
- Session Data
- Generated Results
- Temporary Runtime Data

---

### CFC-004 Reference Integrity

所有 References 必须引用合法的 Asset ID。

不得：

- 引用不存在的 Asset。
- 复制其他 Asset 内容。
- 建立循环依赖。
- 引用 Runtime Asset。

---

### CFC-005 Configuration Composition Consistency

Configuration Composition 必须描述 Canonical Asset 的长期稳定组合结构。

Configuration Composition 不得：

- 保存 Runtime State。
- 保存 Execution Result。
- 修改其他 Asset 的定义。

Configuration Composition 应保持独立，并符合 Configuration Asset 的职责边界。

---

### CFC-006 Foundation Compliance

Configuration Asset 必须继承 Foundation 定义。

不得：

- 删除 Foundation Required Fields。
- 修改 Foundation 的语义。
- 覆盖 Foundation 的 Validation Rules。

Configuration Data Model 仅允许扩展 Configuration 专属 Content。

不得修改 Foundation 的基础规范。

---

## 10.8 Validation Rules

Validation Rules 定义 Configuration Asset 必须满足的数据完整性与一致性要求。

Validation 用于验证 Configuration Asset 是否符合本规范。

Validation 不修改数据。

Validation 仅负责检查数据是否合法。

Validation 应在 Asset 创建、更新及发布时执行。

---

### CFV-001 Required Field Validation

所有 Required Fields 必须存在。

若缺少任何 Required Field，

Validation 应返回 Failed。

---

### CFV-002 Identity Validation

Identity 必须符合 Identity 规范。

Validation 应检查：

- Identity 是否存在。
- Identity 是否唯一。
- Identity 是否符合命名规范。

重复 Identity 不得通过 Validation。

---

### CFV-003 Configuration Definition Validation

Configuration Definition 必须完整。

Validation 应检查：

- Required Configuration Definition 是否存在。
- 不得包含 Runtime State。
- 不得包含 Session Data。
- 不得包含 Execution Result。

---

### CFV-004 Configuration Composition Validation

Configuration Composition 必须符合 Configuration Data Model。

Validation 应检查：

- Configuration Composition 是否存在。
- Configuration Composition 是否符合定义。
- 不得包含 Runtime State。
- 不得包含 Execution Result。

---

### CFV-005 Relationship Validation

所有 Relationships 必须合法。

Validation 应检查：

- Reference 是否使用合法 Asset ID。
- Reference 是否指向存在的 Asset。
- 不得形成循环依赖。
- 不得引用 Runtime Asset。

---

### CFV-006 Foundation Validation

Configuration Asset 必须符合 Foundation。

Validation 应检查：

- Foundation Required Fields 是否完整。
- Foundation Metadata 是否合法。
- Foundation Validation Rules 是否满足。

不得覆盖 Foundation Validation。

---

### CFV-007 Specification Compliance

Configuration Asset 必须符合：

- 00_Core_Principles
- 01_Architecture
- 02_Asset_Specification_01_Foundation
- 02_Asset_Specification_02_Data_Models

任何违反上述规范的 Configuration Asset，

均不得通过 Validation。

---

## 10.9 Extension Points

Extension Points 定义 Configuration Data Model 在未来允许扩展的位置。

所有扩展必须保持：

- Backward Compatibility（向后兼容）
- Architecture Consistency（架构一致性）
- Foundation Compliance（Foundation 一致性）

扩展不得破坏既有 Configuration Data Model。

---

### EP-001 Content Extension

Configuration 可扩展新的 Configuration 专属 Content。

新增 Content：

- 必须符合 Configuration 职责。
- 不得修改已有 Required Fields。
- 不得覆盖已有 Optional Fields。
- 不得改变已有字段的语义（Semantic）。

---

### EP-002 Relationship Extension

Configuration 可新增与未来 Asset 的长期稳定（Canonical）引用关系。

新增 Relationship：

- 必须采用 Reference。
- 必须保持 Canonical。
- 不得引用 Runtime Asset。
- 不得形成循环依赖。

---

### EP-003 Validation Extension

Configuration 可新增 Validation Rules。

新增 Validation：

- 必须基于已有规范。
- 不得降低已有 Validation 的严格程度。
- 不得覆盖 Foundation Validation。

---

### EP-004 Version Compatibility

Configuration Data Model 的未来版本：

- 必须保持向后兼容。
- 不得删除已有 Required Fields。
- 不得修改 Foundation 定义。

如需进行破坏性修改，

必须升级 Major Version。

---

### EP-005 Extension Principles

所有扩展必须遵循以下原则：

- 不修改 Foundation。
- 不改变 Configuration 职责。
- 不引入 Runtime Data。
- 不破坏 Canonical Relationships。
- 不影响其他 Asset 的独立性。

---

# 11. Cross Model Rules

## 11.1 Purpose

Cross Model Rules 定义所有 Asset Data Model 之间必须共同遵循的统一规则。

本章用于保证：

- 各 Data Model 保持一致。
- 各 Asset 保持独立。
- 各 Asset 能够稳定协作。
- 整个 AVPS Data Model 保持统一架构。

Cross Model Rules 不定义新的 Asset。

Cross Model Rules 不修改任何 Data Model。

Cross Model Rules 仅定义所有 Data Model 必须共同遵循的规则。

---

## 11.2 Scope

Cross Model Rules 适用于：

- Character Data Model
- Outfit Data Model
- Component Data Model
- Scene Data Model
- Prop Data Model
- World Data Model
- Configuration Data Model

Cross Model Rules 不适用于：

- Asset Instance
- Runtime State
- Runtime Configuration
- AI Generation
- Project-specific Data

上述内容应由对应规范定义。

---

## 11.3 Common Design Principles

所有 Asset Data Model 必须遵循统一设计原则。

包括：

- Single Responsibility
- Asset-Centric Architecture
- Canonical Data
- Reference First
- Foundation Inheritance

任何 Data Model：

不得违反：

- 00_Core_Principles
- 01_Architecture
- 02_Asset_Specification_01_Foundation

所有 Data Model：

仅允许扩展自身业务结构。

不得修改 Foundation。

---

## 11.4 Cross Model Consistency

所有 Data Model 必须保持统一结构。

统一结构包括：

- Purpose
- Scope
- Data Structure
- Required Fields
- Optional Fields
- Relationships
- Constraints
- Validation Rules
- Extension Points

所有 Data Model：

必须采用统一命名规范。

必须采用统一章节结构。

必须采用统一字段分类原则。

不得因 Asset 类型不同而改变整体模板。

Asset 之间允许业务内容不同，

但不得改变 Data Model 的整体结构。

---

## 11.5 Cross Asset Relationships

所有 Asset 之间的引用关系必须遵循统一规则。

Cross Asset Relationships 适用于所有 Canonical Asset。

所有 Relationships：

- 必须使用 Asset ID 建立引用。
- 不得复制其他 Asset 内容。
- 不得保存 Runtime Data。
- 不得形成循环依赖。

Relationship 的职责仅为：

建立长期稳定（Canonical）的资产关联。

不得承担：

- 数据存储
- Runtime Configuration
- Runtime State
- Asset Composition

任何跨 Asset 数据，

均应由对应 Asset 自身管理。

---

## 11.6 Cross Model Validation

所有 Data Model 必须采用统一 Validation 原则。

Validation：

- 仅负责验证。
- 不修改数据。
- 不补全数据。
- 不推导数据。

Validation 应至少验证：

- Required Fields
- Relationships
- Constraints
- Foundation Compliance

Validation 应在：

- Asset Create
- Asset Update
- Asset Release

阶段执行。

任何 Validation：

不得覆盖 Foundation Validation。

---

## 11.7 Version Compatibility

所有 Data Model 必须保持统一版本兼容策略。

版本管理应遵循：

- Semantic Versioning
- Backward Compatibility
- Major Version
- Minor Version
- Patch Version

破坏性修改（Breaking Change）：

必须升级 Major Version。

新增可兼容能力：

应升级 Minor Version。

修正错误：

应升级 Patch Version。

任何 Data Model：

不得破坏已发布版本的兼容性。

---

## 11.8 Extension Rules

所有 Data Model 的扩展必须遵循统一规则。

扩展允许：

- 新增 Content。
- 新增 Relationships。
- 新增 Validation Rules。
- 新增 Extension Fields。

扩展不得：

- 修改 Foundation。
- 删除 Required Fields。
- 覆盖 Foundation Validation。
- 改变 Asset 的核心职责。
- 引入 Runtime Data。

所有扩展：

必须保持向后兼容。

必须保持架构一致性。

---

## 11.9 Cross Model Overview

Cross Model Rules 是所有 Asset Data Model 的统一规范。

本章用于确保：

- Data Model 保持一致。
- Asset 保持独立。
- Relationships 保持统一。
- Validation 保持统一。
- Version 保持兼容。
- Extension 保持稳定。

所有 Data Model 必须共同遵循：

- 00_Core_Principles
- 01_Architecture
- 02_Asset_Specification_01_Foundation
- 本规范定义的 Cross Model Rules

任何 Data Model：

不得违反上述统一规则。

Cross Model Rules 不定义新的 Asset。

仅定义所有 Data Model 必须共同遵循的规范。

---

# 12. Summary

## 12.1 Purpose

本章用于总结 AVPS Data Models Specification。

本章不定义新的 Data Model。

本章不引入新的设计原则。

本章用于总结：

- Data Model 的整体架构。
- 各 Asset Data Model 的职责。
- Cross Model Rules 的统一规范。
- 本规范的适用范围及未来扩展方向。

---

## 12.2 Data Model Overview

本规范共定义以下 Canonical Asset Data Model：

- Character Data Model
- Outfit Data Model
- Component Data Model
- Scene Data Model
- Prop Data Model
- World Data Model
- Configuration Data Model

所有 Data Model：

- 建立于 Foundation。
- 遵循统一 Template。
- 遵循 Cross Model Rules。
- 保持独立职责。
- 支持长期维护与扩展。

整个 Data Models Specification 构成 AVPS Asset Layer 的统一数据模型标准。

---

## 12.3 Design Principles Summary

所有 Data Model 均共同遵循以下设计原则：

- Single Responsibility
- Asset-Centric Architecture
- Canonical Data
- Reference First
- Foundation Inheritance

所有 Asset：

- 必须保持职责独立。
- 必须保持 Canonical。
- 必须通过 Reference 建立关联。
- 不得承担其他 Asset 的职责。
- 不得修改 Foundation 定义。

所有 Data Model：

必须符合：

- 00_Core_Principles
- 01_Architecture
- 02_Asset_Specification_01_Foundation
- 本规范定义的 Cross Model Rules

---

## 12.4 Future Extensibility

本规范支持未来新增 Asset Data Model。

例如：

- Camera
- Vehicle
- Audio
- Effect
- Animation

新增 Data Model：

必须：

- 继承 Foundation。
- 保持统一 Template。
- 遵循 Cross Model Rules。
- 保持向后兼容（Backward Compatibility）。

新增 Asset 不得修改既有 Data Model。

---

## 12.5 Specification Status

当前 Data Models Specification 已定义：

- Character Data Model
- Outfit Data Model
- Component Data Model
- Scene Data Model
- Prop Data Model
- World Data Model
- Configuration Data Model
- Cross Model Rules

上述规范共同组成 AVPS Data Models 的标准规范。

当前规范状态：

- Status：Stable
- Version：3.0.0

未来版本更新应遵循 Semantic Versioning。

---

## 12.6 Closing Statement

本规范定义 AVPS Asset Data Model 的统一标准。

所有 Asset Data Model：

- 应遵循 Foundation。
- 应遵循统一 Template。
- 应遵循 Cross Model Rules。

未来所有新增 Data Model，

均应保持：

- Architecture Consistency
- Foundation Compliance
- Backward Compatibility

本规范作为 AVPS Asset Data Models 的权威定义（Authoritative Specification），

用于指导所有 Asset Schema 的设计、实现、验证及未来扩展。

Data Models Specification 至此完成。
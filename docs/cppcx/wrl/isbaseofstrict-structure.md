---
description: 了解详细信息： IsBaseOfStrict 结构
title: IsBaseOfStrict 结构
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict
- internal/Microsoft::WRL::Details::IsBaseOfStrict::value
helpviewer_keywords:
- Microsoft::WRL::Details::IsBaseOfStrict structure
- Microsoft::WRL::Details::IsBaseOfStrict::value constant
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
ms.openlocfilehash: bcdab9c4b6b5a2ab108b59d3127c08b53589e16a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298950"
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <typename Base, typename Derived>
struct IsBaseOfStrict;

template <typename Base>
struct IsBaseOfStrict<Base, Base>;
```

### <a name="parameters"></a>parameters

*基座*<br/>
基类型。

*派生*<br/>
派生的类型。

## <a name="remarks"></a>备注

测试一种类型是否是另一种类型的基类。

第一个模板测试类型是否派生自基类型，这可能会产生 **`true`** 或 **`false`** 。 第二个模板测试某一类型是否从其自身派生而来 **`false`** 。

## <a name="members"></a>成员

### <a name="public-constants"></a>公共常量

名称                            | 描述
------------------------------- | --------------------------------------------------
[IsBaseOfStrict：： value](#value) | 指示一种类型是否是另一种类型的基础。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IsBaseOfStrict`

## <a name="requirements"></a>要求

**标头：** internal。h

**命名空间：** Microsoft：： WRL：:D etails

## <a name="isbaseofstrictvalue"></a><a name="value"></a> IsBaseOfStrict：： value

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
static const bool value = __is_base_of(Base, Derived);
```

### <a name="remarks"></a>备注

指示一种类型是否是另一种类型的基础。

`value`**`true`** 如果类型 `Base` 是类型的基类，则为 `Derived` ; 否则为 **`false`** 。

---
description: 了解详细信息： implements_category
title: 'implements_category (c + + COM 特性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.implements_category
helpviewer_keywords:
- implements_category attribute
ms.assetid: fb162df3-1ebe-43dc-a084-668d7ef8c03f
ms.openlocfilehash: 0efc240394c67ab7d470523b8dfe5025b7a0f978
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97289538"
---
# <a name="implements_category"></a>implements_category

指定由目标类实现的组件类别。

## <a name="syntax"></a>语法

```cpp
[ implements_category(implements_category="uuid") ]
```

### <a name="parameters"></a>parameters

*implements_category*<br/>
已实现类别的 ID。

## <a name="remarks"></a>备注

**Implements_category** c + + 特性指定由目标类实现的组件类别。 这是通过创建类别映射并添加由 **implements_category** 属性指定的单独条目来完成的。 有关详细信息，请参阅 [组件类别及其工作原理](/windows/win32/com/component-categories-and-how-they-work)。

此属性要求 [coclass](coclass.md)、 [progid](progid.md)或 [vi_progid](vi-progid.md) 属性（或隐含这些属性之一的其他属性）也应用于同一个元素。 如果使用任何单个属性，则会自动应用另外两个属性。 例如，如果 `progid` 应用了，则 `vi_progid` `coclass` 还会应用。

## <a name="example"></a>示例

下面的代码指定以下对象实现 `Control` 类别。

```cpp
// cpp_attr_ref_implements_category.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="MyLib")];
[ coclass, implements_category("CATID_Control"),
  uuid("20a0d0cc-5172-40f5-99ae-5e032f3205ae")]
class CMyClass {};
```

## <a name="requirements"></a>要求

| 特性上下文 | 值 |
|-|-|
|**适用于**|**`class`**, **`struct`**|
|**且**|是|
|**必需属性**|以下项之一： `coclass` 、 `progid` 或 `vi_progid`|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[COM 特性](com-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[IMPLEMENTED_CATEGORY](../../atl/reference/category-macros.md#implemented_category)

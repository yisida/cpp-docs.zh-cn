---
description: 了解详细信息： switch_type
title: 'switch_type (c + + COM 特性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.switch_type
helpviewer_keywords:
- switch_type attribute
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
ms.openlocfilehash: e291524d00afff89aa17634307426ef62cd40f4b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327259"
---
# <a name="switch_type"></a>switch_type

标识用作联合判别的变量的类型。

## <a name="syntax"></a>语法

```cpp
[switch_type(
type
}]
```

### <a name="parameters"></a>参数

type<br/>
开关类型可以是整数、字符、布尔值或枚举类型。

## <a name="remarks"></a>备注

**Switch_type** c + + 特性具有与 [switch_type](/windows/win32/Midl/switch-type) MIDL 特性相同的功能。

C + + 特性不支持 [封装的联合](/windows/win32/Midl/encapsulated-unions)。 仅支持以下格式的[Nonencapsulated 联合](/windows/win32/Midl/nonencapsulated-unions)：

```cpp
// cpp_attr_ref_switch_type.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLibrary")];
[ export ]
struct SizedValue2 {
   [switch_type("char"), switch_is(kind)] union {
      [case(1), string]
         wchar_t* wval;
      [default, string]
         char* val;
   };
   char kind;
};
```

## <a name="example"></a>示例

有关 **switch_type** 的示例用法，请参阅 [事例](case-cpp.md)示例。

## <a name="requirements"></a>要求

| 特性上下文 | 值 |
|-|-|
|**适用于**|**`typedef`**|
|**且**|否|
|**必需属性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[先导](export.md)

---
description: '了解详细信息： false (c + +) '
title: false (C++)
ms.date: 11/04/2016
f1_keywords:
- false_cpp
helpviewer_keywords:
- false keyword [C++]
ms.assetid: cc13aec5-1f02-4d38-8dbf-5473ea2b354f
ms.openlocfilehash: 73f1f07c858f0a578cc2d3135e560cc8e0cb9d32
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319451"
---
# <a name="false-c"></a>false (C++)

关键字是类型为 [bool](../cpp/bool-cpp.md) 的变量或条件表达式的两个值中的一个值 (条件表达式现在为 **`true`** 布尔表达式) 。 例如，如果 `i` 是类型为的变量 **`bool`** ，则该 `i = false;` 语句将分配 **`false`** 给 `i` 。

## <a name="example"></a>示例

```cpp
// bool_false.cpp
#include <stdio.h>

int main()
{
    bool bb = true;
    printf_s("%d\n", bb);
    bb = false;
    printf_s("%d\n", bb);
}
```

```Output
1
0
```

## <a name="see-also"></a>请参阅

[关键字](../cpp/keywords-cpp.md)

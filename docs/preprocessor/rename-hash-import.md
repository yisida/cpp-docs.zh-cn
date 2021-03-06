---
description: 了解详细信息：重命名导入属性
title: 重命名导入属性
ms.date: 08/29/2019
helpviewer_keywords:
- rename attribute
ms.assetid: 5c5c6153-1087-4b7b-87fb-fc59b90b9975
ms.openlocfilehash: 3003300887dadbab5cf05396ff3fa38b6dd29026
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176595"
---
# <a name="rename-import-attribute"></a>重命名导入属性

**C++ 专用**

解决名称冲突问题。

## <a name="syntax"></a>语法

> **#import** *类型-库***重命名 (** "*OldName*" **、** "*NewName*" **)**

### <a name="parameters"></a>parameters

*OldName*\
类型库中的旧名称。

*NewName*\
要替代旧名称使用的名称。

## <a name="remarks"></a>备注

当指定 **rename** 特性时，编译器会将 *类型库* 中出现的所有 *OldName* 替换为生成的标头文件中的用户提供的 *NewName* 。

当类型库中的名称与系统头文件中的宏定义一致时，可以使用 **rename** 特性。 如果未解决这种情况，编译器可能会发出多种语法错误，如 [编译器错误 C2059](../error-messages/compiler-errors-1/compiler-error-c2059.md) 和 [编译器错误 C2061](../error-messages/compiler-errors-1/compiler-error-c2061.md)。

> [!NOTE]
> 该替换是针对类型库中使用的名称，而不是针对生成的标头文件中的名称。

例如，假设类型库中存在名为 `MyParent` 的属性，并且在标头文件中定义了宏 `GetMyParent`，在 `#import` 前面使用了该宏。 由于 `GetMyParent` 是错误处理属性的包装函数的默认名称，因此会 `get` 发生名称冲突。 若要解决此问题，请在 `#import` 语句中使用以下特性：

```cpp
#import MyTypeLib.tlb rename("MyParent","MyParentX")
```

该语句对类型库中的名称 `MyParent` 重命名。 尝试对 `GetMyParent` 包装器名称重命名将失败：

```cpp
#import MyTypeLib.tlb rename("GetMyParent","GetMyParentX")
```

这是因为该名称 `GetMyParent` 只出现在生成的类型库标头文件中。

**结束 C++ 专用**

## <a name="see-also"></a>请参阅

[#import 特性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指令](../preprocessor/hash-import-directive-cpp.md)

---
description: 了解更多：编译器错误 C2283
title: 编译器错误 C2283
ms.date: 11/04/2016
f1_keywords:
- C2283
helpviewer_keywords:
- C2283
ms.assetid: 8a5b3175-b480-4598-a1f7-0b50504c5caa
ms.openlocfilehash: dab8688623962051759f9f4be84f5831b58a700f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294972"
---
# <a name="compiler-error-c2283"></a>编译器错误 C2283

“identifier”：未命名的结构上不允许使用纯说明符或抽象重写说明符

使用纯说明符声明了未命名类或结构的成员函数，这是不允许的。

以下示例生成 C2283：

```cpp
// C2283.cpp
// compile with: /c
struct {
   virtual void func() = 0;   // C2283
};
struct T {
   virtual void func() = 0;   // OK
};
```

---
description: 了解更多：编译器错误 C3243
title: 编译器错误 C3243
ms.date: 11/04/2016
f1_keywords:
- C3243
helpviewer_keywords:
- C3243
ms.assetid: 35d8ad1a-377d-47df-be9d-c55eea23340f
ms.openlocfilehash: 068987c8e15cc4904d782a5288dff4f7f69acace
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307205"
---
# <a name="compiler-error-c3243"></a>编译器错误 C3243

“interface”未引入任何重载函数

你试图 [显式重写](../../cpp/explicit-overrides-cpp.md) 在指定接口中不存在的成员。

下面的示例生成 C3243：

```cpp
// C3243.cpp
#pragma warning(disable:4199)
__interface IX14A {
   void g();
};

__interface IX14B {
   void f();
   void f(int);
};

class CX14 : public IX14A, public IX14B {
public:
   void IX14A::g();
   void IX14B::f();
   void IX14B::f(int);
};

void CX14::IX14A::f()   // C3243 occurs here
{
}
```

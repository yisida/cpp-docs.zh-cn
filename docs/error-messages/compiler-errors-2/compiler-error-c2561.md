---
description: 了解更多：编译器错误 C2561
title: 编译器错误 C2561
ms.date: 11/04/2016
f1_keywords:
- C2561
helpviewer_keywords:
- C2561
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
ms.openlocfilehash: 11ec708d25af9fc9603977c33741a1f74a406e92
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144867"
---
# <a name="compiler-error-c2561"></a>编译器错误 C2561

"identifier"：函数必须返回值

该函数被声明为返回值，但函数定义不包含 **`return`** 语句。

此错误可能是由不正确的函数原型引起的：

1. 如果函数未返回值，请使用返回类型 [void](../../cpp/void-cpp.md)声明函数。

1. 检查函数的所有可能的分支是否返回在原型中声明的类型的值。

1. 包含在寄存器中存储返回值的内联程序集例程的 c + + 函数 `AX` 可能需要返回语句。 将中的值复制 `AX` 到临时变量，并从函数返回该变量。

下面的示例生成 C2561：

```cpp
// C2561.cpp
int Test(int x) {
   if (x) {
      return;   // C2561
      // try the following line instead
      // return 1;
   }
   return 0;
}

int main() {
   Test(1);
}
```

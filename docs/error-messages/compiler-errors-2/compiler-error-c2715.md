---
description: 了解更多：编译器错误 C2715
title: 编译器错误 C2715
ms.date: 11/04/2016
f1_keywords:
- C2715
helpviewer_keywords:
- C2715
ms.assetid: c81567a7-5b65-468f-aaf9-835f91e468e4
ms.openlocfilehash: 6575e5b678189834a035f9e236b3d768dc7ab368
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320803"
---
# <a name="compiler-error-c2715"></a>编译器错误 C2715

"type"：无法引发或捕捉此类型

在托管代码中使用异常处理时，值类型不是有效的参数 (有关详细信息，请参阅 [异常处理](../../extensions/exception-handling-cpp-component-extensions.md)) 。

```cpp
// C2715a.cpp
// compile with: /clr
using namespace System;

value struct V {
   int i;
};

void f1() {
   V v;
   v.i = 10;
   throw v;   // C2715
   // try the following line instead
   // throw ((V^)v);
}

int main() {
   try {
      f1();
   }

   catch(V v) { if ( v.i == 10 ) {   // C2715
   // try the following line instead
   // catch(V^ pv) { if ( pv->i == 10 ) {
         Console::WriteLine("caught 10 - looks OK");
      }
      else {
         Console::WriteLine("catch looks bad");
      }
   }
   catch(...) {
      Console::WriteLine("catch looks REALLY bad");
   }
}
```

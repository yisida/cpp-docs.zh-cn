---
description: 了解更多：编译器错误 C3231
title: 编译器错误 C3231
ms.date: 11/04/2016
f1_keywords:
- C3231
helpviewer_keywords:
- C3231
ms.assetid: fe5dc352-e634-45fa-9534-3da176294c98
ms.openlocfilehash: 4b6a89ab1c5ecefad62852d8214c8edc3c10ccb1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304085"
---
# <a name="compiler-error-c3231"></a>编译器错误 C3231

"arg"：模板类型参数不能使用泛型类型参数

模板在编译时实例化，而泛型在运行时实例化。 因此，不能生成可调用模板的泛型代码，因为当泛型类型在最后才已知时，模板不能在运行时实例化。

下面的示例生成 C3231：

```cpp
// C3231.cpp
// compile with: /clr /LD
template <class T> class A;

generic <class T>
ref class C {
   void f() {
      A<T> a;   // C3231
   }
};
```

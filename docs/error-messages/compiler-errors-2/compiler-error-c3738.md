---
description: 了解更多：编译器错误 C3738
title: 编译器错误 C3738
ms.date: 11/04/2016
f1_keywords:
- C3738
helpviewer_keywords:
- C3738
ms.assetid: dd3ee011-e204-4264-bf3a-da32c4ef7038
ms.openlocfilehash: 7ec94d2be4faa0324563b723eb8a674c2d2d274f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97244922"
---
# <a name="compiler-error-c3738"></a>编译器错误 C3738

"calling_convention"：显式实例化的调用约定必须与被实例化的模板的调用约定匹配

建议你不要在显式实例化上指定调用约定。 不过，如果必须，调用约定必须匹配。

## <a name="example"></a>示例

下面的示例生成 C3738。

```cpp
// C3738.cpp
// compile with: /clr
// processor: x86
#include <stdio.h>
template< class T >
void f ( T arg ) {   // by default calling convention is __cdecl
   printf ( "f: %s\n", __FUNCSIG__ );
}

template
void __stdcall f< int > ( int arg );   // C3738
// try the following line instead
// void f< int > ( int arg );

int main () {
   f(1);
   f< int > ( 1 );
}
```

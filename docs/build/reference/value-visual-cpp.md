---
description: 了解详细信息： &lt; 值&gt;
title: '&lt; (c + + 文档注释> 值) '
ms.date: 11/04/2016
f1_keywords:
- value
- <value>
helpviewer_keywords:
- value C++ XML tag
- <value> C++ XML tag
ms.assetid: 0ba0a0d5-bcd7-4862-a169-83f2721ad80e
ms.openlocfilehash: 110091607af7c973591384d44816f372f0d15b14
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187021"
---
# <a name="ltvaluegt"></a>&lt;value&gt;

\<value>标记可用于描述属性和属性访问器方法。 请注意，当您在 Visual Studio 集成开发环境中使用代码向导添加属性时，它将 [\<summary>](summary-visual-cpp.md) 为新属性添加标记。 然后，应手动添加 \<value> 标记，以描述属性表示的值。

## <a name="syntax"></a>语法

```
<value>property-description</value>
```

#### <a name="parameters"></a>parameters

*property-description*<br/>
属性的说明。

## <a name="remarks"></a>备注

使用 [/doc](doc-process-documentation-comments-c-cpp.md) 进行编译，将文档注释处理到文件中。

## <a name="example"></a>示例

```cpp
// xml_value_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_value_tag.dll
using namespace System;
/// Text for class Employee.
public ref class Employee {
private:
   String ^ name;
   /// <value>Name accesses the value of the name data member</value>
public:
   property String ^ Name {
      String ^ get() {
         return name;
      }
      void set(String ^ i) {
         name = i;
      }
   }
};
```

## <a name="see-also"></a>请参阅

[XML 文档](xml-documentation-visual-cpp.md)

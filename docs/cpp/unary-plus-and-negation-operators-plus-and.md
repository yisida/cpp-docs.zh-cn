---
description: 了解有关以下内容的详细信息：一元加运算符和求反运算符： + 和-
title: 一元加号和非运算符：+ 和 -
ms.date: 11/04/2016
f1_keywords:
- +
- '-'
helpviewer_keywords:
- unary operators [C++], plus
- '- operator'
- negation operator
- + operator [C++], unary operators
- + operator
ms.assetid: 2c58c4f4-0d92-4ae3-9d0c-1a6157875cc1
ms.openlocfilehash: 64478ccfa9191e5704c1e3c896b17bc0986dc0e5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97145764"
---
# <a name="unary-plus-and-negation-operators--and--"></a>一元加号和非运算符：+ 和 -

## <a name="syntax"></a>语法

```
+ cast-expression
- cast-expression
```

## <a name="-operator"></a>+ 运算符

一元加运算符 () 的结果 **+** 是操作数的值。 一元加运算符的操作数必须是一个算术类型。

整型提升是对整型操作数执行的。 结果类型是操作数将提升到的类型。 因此，expression `+ch` ，其中 `ch` 的类型为 **`char`** ，结果为类型 **`int`** ; 值不被修改。 请参阅 [标准转换](standard-conversions.md) ，了解有关如何完成升级的详细信息。

## <a name="--operator"></a>- 运算符

一元求反运算符 (**-**) 生成其操作数的负值。 一元求反运算符的操作数必须是算术类型。

将对整型操作数执行整型提升，并且结果类型将是操作数将提升到的类型。 有关如何执行升级的详细信息，请参阅 [标准转换](standard-conversions.md) 。

**Microsoft 专用**

通过从 2^n 中减去操作数的值来执行无符号数量的一元求反运算，其中 n 是给定的无符号类型的对象的位数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)<br/>
[C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)

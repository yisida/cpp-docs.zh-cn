---
description: 了解更多： c + + 程序启动和终止
title: C++ 程序启动和终止
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Standard Library, program startup and termination
- terminating execution
- Function Main procedures
- control text streams
- startup code, and C++ program termination
- main function, program startup
ms.assetid: f72c8f76-f507-4ddd-a270-7b60f4fed625
ms.openlocfilehash: 644be6d4392f8e41b1d1cf7d45b484ed9903d463
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324782"
---
# <a name="c-program-startup-and-termination"></a>C++ 程序启动和终止

C++ 程序执行的操作与 C 程序在程序启动及终止时所执行的操作相同，另外还执行此处所述的一些其他操作。

在目标环境调用函数 `main` 之前，以及将任何指定的常量初始值存储在具有静态持续时间的所有对象中后，程序将为这些静态对象执行任何剩余的构造函数。 执行顺序并未在转换单元之间指定，但你可以假设这些静态构造函数对某些 [iostreams](../standard-library/iostreams-conventions.md) 对象执行了正确初始化。 这些控制文本流为：

- [cin](../standard-library/iostream.md#cin) — 针对标准输入。

- [cout](../standard-library/iostream.md#cout) — 针对标准输出。

- [cerr](../standard-library/iostream.md#cerr) — 针对未缓冲的标准错误输出。

- [clog](../standard-library/iostream.md#clog) — 针对已缓冲的标准错误输出。

此外，还可以在程序终止期间，在为静态对象调用的析构函数中使用这些对象。

与 C 程序一样，从 `main` 返回或调用 `exit` 时，它会按相反顺序的注册表调用在 `atexit` 注册的所有函数。 从已注册函数引发的异常会调用 `terminate`。

## <a name="see-also"></a>请参阅

[C + + 标准库概述](../standard-library/cpp-standard-library-overview.md)\
[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

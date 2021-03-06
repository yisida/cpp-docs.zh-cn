---
description: 了解详细信息： &lt; codecvt&gt;
title: '&lt;codecvt&gt;'
ms.date: 11/04/2016
f1_keywords:
- codecvt
- <codecvt>
helpviewer_keywords:
- codecvt header
ms.assetid: d44ee229-00d5-4761-9b48-0c702122789d
ms.openlocfilehash: 454637427b4a2c058b8ee8cf4bb5b8bc99215e74
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97233963"
---
# <a name="ltcodecvtgt"></a>&lt;codecvt&gt;

定义了多个类模板，用于描述基于类模板 [codecvt](../standard-library/codecvt-class.md)的对象。 这些对象可用作 [区域设置 facet](../standard-library/locale-class.md#facet_class) ，它们控制类型的值序列 `Elem` 和类型的值序列之间的转换 **`char`** 。

## <a name="syntax"></a>语法

```cpp
#include <codecvt>
```

## <a name="remarks"></a>备注

在此标头中声明的区域设置 facet 在几个字符编码之间进行转换。 对于宽字符（存储在固定大小整数程序中）：

- UCS-4 是在程序内作为 32 位整数的编码的 Unicode (ISO 10646)。

- UCS-2 是在程序内作为 16 位整数的编码的 Unicode。

- UTF-16 是在程序内作为任意一个或两个 16 位整数的编码的 Unicode。 （请注意，这不符合标准 C 或标准 C++ 的有效宽字符编码的全部要求。 不过，它仍被广泛使用。）

对于字节流 (存储在文件中，以字节序列的形式传输，或存储在) 的数组中的程序内 **`char`** ：

- Utf-8 是字节流中已编码的 Unicode，为具有确定性字节顺序的一个或多个八位字节。

- UTF 16LE 是字节流中作为 UTF-16 已编码的 Unicode，每个 16 位整数表示为两个八位字节，不重要字节优先。

- UTF 16BE 是字节流中作为 UTF-16 已编码的 Unicode，每个 16 位整数表示为两个八位字节，重要字节优先。

### <a name="enumerations"></a>枚举

|名称|描述|
|-|-|
|[codecvt_mode](../standard-library/codecvt-enums.md#codecvt_mode)|指定区域设置 facet 的配置信息。|

### <a name="classes"></a>类

|类|描述|
|-|-|
|[codecvt_utf8](codecvt-utf8-class.md)|表示在编码为 UCS-2 或 UCS-4 的宽字符和编码为 UTF-8 的字节流之间转换的区域设置 facet。|
|[codecvt_utf8_utf16](codecvt-utf8-utf16-class.md)|表示在编码为 UTF-16 的宽字符和编码为 UTF-8 的字节流之间转换的区域设置 facet。|
|[codecvt_utf16](codecvt-utf16-class.md)|表示在编码为 UCS-2 或 UCS-4 的宽字符和编码为 UTF-16LE 或 UTF-16BE 的字节流之间转换的区域设置 facet。|

## <a name="requirements"></a>要求

**标头：**\<codecvt>

**命名空间:** std

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)

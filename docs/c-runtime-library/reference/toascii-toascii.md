---
description: 了解详细信息： toascii、__toascii
title: toascii、__toascii
ms.date: 11/04/2016
api_name:
- __toascii
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __toascii
- toascii
- ctype/toascii
- ctype/__toascii
helpviewer_keywords:
- toascii function
- string conversion, to ASCII characters
- __toascii function
- ASCII characters, converting to
ms.assetid: a07c0608-b0e2-4da2-a20c-7b64d6a9b77c
ms.openlocfilehash: 9f1718da5e7d701bb6cc6ea68c1e21b6fe4283f2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318346"
---
# <a name="toascii-__toascii"></a>toascii、__toascii

通过截断将字符转换为 7 位 ASCII。

## <a name="syntax"></a>语法

```C
int __toascii(
   int c
);
#define toascii __toascii
```

### <a name="parameters"></a>parameters

*c*<br/>
要转换的字符。

## <a name="return-value"></a>返回值

**__toascii** 将 *c* 的值转换为7位 ASCII 范围并返回结果。 没有保留任何返回值以指示错误。

## <a name="remarks"></a>备注

**__Toascii** 例程通过将给定字符截断为低序位7位，将该字符转换为 ASCII 字符。 未应用其他转换。

**__Toascii** 例程定义为宏，除非定义了预处理器宏 _CTYPE_DISABLE_MACROS。 为实现向后兼容性，仅当未定义 [&#95;&#95;STDC&#95;&#95;](../../preprocessor/predefined-macros.md)或将其定义为0时，才将 **toascii** 定义为宏;否则为未定义。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**toascii**、 **__toascii**|Ansi-c \<ctype.h><br /><br /> C + +： \<cctype> 或 \<ctype.h>|

**Toascii** 宏是 posix 扩展， **__toascii** 是 posix 扩展的特定于 Microsoft 的实现。 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[为，isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>
[to 函数](../../c-runtime-library/to-functions.md)<br/>

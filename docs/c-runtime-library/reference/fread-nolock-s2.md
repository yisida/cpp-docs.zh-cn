---
description: 了解详细信息： _fread_nolock_s
title: _fread_nolock_s2
ms.date: 4/2/2020
api_name:
- _fread_nolock_s
- _o__fread_nolock_s
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _fread_nolock_s
- stdio/_fread_nolock_s
ms.assetid: 5badb9ab-11df-4e17-8162-30bda2a4572e
ms.openlocfilehash: ba971d8db9fde15009362b2e8da0791883fb64e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97283064"
---
# <a name="_fread_nolock_s"></a>_fread_nolock_s

读取流中的数据，而不锁定其他线程。 这是 [fread_nolock](fread-nolock.md) 版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。

## <a name="syntax"></a>语法

```C
size_t _fread_nolock_s(
   void *buffer,
   size_t bufferSize,
   size_t elementSize,
   size_t elementCount,
   FILE *stream
);
```

### <a name="parameters"></a>parameters

*宽限*<br/>
数据的存储位置。

*bufferSize*<br/>
目标缓冲区的大小（以字节为单位）。

*elementSize*<br/>
要读取的项的大小（以字节为单位）。

*Elementcount 多于*<br/>
要读取的项的最大数量。

*流*<br/>
指向 **文件** 结构的指针。

## <a name="return-value"></a>返回值

请参阅 [fread_s](fread-s.md)。

## <a name="remarks"></a>备注

此函数是 **fread_s** 的非锁定版本。 它与 **fread_s** 完全相同，只不过它不会受到其他线程的干扰。 它可能更快，因为它不会产生锁定其他线程的开销。 仅在线程安全的上下文中使用此函数，如单线程应用程序或调用范围已处理线程隔离的区域。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_fread_nolock_s**|C： \<stdio.h> ;C + +： \<cstdio> 或 \<stdio.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>

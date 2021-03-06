---
description: 了解详细信息： wctomb、_wctomb_l
title: wctomb、_wctomb_l
ms.date: 4/2/2020
api_name:
- _wctomb_l
- wctomb
- _o__wctomb_l
- _o_wctomb
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctomb
helpviewer_keywords:
- string conversion, wide characters
- wide characters, converting
- _wctomb_l function
- wctomb function
- wctomb_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 4a543f0e-5516-4d81-8ff2-3c5206f02ed5
ms.openlocfilehash: f49915d062aa602ab361084cbcc7a9a034599de2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97136807"
---
# <a name="wctomb-_wctomb_l"></a>wctomb、_wctomb_l

将宽字符转换为对应的多字节字符。 提供这些函数的更多安全版本；请参阅 [wctomb_s、_wctomb_s_l](wctomb-s-wctomb-s-l.md)。

## <a name="syntax"></a>语法

```C
int wctomb(
   char *mbchar,
   wchar_t wchar
);
int _wctomb_l(
   char *mbchar,
   wchar_t wchar,
   _locale_t locale
);
```

### <a name="parameters"></a>parameters

*mbchar*<br/>
多字节字符的地址。

*wchar*<br/>
宽字符。

## <a name="return-value"></a>返回值

如果 **wctomb** 将宽字符转换为多字节字符，它将返回 (的字节数，该字节数绝不会大于宽字符中 **MB_CUR_MAX**) 。 如果 *wchar* 是 "\ 0" )  (的宽字符 null 字符，则 **wctomb** 返回1。 如果目标指针 *mbchar* 为 **NULL**，则 **wctomb** 返回0。 如果当前区域设置中不能进行转换，则 **wctomb** 将返回-1，并将 **Errno** 设置为 **eilseq 且**。

## <a name="remarks"></a>备注

**Wctomb** 函数将其 *wchar* 参数转换为相应的多字节字符，并将结果存储在 *mbchar*。 可以从任何程序的任何程序点调用该函数。 **wctomb** 为任何与区域设置相关的行为使用当前区域设置; **_wctomb_l** 与 **wctomb** 相同，只不过它使用传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

**wctomb** 验证其参数。 如果 *mbchar* 为 **NULL**，则将调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则将 **errno** 设置为 **EINVAL** ，并且该函数将返回-1。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**wctomb**|\<stdlib.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

本程序演示 wctomb 函数的行为。

```cpp
// crt_wctomb.cpp
// compile with: /W3
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int i;
   wchar_t wc = L'a';
   char *pmb = (char *)malloc( MB_CUR_MAX );

   printf( "Convert a wide character:\n" );
   i = wctomb( pmb, wc ); // C4996
   // Note: wctomb is deprecated; consider using wctomb_s
   printf( "   Characters converted: %u\n", i );
   printf( "   Multibyte character: %.1s\n\n", pmb );
}
```

```Output
Convert a wide character:
   Characters converted: 1
   Multibyte character: a
```

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>

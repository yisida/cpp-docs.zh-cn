---
description: 了解详细信息： wcstombs、_wcstombs_l
title: wcstombs、_wcstombs_l
ms.date: 4/2/2020
api_name:
- wcstombs
- _wcstombs_l
- _o__wcstombs_l
- _o_wcstombs
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
- wcstombs
- _wcstombs_l
helpviewer_keywords:
- _wcstombs_l function
- wcstombs function
- string conversion, wide characters
- wide characters, converting
- wcstombs_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 91234252-9ea1-423a-af99-e9d0ce4a40e3
ms.openlocfilehash: 070ba4dbf574ccd6b1afaec074dc9eb9f311e728
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97136833"
---
# <a name="wcstombs-_wcstombs_l"></a>wcstombs、_wcstombs_l

将宽字符序列转换为对应的多字节字符序列。 提供这些函数的更多安全版本；请参阅 [wcstombs_s、_wcstombs_s_l](wcstombs-s-wcstombs-s-l.md)。

## <a name="syntax"></a>语法

```C
size_t wcstombs(
   char *mbstr,
   const wchar_t *wcstr,
   size_t count
);
size_t _wcstombs_l(
   char *mbstr,
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
size_t wcstombs(
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count
); // C++ only
template <size_t size>
size_t _wcstombs_l(
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>parameters

*mbstr*<br/>
多字节字符序列的地址。

*wcstr*<br/>
宽字符序列的地址。

*计数*<br/>
多字节输出字符串可以存储的最大字节数。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

如果 **wcstombs** 成功转换多字节字符串，则它将返回写入多字节输出字符串的字节数，如果有任何) ，则不包括终止 null (。 如果 *mbstr* 参数为 **NULL**，则 **wcstombs** 返回目标字符串所需的大小（以字节为单位）。 如果 **wcstombs** 遇到不能转换为多字节字符的宽字符，则将返回-1 强制转换为类型 **size_t** ，并将 **errno** 设置为 **eilseq 且**。

## <a name="remarks"></a>备注

**Wcstombs** 函数将 *wcstr* 指向的宽字符字符串转换为相应的多字节字符，并将结果存储在 *mbstr* 数组中。 *Count* 参数指示多字节输出字符串可以存储的最大字节数， (即 *mbstr*) 的大小。 一般情况下，转换宽字符字符串时不会知道需要多少个字节。 某些宽字符在输出字符串中仅占一个字节；其他的字符则占两个。 如果输入字符串中的每个宽字符的多字节输出字符串中有两个字节 (包括宽字符 null) ，则结果将保证合适。

如果 **wcstombs** 遇到 "\ 0" (的宽字符空字符 ) 在 *count* 之前或之后发生，则将其转换为8位0并停止。 因此，仅当 **wcstombs** 在转换期间遇到宽字符 null 字符时， *mbstr* 处的多字节字符串才以 null 结尾。 如果由 *wcstr* 和 *mbstr* 指向的序列重叠，则 **wcstombs** 的行为不确定。

如果 *mbstr* 参数为 **NULL**，则 **wcstombs** 返回目标字符串所需的大小（以字节为单位）。

**wcstombs** 验证其参数。 如果 *wcstr* 为 **NULL**，或者 *计数* 大于 **INT_MAX**，则此函数将调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。 如果允许执行继续，则该函数将 **errno** 设置为 **EINVAL** ，并返回-1。

**wcstombs** 为任何与区域设置相关的行为使用当前区域设置; **_wcstombs_l** 相同，只不过它使用传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

在 C++ 中，这些函数具有模板重载，以调用这些函数的更新、更安全副本。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**wcstombs**|\<stdlib.h>|
|**_wcstombs_l**|\<stdlib.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

此程序演示 **wcstombs** 函数的行为。

```C
// crt_wcstombs.c
// compile with: /W3
// This example demonstrates the use
// of wcstombs, which converts a string
// of wide characters to a string of
// multibyte characters.

#include <stdlib.h>
#include <stdio.h>

#define BUFFER_SIZE 100

int main( void )
{
    size_t  count;
    char    *pMBBuffer = (char *)malloc( BUFFER_SIZE );
    wchar_t *pWCBuffer = L"Hello, world.";

    printf("Convert wide-character string:\n" );

    count = wcstombs(pMBBuffer, pWCBuffer, BUFFER_SIZE ); // C4996
    // Note: wcstombs is deprecated; consider using wcstombs_s instead
    printf("   Characters converted: %u\n",
            count );
    printf("    Multibyte character: %s\n\n",
           pMBBuffer );

    free(pMBBuffer);
}
```

```Output
Convert wide-character string:
   Characters converted: 13
    Multibyte character: Hello, world.
```

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>

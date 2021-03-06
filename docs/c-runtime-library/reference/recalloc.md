---
description: 了解详细信息： _recalloc
title: _recalloc
ms.date: 4/2/2020
api_name:
- _recalloc
- _o__recalloc
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _recalloc
- recalloc
helpviewer_keywords:
- _recalloc function
- recalloc function
ms.assetid: 1db8305a-3f03-418c-8844-bf9149f63046
ms.openlocfilehash: 09cecc0b7fe006ca5f52340254534fcc67b70e84
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205169"
---
# <a name="_recalloc"></a>_recalloc

**Realloc** 和 **calloc** 的组合。 重新分配内存中的数组并将其元素初始化为 0。

## <a name="syntax"></a>语法

```C
void *_recalloc(
   void *memblock
   size_t num,
   size_t size
);
```

### <a name="parameters"></a>parameters

*memblock*<br/>
指向之前已分配内存块的指针。

*数字*<br/>
元素数量。

*大小*<br/>
每个元素的长度（以字节为单位）。

## <a name="return-value"></a>返回值

**_recalloc** 返回指向重新 **`void`** 分配的 (并可能移动) 内存块的指针。

如果没有足够的可用内存将块扩展到给定大小，则原始块将保持不变，并返回 **NULL** 。

如果请求的大小为零，则释放由 *memblock* 指向的块;返回值为 **NULL**， *memblock* 将指向已释放的块。

返回值将指向保证适当对齐任何类型的对象的存储的存储空间。 若要获取指向类型而非的指针 **`void`** ，请在返回值上使用类型转换。

## <a name="remarks"></a>备注

**_Recalloc** 函数更改已分配内存块的大小。 *Memblock* 参数指向内存块的开头。 如果 *memblock* 为 **NULL**，则 **_recalloc** 的行为方式与 [calloc](calloc.md)相同，并分配新的 *数字*  *  *大小* 字节块。 将每个元素初始化为 0。 如果 *memblock* 不为 **NULL**，则它应为先前对 **calloc**、 [malloc](malloc.md)或 [realloc](realloc.md)的调用返回的指针。

因为新块可以在新的内存位置，所以 **_recalloc** 返回的指针不一定是通过 *memblock* 参数传递的指针。

如果内存分配失败或请求的内存量超过 **_HEAP_MAXREQ**， **_recalloc** 将 **errno** 设置为 **ENOMEM** 。 有关此代码及其他错误代码的信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

**recalloc** 调用 **realloc** ，以便使用 c + + [_set_new_mode](set-new-mode.md) 函数设置新的处理程序模式。 新处理程序模式指示在失败时， **realloc** 是否调用 [_set_new_handler](set-new-handler.md)设置的新处理程序例程。 默认情况下， **realloc** 不会在失败时调用新的处理程序例程来分配内存。 您可以重写此默认行为，以便在 **_recalloc** 无法分配内存时， **realloc** 会调用新的处理程序例程，方法与 **`new`** 运算符在同一原因发生故障时相同。 若要重写默认值，请在程序的早期调用：

```C
_set_new_mode(1);
```

或链接到 NEWMODE.OBJ。

当应用程序与调试版的 C 运行时库链接时， **_recalloc** 解析为 [_recalloc_dbg](recalloc-dbg.md)。 有关在调试过程中如何托管堆的详细信息，请参阅 [CRT 调试堆](/visualstudio/debugger/crt-debug-heap-details)。

**_recalloc** 标记为 `__declspec(noalias)` ， `__declspec(restrict)` 这意味着该函数保证不修改全局变量，并且返回的指针没有化名。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md) 和[限制](../../cpp/restrict.md)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_recalloc**|\<stdlib.h> 和 \<malloc.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
[_recalloc_dbg](recalloc-dbg.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
[free](free.md)<br/>
[链接选项](../../c-runtime-library/link-options.md)<br/>

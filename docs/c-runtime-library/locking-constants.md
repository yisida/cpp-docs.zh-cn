---
description: 了解详细信息： _locking 常量
title: _locking 常量
ms.date: 11/04/2016
f1_keywords:
- _LK_RLCK
- _LK_NBLCK
- _LK_LOCK
- _LK_NBRLCK
- _LK_UNLCK
helpviewer_keywords:
- LK_UNLCK constant
- LK_NBRLCK constant
- _LK_NBRLCK constant
- _LK_NBLCK constant
- _LK_LOCK constant
- LK_NBLCK constant
- _LK_UNLCK constant
- LK_RLCK constant
- _LK_RLCK constant
- LK_LOCK constant
ms.assetid: c3dc92c8-60e3-4d29-9f50-5d217627c8ad
ms.openlocfilehash: 143c1416dada19e0bd35f1607d77826d98817879
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331023"
---
# <a name="_locking-constants"></a>_locking 常量

## <a name="syntax"></a>语法

```
#include <sys/locking.h>
```

## <a name="remarks"></a>备注

`_locking` 函数调用中的 mode 参数指定要执行的锁定操作。

mode 参数必须是以下清单常量之一。

|值|描述|
|-|-|
| `_LK_LOCK`  | 锁定指定字节。 如果无法锁定字节，该函数会在 1 秒后再次尝试。 如果在 10 次尝试后仍无法锁定字节，该函数将返回一个错误。  |
| `_LK_RLCK`  | 与 `_LK_LOCK` 相同。  |
|`_LK_NBLCK`  | 锁定指定字节。 如果无法锁定字节，该函数将返回一个错误。  |
| `_LK_NBRLCK`  | 与 `_LK_NBLCK` 相同。  |
| `_LK_UNLCK`  | 解锁指定字节。 （这些字节必须在之前锁定。）  |

## <a name="see-also"></a>请参阅

[_locking](../c-runtime-library/reference/locking.md)<br/>
[全局常量](../c-runtime-library/global-constants.md)

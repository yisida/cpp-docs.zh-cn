---
description: 了解详细信息：像素/HIMETRIC 转换全局函数
title: 像素 HIMETRIC 转换全局函数
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
ms.openlocfilehash: 53753ff92b04466a94b821fdc4b4f221117c6ade
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138978"
---
# <a name="pixelhimetric-conversion-global-functions"></a>象素/HIMETRIC 转换全局函数

这些函数为转换到像素和 HIMETRIC 单元提供支持。

> [!IMPORTANT]
> 下表中列出的函数不能用于在 Windows 运行时中执行的应用程序。

|名称|描述|
|-|-|
|[AtlHiMetricToPixel](#atlhimetrictopixel)|将每个单位 (的 HIMETRIC 单位转换为0.01 毫米) 为像素。|
|[AtlPixelToHiMetric](#atlpixeltohimetric)|将像素转换为 HIMETRIC 单位 (每个单位的) 为0.01 毫米。|

## <a name="atlhimetrictopixel"></a><a name="atlhimetrictopixel"></a> AtlHiMetricToPixel

将以 HIMETRIC 为单位（每个单位是 0.01 毫米）的对象大小转换为以屏幕设备上的像素为单位的大小。

```
extern void AtlHiMetricToPixel(
    const SIZEL* lpSizeInHiMetric,
    LPSIZEL lpSizeInPix);
```

### <a name="parameters"></a>parameters

*lpSizeInHiMetric*<br/>
中指向对象的大小的指针，以 HIMETRIC 单位表示。

*lpSizeInPix*<br/>
弄一个指针，指向要返回对象的大小（以像素为单位）的位置。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#49](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_1.cpp)]

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="atlpixeltohimetric"></a><a name="atlpixeltohimetric"></a> AtlPixelToHiMetric

将以屏幕设备上的像素为单位的对象大小转换为以 HIMETRIC 为单位（每个单位是 0.01 毫米）的大小。

```
extern void AtlPixelToHiMetric(
    const SIZEL* lpSizeInPix,
    LPSIZEL lpSizeInHiMetric);
```

### <a name="parameters"></a>parameters

*lpSizeInPix*<br/>
中一个指针，指向对象的大小（以像素为单位）。

*lpSizeInHiMetric*<br/>
弄一个指针，指向要返回对象在 HIMETRIC 单位中的大小的位置。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#51](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="see-also"></a>请参阅

[函数](../../atl/reference/atl-functions.md)

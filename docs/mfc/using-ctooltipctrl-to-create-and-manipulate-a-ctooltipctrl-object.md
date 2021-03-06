---
description: 了解详细信息：使用 CToolTipCtrl 创建和操作 CToolTipCtrl 对象
title: 使用 CToolTipCtrl 创建和操作 CToolTipCtrl 对象
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], creating
- CToolTipCtrl class [MFC], using
ms.assetid: 0a34583f-f66d-46a1-a239-31b80ea395ad
ms.openlocfilehash: 363d46ce078b71cf88d742ae390ab674a73ab935
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202335"
---
# <a name="using-ctooltipctrl-to-create-and-manipulate-a-ctooltipctrl-object"></a>使用 CToolTipCtrl 创建和操作 CToolTipCtrl 对象

下面是 [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) 用法的示例：

### <a name="to-create-and-manipulate-a-ctooltipctrl"></a>创建和操作 CToolTipCtrl

1. 构造 `CToolTipCtrl` 对象。

1. 调用 [create](../mfc/reference/ctooltipctrl-class.md#create) 创建 Windows 工具提示公共控件并将其附加到 `CToolTipCtrl` 对象。

1. 调用 [AddTool](../mfc/reference/ctooltipctrl-class.md#addtool) ，将工具注册到工具提示控件，以便在光标位于工具上时显示工具提示中存储的信息。

1. 调用 [SetToolInfo](../mfc/reference/ctooltipctrl-class.md#settoolinfo) 可设置工具提示为工具维护的信息。

1. 调用 [SetToolRect](../mfc/reference/ctooltipctrl-class.md#settoolrect) 为工具设置新的边框。

1. 调用 [system.windows.media.visualtreehelper.hittest](../mfc/reference/ctooltipctrl-class.md#hittest) 来测试一个点，以确定它是否位于给定工具的边框内，如果是，则检索有关该工具的信息。

1. 调用 [GetToolCount](../mfc/reference/ctooltipctrl-class.md#gettoolcount) 可检索已注册到工具提示控件的工具的计数。

## <a name="see-also"></a>请参阅

[使用 CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

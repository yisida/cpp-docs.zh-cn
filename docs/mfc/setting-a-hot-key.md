---
description: 了解详细信息：设置热键
title: 设置热键
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
ms.openlocfilehash: fa713be2d478eb18b11dca27558656e5e6993076
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217180"
---
# <a name="setting-a-hot-key"></a>设置热键

应用程序可以通过以下两种方式之一使用热键 ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) 控件提供的信息：

- 通过向要激活的窗口发送 [WM_SETHOTKEY](/windows/win32/inputdev/wm-sethotkey) 消息，设置用于激活 nonchild 窗口的全局热键。

- 通过调用 Windows 函数 [RegisterHotKey](/windows/win32/api/winuser/nf-winuser-registerhotkey)设置线程特定的热键。

## <a name="see-also"></a>请参阅

[使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

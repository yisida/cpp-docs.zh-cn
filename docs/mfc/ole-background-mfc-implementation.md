---
description: 了解更多： OLE 背景： MFC 实现
title: OLE 后台：MFC 实现
ms.date: 11/04/2016
f1_keywords:
- IMarshall
- IMoniker
helpviewer_keywords:
- MFC libraries, implementing
- OLE MFC library implementation
- OLE IMarshal interface
- IMoniker interface, MFC
- IMarshall class [MFC]
- OLE, compound files
- OLE IMoniker interface
- OLE IUnknown
ms.assetid: 2b67016a-d78e-4d60-925f-c28ec8fb6180
ms.openlocfilehash: 81b62fc1ff704a8a0f34bfd1ac864142720b3864
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343537"
---
# <a name="ole-background-mfc-implementation"></a>OLE 后台：MFC 实现

由于原始 OLE API 的大小和复杂性，直接调用它来编写 OLE 应用程序会非常耗时。 OLE 的 Microsoft 基础类库实现的目的是减少编写功能齐全、具有 OLE 功能的应用程序所必须进行的工作量。

本文将介绍 MFC 中尚未实现的部分 OLE API。 讨论还介绍了如何实现如何映射到 Windows SDK 的 OLE 部分。

## <a name="portions-of-ole-not-implemented-by-the-class-library"></a><a name="_core_portions_of_ole_not_implemented_by_the_class_library"></a> 类库未实现的 OLE 部分

MFC 未直接提供 OLE 的一些接口和功能。 如果您要使用这些功能，可以直接调用 OLE API。

IMoniker 接口 `IMoniker` ：接口由类库实现 (例如， `COleServerItem` 类) ，但之前未向程序员公开。 有关此接口的详细信息，请参阅 Windows SDK 的 OLE 部分中的 OLE 名字对象实现。 但请参阅类 [CMonikerFile](reference/cmonikerfile-class.md) 和 [CAsyncMonikerFile](reference/casyncmonikerfile-class.md)。

IUnknown 和 IMarshal 接口此 `IUnknown` 接口由类库实现，但不向程序员公开。 `IMarshal`接口不是由类库实现，而是在内部使用。 使用类库生成的自动化服务器已内置了封送功能。

类库) 部分支持复合文件 (复合文件的 Docfiles。 任何直接操作复合文件的函数（创建复合文件的函数除外）都不受支持。 MFC 使用类 `COleFileStream` 来支持使用标准文件函数对流进行操作。 有关详细信息，请参阅文章 [容器：复合文件](containers-compound-files.md)。

在进程内服务器和对象处理程序中 In-Process 服务器和对象处理程序允许在动态链接库中 (COM) 对象实现可视化编辑数据或完全组件对象模型 (DLL) 。 为此，可以通过直接调用 OLE API 实现 DLL。 但是，如果您正在编写自动化服务器而且该服务器没有用户界面，则可使用 AppWizard 使该服务器成为进程内服务器并将其完全置于 DLL 中。 有关这些主题的详细信息，请参阅 [自动化服务器](automation-servers.md)。

> [!TIP]
> 实现自动化服务器的最简单方法是将它置于 DLL 中。 MFC 支持这种做法。

有关 Microsoft 基础 OLE 类如何实现 OLE 接口的详细信息，请参阅 MFC 技术说明 [38](tn038-mfc-ole-iunknown-implementation.md)、 [39](tn039-mfc-ole-automation-implementation.md)和 [40](tn040-mfc-ole-in-place-resizing-and-zooming.md)。

## <a name="see-also"></a>请参阅

[OLE 背景](ole-background.md)<br/>
[OLE 后台：实现策略](ole-background-implementation-strategies.md)

---
description: 了解详细信息： ATL 连接点
title: ATL 连接点
ms.date: 11/04/2016
helpviewer_keywords:
- connections, connection points
- ATL, connection points
- connection points [C++], about connection points
ms.assetid: 17d76165-5f83-4f95-b36d-483821c247a1
ms.openlocfilehash: 60b9018185bea2af26407ee9d7a203148c8dc477
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165818"
---
# <a name="atl-connection-points"></a>ATL 连接点

可连接对象是支持输出接口的对象。 输出接口允许对象与客户端进行通信。 对于每个输出接口，可连接对象都释放一个连接点。 每个输出接口是由调用接收器的对象上的客户端实现的。

![连接点](../atl/media/vc2zw31.gif "连接点")

每个连接点都支持 [IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint) 接口。 可连接对象通过 [IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer) 接口向客户端公开其连接点。

## <a name="in-this-section"></a>本节内容

[ATL 连接点类](../atl/atl-connection-point-classes.md)<br/>
简要介绍支持连接点的 ATL 类。

[向对象添加连接点](../atl/adding-connection-points-to-an-object.md)<br/>
概述了用于将连接点添加到对象的步骤。

[ATL 连接点示例](../atl/atl-connection-point-example.md)<br/>
提供了声明连接点的一个示例。

## <a name="related-sections"></a>相关章节

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
提供了关于如何使用 Active Template Library 进行编程的概念性主题的链接。

## <a name="see-also"></a>请参阅

[概念](../atl/active-template-library-atl-concepts.md)

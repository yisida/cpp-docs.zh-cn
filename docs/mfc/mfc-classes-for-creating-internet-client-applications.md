---
description: 了解更多：用于创建 Internet 客户端应用程序的 MFC 类
title: 用于创建 Internet 客户端应用程序的 MFC 类
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, WinInet classes
- WinInet classes [MFC], classes
- classes [MFC], MFC
- Internet client applications [MFC], MFC
- Internet applications [MFC], MFC
ms.assetid: 67d34117-9839-4f4b-8bb8-0e4a9471c606
ms.openlocfilehash: c68110182b01d9c425090a926ee1e352ca3d3bdf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280672"
---
# <a name="mfc-classes-for-creating-internet-client-applications"></a>用于创建 Internet 客户端应用程序的 MFC 类

MFC 提供了以下用于编写 Internet 客户端应用程序的类和全局函数。 缩进指示类派生自其上方的未缩进的类。 `CGopherFile``CHttpFile` `CInternetFile` 例如，派生自。 这些类和全局函数在 AFXINET.H 中声明。H， `CFileFind` 在 AFX 中声明的除外。

## <a name="classes"></a>类

- [CInternetSession](reference/cinternetsession-class.md)

- [CInternetConnection](reference/cinternetconnection-class.md)

  - [CFtpConnection](reference/cftpconnection-class.md)

  - [CGopherConnection](reference/cgopherconnection-class.md)

  - [CHttpConnection](reference/chttpconnection-class.md)

- [CInternetFile](reference/cinternetfile-class.md)

  - [CGopherFile](reference/cgopherfile-class.md)

  - [CHttpFile](reference/chttpfile-class.md)

- [CFileFind](reference/cfilefind-class.md)

  - [CFtpFileFind](reference/cftpfilefind-class.md)

  - [CGopherFileFind](reference/cgopherfilefind-class.md)

- [CGopherLocator](reference/cgopherlocator-class.md)

- [CInternetException](reference/cinternetexception-class.md)

## <a name="global-functions"></a>全局函数

- [AfxParseURL](reference/internet-url-parsing-globals.md#afxparseurl)

- [AfxGetInternetHandleType](reference/internet-url-parsing-globals.md#afxgetinternethandletype)

- [AfxThrowInternetException](reference/internet-url-parsing-globals.md#afxthrowinternetexception)

## <a name="see-also"></a>请参阅

[ (WinInet) 的 Win32 Internet 扩展 ](win32-internet-extensions-wininet.md)<br/>
[Internet 客户端类的先决条件](prerequisites-for-internet-client-classes.md)<br/>
[使用 MFC WinInet 类编写 Internet 客户端应用程序](writing-an-internet-client-application-using-mfc-wininet-classes.md)

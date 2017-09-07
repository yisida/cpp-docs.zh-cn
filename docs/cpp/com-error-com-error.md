---
title: "_com_error::_com_error | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_error._com_error"
  - "_com_error::_com_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_com_error 方法"
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _com_error::_com_error
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 构造 `_com_error` 对象。  
  
## 语法  
  
```  
  
      _com_error(  
   HRESULT hr,  
   IErrorInfo* perrinfo = NULL,  
   bool fAddRef=false  
) throw( );  
_com_error(  
   const _com_error& that   
) throw( );  
```  
  
#### 参数  
 `hr`  
 `HRESULT` 信息。  
  
 `perrinfo`  
 **IErrorInfo** 对象。  
  
 **bool fAddRef\=false**  
 导致构造函数在非 null **IErrorInfo** 接口上调用 AddRef。  这可以在接口的所有权传入 `_com_error` 对象的常见情况下提供正确的引用计数，例如：  
  
```  
throw _com_error(hr, perrinfo);  
```  
  
 如果您不想让代码将所有权转交到 `_com_error` 对象，并且在 `_com_error` 析构函数中对 **Release** 进行偏移需要 `AddRef`，则按以下方式构造对象：  
  
```  
_com_error err(hr, perrinfo, true);  
```  
  
 `that`  
 一个现有的 `_com_error` 对象。  
  
## 备注  
 第一个构造函数基于 `HRESULT` 和可选的 **IErrorInfo** 对象创建一个新对象。  第二个构造函数创建现有 `_com_error` 对象的副本。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_com\_error 类](../cpp/com-error-class.md)
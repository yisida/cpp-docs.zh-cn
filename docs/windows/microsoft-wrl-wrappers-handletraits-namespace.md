---
title: "Microsoft::WRL::Wrappers::HandleTraits 命名空间 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "HandleTraits 命名空间"
ms.assetid: 2fb5c6d1-bfc2-4e09-91eb-31705064ffb3
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Microsoft::WRL::Wrappers::HandleTraits 命名空间
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述常见的基于句柄的资源类型的特征。  
  
## <a name="syntax"></a>语法  
  
```  
namespace Microsoft::WRL::Wrappers::HandleTraits;  
```  
  
## <a name="members"></a>成员  
  
### <a name="structures"></a>结构  
  
|名称|描述|  
|----------|-----------------|  
|[CriticalSectionTraits 结构](../windows/criticalsectiontraits-structure.md)|专用化 `CriticalSection` 对象以支持无效的临界区或发布临界区的功能。|  
|[EventTraits 结构](../windows/eventtraits-structure.md)|定义特征 `Event` 类句柄。|  
|[FileHandleTraits 结构](../windows/filehandletraits-structure.md)|定义的文件句柄的特征。|  
|[HANDLENullTraits 结构](../windows/handlenulltraits-structure.md)|定义一个未初始化的句柄的共同特征。|  
|[HANDLETraits 结构](../windows/handletraits-structure.md)|定义句柄的共同特征。|  
|[MutexTraits 结构](../windows/mutextraits-structure.md)|定义的共性 [互斥体](../windows/mutex-class1.md) 类。|  
|[SemaphoreTraits 结构](../windows/semaphoretraits-structure.md)|定义信号量对象的共同特征。|  
|[SRWLockExclusiveTraits 结构](../windows/srwlockexclusivetraits-structure.md)|描述的共性 `SRWLock` 中排他锁模式的类。|  
|[SRWLockSharedTraits 结构](../windows/srwlocksharedtraits-structure.md)|描述的共性 `SRWLock` 中共享锁模式的类。|  
  
## <a name="requirements"></a>要求  
 **标头︰** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另请参阅  
 [Microsoft::WRL::Wrappers Namespace](../windows/microsoft-wrl-wrappers-namespace.md)
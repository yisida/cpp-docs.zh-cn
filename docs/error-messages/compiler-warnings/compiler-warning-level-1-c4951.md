---
description: 了解详细信息：编译器警告 (等级 1) C4951
title: 编译器警告（等级 1）C4951
ms.date: 08/27/2018
f1_keywords:
- C4951
helpviewer_keywords:
- C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
ms.openlocfilehash: effb1f5af0c406de002b5c0b8522e7c58a2424a5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327964"
---
# <a name="compiler-warning-level-1-c4951"></a>编译器警告（等级 1）C4951

> 自收集配置文件数据后已编辑过 "*函数*"，未使用函数配置文件数据

在输入模块中已将函数编辑为 [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)，因此配置文件数据现在无效。 在 **/ltcg: pginstrument** 后已重新编译输入模块并且有一个函数（*函数*），使用的控制流不是在执行 **/ltcg: pginstrument** 操作时模块中的控制流。

此警告为信息性。 若要解决此警告，请运行 **/LTCG:PGINSTRUMENT**，重做所有测试，并运行 **/LTCG:PGOPTIMIZE**。

如果已使用 **/LTCG:PGOPTIMIZE** ，此警告将替换为一个错误。

---
description: '详细了解：事务：在记录集中执行事务 (ODBC) '
title: 事务：在记录集中执行事务 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
ms.openlocfilehash: bb041d35e7ab0bfc7e19f2658a8cdadae4bd8c7e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333888"
---
# <a name="transaction-performing-a-transaction-in-a-recordset-odbc"></a>事务：在记录集中执行事务 (ODBC)

本主题说明如何在记录集中执行事务。

> [!NOTE]
> 只支持一个级别的事务;不能嵌套事务。

#### <a name="to-perform-a-transaction-in-a-recordset"></a>在记录集中执行事务

1. 调用 `CDatabase` 对象的 `BeginTrans` 成员函数。

1. 如果尚未实现批量提取行，请根据需要调用 `AddNew/Update` `Edit/Update` `Delete` 同一数据库的一个或多个记录集对象的、和成员函数。 有关详细信息，请参阅 [记录集： (ODBC) 添加、更新和删除记录 ](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)。 如果已实现批量行提取，则必须编写自己的函数以更新数据源。

1. 最后，调用 `CDatabase` 对象的 `CommitTrans` 成员函数。 如果某个更新中出现错误，或者您决定取消这些更改，请调用其 `Rollback` 成员函数。

下面的示例使用两个记录集从学校注册数据库中删除学生的注册，并从注册了学生的所有类中删除了该学生。 由于 `Delete` 两个记录集中的调用都必须成功，因此需要事务。 该示例假设存在 `m_dbStudentReg` 、类型的成员变量 `CDatabase` 已连接到数据源以及记录集类 `CEnrollmentSet` 和 `CStudentSet` 。 `strStudentID`变量包含从用户获取的值。

```
BOOL CEnrollDoc::RemoveStudent( CString strStudentID )
{
    // remove student from all the classes
    // the student is enrolled in

    if ( !m_dbStudentReg.BeginTrans( ) )
        return FALSE;

    CEnrollmentSet rsEnrollmentSet(&m_dbStudentReg);
    rsEnrollmentSet.m_strFilter = "StudentID = " + strStudentID;

    if ( !rsEnrollmentSet.Open(CRecordset::dynaset) )
        return FALSE;

    CStudentSet rsStudentSet(&m_dbStudentReg);
    rsStudentSet.m_strFilter = "StudentID = " + strStudentID;

    if ( !rsStudentSet.Open(CRecordset::dynaset) )
        return FALSE;

    TRY
    {
        while ( !rsEnrollmentSet.IsEOF( ) )
        {
            rsEnrollmentSet.Delete( );
            rsEnrollmentSet.MoveNext( );
        }

        // delete the student record
        rsStudentSet.Delete( );

        m_dbStudentReg.CommitTrans( );
    }

    CATCH_ALL(e)
    {
        m_dbStudentReg.Rollback( );
        return FALSE;
    }
    END_CATCH_ALL

    rsEnrollmentSet.Close( );
    rsStudentSet.Close( );

    return TRUE;

}
```

> [!NOTE]
> `BeginTrans`再次调用而不调用 `CommitTrans` 或 `Rollback` 为错误。

## <a name="see-also"></a>请参阅

[事务 (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[事务：事务如何影响 ODBC (更新) ](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)<br/>
[CDatabase 类](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)

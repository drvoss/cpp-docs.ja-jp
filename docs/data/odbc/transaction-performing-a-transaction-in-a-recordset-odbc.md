---
title: 'トランザクション: レコードセットからのトランザクション実行 (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
ms.openlocfilehash: df7c28ebfbb68f3e0163368247b90ff69058726d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50659590"
---
# <a name="transaction-performing-a-transaction-in-a-recordset-odbc"></a>トランザクション: レコードセットからのトランザクション実行 (ODBC)

このトピックでは、レコード セットのトランザクションを実行する方法について説明します。

> [!NOTE]
>  トランザクションの 1 つだけのレベルがサポートされています。トランザクションを入れ子にすることはできません。

#### <a name="to-perform-a-transaction-in-a-recordset"></a>レコード セットのトランザクションを実行するには

1. 呼び出す、`CDatabase`オブジェクトの`BeginTrans`メンバー関数。

1. バルク行フェッチを実装しない場合、 `AddNew/Update`、 `Edit/Update`、および`Delete`必要な回数と同じデータベースの 1 つまたは複数のレコード セット オブジェクトのメンバー関数。 詳細については、次を参照してください。[レコード セット: 追加、更新、およびレコードの削除 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)します。 バルク行フェッチを実装している場合は、データ ソースを更新する、独自の関数を記述する必要があります。

1. 最後に、呼び出し、`CDatabase`オブジェクトの`CommitTrans`メンバー関数。 呼び出す場合、更新プログラムのいずれかでエラーが発生したまたは変更をキャンセルする場合、その`Rollback`メンバー関数。

次の例では、2 つのレコード セットを使用して、生徒が登録されているすべてのクラスから受講者を削除する、学校の登録情報データベースから学生の登録を削除します。 `Delete`両方のレコード セットでの呼び出しが成功する必要があります、トランザクションが必要です。 例では、ことを想定の`m_dbStudentReg`、型のメンバー変数`CDatabase`、データ ソースとレコード セット クラスに既に接続されている`CEnrollmentSet`と`CStudentSet`します。 `strStudentID`変数には、ユーザーから取得した値が含まれています。

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
>  呼び出す`BeginTrans`呼び出さずにもう一度`CommitTrans`または`Rollback`エラーが発生します。

## <a name="see-also"></a>関連項目

[トランザクション (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[トランザクション: トランザクションが更新処理に与える影響 (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)<br/>
[CDatabase クラス](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset クラス](../../mfc/reference/crecordset-class.md)
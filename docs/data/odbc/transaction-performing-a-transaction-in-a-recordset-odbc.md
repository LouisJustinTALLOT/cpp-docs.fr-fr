---
description: 'En savoir plus sur : transaction : exécution d’une transaction dans un Recordset (ODBC)'
title: "Transaction : exécution d'une transaction dans un recordset (ODBC)"
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
ms.openlocfilehash: bb041d35e7ab0bfc7e19f2658a8cdadae4bd8c7e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333880"
---
# <a name="transaction-performing-a-transaction-in-a-recordset-odbc"></a>Transaction : exécution d'une transaction dans un recordset (ODBC)

Cette rubrique explique comment effectuer une transaction dans un Recordset.

> [!NOTE]
> Un seul niveau de transactions est pris en charge ; vous ne pouvez pas imbriquer des transactions.

#### <a name="to-perform-a-transaction-in-a-recordset"></a>Pour exécuter une transaction dans un Recordset

1. Appelez la `CDatabase` fonction membre de l’objet `BeginTrans` .

1. Si vous n’avez pas implémenté l’extraction de lignes en bloc, appelez les `AddNew/Update` `Edit/Update` `Delete` fonctions membres, et d’un ou plusieurs objets Recordset de la même base de données autant de fois que nécessaire. Pour plus d’informations, consultez [Recordset : ajout, mise à jour et suppression d’enregistrements (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md). Si vous avez implémenté l’extraction de lignes en bloc, vous devez écrire vos propres fonctions pour mettre à jour la source de données.

1. Enfin, appelez la `CDatabase` fonction membre de l’objet `CommitTrans` . Si une erreur se produit dans l’une des mises à jour ou si vous décidez d’annuler les modifications, appelez la `Rollback` fonction membre.

L’exemple suivant utilise deux recordsets pour supprimer l’inscription d’un étudiant d’une base de données d’inscription scolaire, en supprimant l’étudiant de toutes les classes dans lesquelles l’étudiant est inscrit. Étant donné que les `Delete` appels dans les deux jeux d’enregistrements doivent s’effectuer correctement, une transaction est requise. L’exemple suppose l’existence de `m_dbStudentReg` , une variable membre de type `CDatabase` déjà connectée à la source de données, et les classes de recordset `CEnrollmentSet` et `CStudentSet` . La `strStudentID` variable contient une valeur obtenue de l’utilisateur.

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
> `BeginTrans`L’appel de nouveau sans appeler `CommitTrans` ou `Rollback` est une erreur.

## <a name="see-also"></a>Voir aussi

[Transaction (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[Transaction : répercussions des transactions sur les mises à jour (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)<br/>
[CDatabase, classe](../../mfc/reference/cdatabase-class.md)<br/>
[Classe CRecordset](../../mfc/reference/crecordset-class.md)

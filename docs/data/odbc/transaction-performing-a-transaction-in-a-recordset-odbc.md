---
title: "Transaction : exécution d'une transaction dans un recordset (ODBC)"
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
ms.openlocfilehash: 45ae414c318376b2c4d787498e9a288a0037af83
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358094"
---
# <a name="transaction-performing-a-transaction-in-a-recordset-odbc"></a>Transaction : exécution d'une transaction dans un recordset (ODBC)

Ce sujet explique comment effectuer une transaction dans un ensemble d’enregistrements.

> [!NOTE]
> Un seul niveau de transactions est pris en charge; vous ne pouvez pas nicher les transactions.

#### <a name="to-perform-a-transaction-in-a-recordset"></a>Effectuer une transaction dans un ensemble d’enregistrements

1. Appelez `CDatabase` la fonction `BeginTrans` de membre de l’objet.

1. Si vous n’avez pas implémenté la ligne en vrac, appelez les `AddNew/Update`fonctions , `Edit/Update`et `Delete` les membres d’un ou plusieurs objets de l’enregistrement de la même base de données autant de fois que nécessaire. Pour plus d’informations, voir [Recordset: Adding, Updating, and Deleting Records (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md). Si vous avez implémenté la ligne en vrac, vous devez écrire vos propres fonctions pour mettre à jour la source de données.

1. Enfin, appelez `CDatabase` la `CommitTrans` fonction de membre de l’objet. Si une erreur se produit dans l’une des mises `Rollback` à jour ou si vous décidez d’annuler les modifications, appelez sa fonction de membre.

L’exemple suivant utilise deux ensembles d’enregistrements pour supprimer l’inscription d’un élève dans une base de données d’inscription scolaire, en retirant l’élève de toutes les classes dans lesquelles l’élève est inscrit. Étant `Delete` donné que les appels dans les deux ensembles d’enregistrements doivent réussir, une transaction est nécessaire. L’exemple suppose l’existence `m_dbStudentReg`de , `CDatabase` une variable de membre de type `CEnrollmentSet` `CStudentSet`déjà connecté à la source de données, et les classes de documents et . La `strStudentID` variable contient une valeur obtenue de l’utilisateur.

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
> Appeler `BeginTrans` à `CommitTrans` nouveau `Rollback` sans appeler ou est une erreur.

## <a name="see-also"></a>Voir aussi

[Transaction (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[Transaction : répercussions des transactions sur les mises à jour (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)<br/>
[Classe CDatabase](../../mfc/reference/cdatabase-class.md)<br/>
[Classe CRecordset](../../mfc/reference/crecordset-class.md)

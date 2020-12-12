---
description: 'En savoir plus sur : Recordset : ajout, mise à jour et suppression d’enregistrements (ODBC)'
title: "Recordset : ajout, modification et suppression d'enregistrements (ODBC)"
ms.date: 11/04/2016
helpviewer_keywords:
- records [C++], updating
- record editing [C++], in recordsets
- recordsets [C++], adding records
- records [C++], adding
- ODBC recordsets [C++], adding records
- recordsets [C++], editing records
- recordsets [C++], updating
- records [C++], deleting
- AddNew method
- ODBC recordsets [C++], deleting records
- data in recordsets [C++]
- record editing [C++]
- recordsets [C++], deleting records
- ODBC recordsets [C++], editing records
- records [C++], editing
ms.assetid: 760c8889-bec4-482b-a8f2-319792a6af98
ms.openlocfilehash: 20af392182481cc786d65567b4db1547d703ba0e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186140"
---
# <a name="recordset-adding-updating-and-deleting-records-odbc"></a>Recordset : ajout, modification et suppression d'enregistrements (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

> [!NOTE]
> Vous pouvez maintenant ajouter des enregistrements de manière plus efficace en masse. Pour plus d’informations, consultez [Recordset : ajout d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-adding-records-in-bulk-odbc.md).

> [!NOTE]
> Cette rubrique s’applique aux objets dérivés de `CRecordset` où l’extraction de lignes en bloc n’a pas été implémentée. Si vous utilisez l’extraction de lignes en bloc, consultez [Recordset : extraction globale d’enregistrements (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Les instantanés et les feuilles de réponse dynamiques modifiables vous permettent d’ajouter, de modifier (mettre à jour) et de supprimer des enregistrements. Cette rubrique répond aux questions suivantes :

- [Comment déterminer si votre Recordset peut être mis à jour](#_core_determining_whether_your_recordset_is_updatable).

- [Comment ajouter un nouvel enregistrement](#_core_adding_a_record_to_a_recordset).

- [Comment modifier un enregistrement existant](#_core_editing_a_record_in_a_recordset).

- [Comment supprimer un enregistrement](#_core_deleting_a_record_from_a_recordset).

Pour plus d’informations sur la façon dont les mises à jour sont effectuées et sur la façon dont vos mises à jour apparaissent aux autres utilisateurs, consultez [Recordset : comment les recordsets mettent à jour les enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md). En règle générale, lorsque vous ajoutez, modifiez ou supprimez un enregistrement, le Recordset modifie immédiatement la source de données. Au lieu de cela, vous pouvez regrouper par lots les mises à jour associées dans des transactions. Si une transaction est en cours, la mise à jour ne devient définitive qu’une fois la transaction validée. Cela vous permet de reprendre ou d’annuler les modifications. Pour plus d’informations sur les transactions, consultez [transaction (ODBC)](../../data/odbc/transaction-odbc.md).

Le tableau suivant récapitule les options disponibles pour les jeux d’enregistrements avec différentes caractéristiques de mise à jour.

### <a name="recordset-readupdate-options"></a>Options de lecture/mise à jour du Recordset

|Type|Lire|Modifier un enregistrement|Supprimer un enregistrement|Ajouter nouveau (ajouter)|
|----------|----------|-----------------|-------------------|------------------------|
|Lecture seule|O|N|N|N|
|Ajout uniquement|O|N|N|O|
|Entièrement modifiable|O|O|O|O|

## <a name="determining-whether-your-recordset-is-updateable"></a><a name="_core_determining_whether_your_recordset_is_updatable"></a> Détermination de la possibilité de mise à jour de votre Recordset

Un objet Recordset peut être mis à jour si la source de données est modifiable et que vous avez ouvert le Recordset comme étant modifiable. Sa mise à jour dépend également de l’instruction SQL que vous utilisez, des fonctionnalités de votre pilote ODBC et de l’utilisation ou non de la bibliothèque de curseurs ODBC dans la mémoire. Vous ne pouvez pas mettre à jour un jeu d’enregistrements ou une source de données en lecture seule.

#### <a name="to-determine-whether-your-recordset-is-updatable"></a>Pour déterminer si votre Recordset peut être mis à jour

1. Appelez la fonction membre [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) de l’objet Recordset.

   `CanUpdate` retourne une valeur différente de zéro si le jeu d’enregistrements peut être mis à jour.

Par défaut, les recordsets sont entièrement modifiables (vous pouvez effectuer des `AddNew` opérations, `Edit` et `Delete` ). Toutefois, vous pouvez également utiliser l’option [AppendOnly](../../mfc/reference/crecordset-class.md#open) pour ouvrir des recordsets pouvant être mis à jour. Un jeu d’enregistrements ouvert de cette façon n’autorise que l’ajout de nouveaux enregistrements avec `AddNew` . Vous ne pouvez pas modifier ou supprimer des enregistrements existants. Vous pouvez tester si un jeu d’enregistrements est ouvert uniquement pour l’ajout en appelant la fonction membre [CanAppend](../../mfc/reference/crecordset-class.md#canappend) . `CanAppend` retourne une valeur différente de zéro si le jeu d’enregistrements est entièrement modifiable ou ouvert uniquement pour l’ajout.

Le code suivant montre comment vous pouvez utiliser `CanUpdate` pour un objet Recordset appelé `rsStudentSet` :

```cpp
if( !rsStudentSet.Open( ) )
    return FALSE;
if( !rsStudentSet.CanUpdate( ) )
{
    AfxMessageBox( "Unable to update the Student recordset." );
    return;
}
```

> [!CAUTION]
> Lorsque vous vous préparez à mettre à jour un jeu d’enregistrements en appelant, assurez-vous `Update` que votre Recordset comprend toutes les colonnes qui composent la clé primaire de la table (ou toutes les colonnes d’un index unique sur la table). Dans certains cas, l’infrastructure peut utiliser uniquement les colonnes sélectionnées dans votre jeu d’enregistrements pour identifier l’enregistrement à mettre à jour dans votre table. Si vous ne disposez pas de toutes les colonnes nécessaires, plusieurs enregistrements peuvent être mis à jour dans la table, ce qui peut endommager l’intégrité référentielle de la table. Dans ce cas, l’infrastructure lève des exceptions lorsque vous appelez `Update` .

## <a name="adding-a-record-to-a-recordset"></a><a name="_core_adding_a_record_to_a_recordset"></a> Ajout d’un enregistrement à un jeu d’enregistrements

Vous pouvez ajouter de nouveaux enregistrements à un Recordset si sa fonction membre [CanAppend](../../mfc/reference/crecordset-class.md#canappend) retourne une valeur différente de zéro.

#### <a name="to-add-a-new-record-to-a-recordset"></a>Pour ajouter un nouvel enregistrement à un Recordset

1. Assurez-vous que le jeu d’enregistrements peut être ajouté.

1. Appelez la fonction membre [AddNew](../../mfc/reference/crecordset-class.md#addnew) de l’objet Recordset.

   `AddNew` prépare le Recordset pour qu’il agisse comme un tampon d’édition. Tous les membres de données de champ sont définis sur la valeur spéciale null et marqués comme inchangés, de sorte que seules les valeurs modifiées (modifiées) sont écrites dans la source de données lorsque vous appelez [Update](../../mfc/reference/crecordset-class.md#update).

1. Définissez les valeurs des membres de données de champ du nouvel enregistrement.

   Assignez des valeurs aux membres de données de champ. Ceux que vous n’assignez pas ne sont pas écrits dans la source de données.

1. Appelez la fonction membre de l’objet Recordset `Update` .

   `Update` termine l’ajout en écrivant le nouvel enregistrement dans la source de données. Pour plus d’informations sur les événements qui se produisent si vous ne parvenez pas à appeler `Update` , consultez [Recordset : comment les recordsets mettent à jour les enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

Pour plus d’informations sur le fonctionnement de l’ajout d’enregistrements et sur la façon dont les enregistrements ajoutés sont visibles dans votre Recordset, consultez [Recordset : fonctionnement des opérations AddNew, Edit et Delete (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md).

L’exemple suivant montre comment ajouter un nouvel enregistrement :

```cpp
if( !rsStudent.Open( ) )
    return FALSE;
if( !rsStudent.CanAppend( ) )
    return FALSE;                      // no field values were set
rsStudent.AddNew( );
rsStudent.m_strName = strName;
rsStudent.m_strCity = strCity;
rsStudent.m_strStreet = strStreet;
if( !rsStudent.Update( ) )
{
    AfxMessageBox( "Record not added; no field values were set." );
    return FALSE;
}
```

> [!TIP]
> Pour annuler un `AddNew` `Edit` appel ou, effectuez simplement un autre appel à `AddNew` ou, `Edit` ou appelez `Move` avec le paramètre *AFX_MOVE_REFRESH* . Les membres de données sont réinitialisés à leurs valeurs précédentes et vous êtes toujours en `Edit` `Add` mode ou.

## <a name="editing-a-record-in-a-recordset"></a><a name="_core_editing_a_record_in_a_recordset"></a> Modification d’un enregistrement dans un Recordset

Vous pouvez modifier des enregistrements existants si la fonction membre [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) de votre Recordset retourne une valeur différente de zéro.

#### <a name="to-edit-an-existing-record-in-a-recordset"></a>Pour modifier un enregistrement existant dans un Recordset

1. Assurez-vous que le jeu d’enregistrements peut être mis à jour.

1. Faites défiler jusqu’à l’enregistrement que vous souhaitez mettre à jour.

1. Appelez la fonction membre [Edit](../../mfc/reference/crecordset-class.md#edit) de l’objet Recordset.

   `Edit` prépare le Recordset pour qu’il agisse comme un tampon d’édition. Tous les membres de données de champ sont marqués afin que le jeu d’enregistrements puisse indiquer ultérieurement s’ils ont été modifiés. Les nouvelles valeurs des membres de données de champ modifiés sont écrites dans la source de données lorsque vous appelez [Update](../../mfc/reference/crecordset-class.md#update).

1. Définissez les valeurs des membres de données de champ du nouvel enregistrement.

   Assignez des valeurs aux membres de données de champ. Ceux auxquels vous n’affectez pas de valeurs restent inchangés.

1. Appelez la fonction membre de l’objet Recordset `Update` .

   `Update` termine la modification en écrivant l’enregistrement modifié dans la source de données. Pour plus d’informations sur les événements qui se produisent si vous ne parvenez pas à appeler `Update` , consultez [Recordset : comment les recordsets mettent à jour les enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

Une fois que vous avez modifié un enregistrement, l’enregistrement modifié reste l’enregistrement en cours.

L’exemple suivant illustre une `Edit` opération. Il part du principe que l’utilisateur a été déplacé vers un enregistrement qu’il souhaite modifier.

```cpp
rsStudent.Edit( );
rsStudent.m_strStreet = strNewStreet;
rsStudent.m_strCity = strNewCity;
rsStudent.m_strState = strNewState;
rsStudent.m_strPostalCode = strNewPostalCode;
if( !rsStudent.Update( ) )
{
    AfxMessageBox( "Record not updated; no field values were set." );
    return FALSE;
}
```

> [!TIP]
> Pour annuler un `AddNew` `Edit` appel ou, effectuez simplement un autre appel à `AddNew` ou, `Edit` ou appelez `Move` avec le paramètre *AFX_MOVE_REFRESH* . Les membres de données sont réinitialisés à leurs valeurs précédentes et vous êtes toujours en `Edit` `Add` mode ou.

## <a name="deleting-a-record-from-a-recordset"></a><a name="_core_deleting_a_record_from_a_recordset"></a> Suppression d’un enregistrement d’un jeu d’enregistrements

Vous pouvez supprimer des enregistrements si la fonction membre [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) de votre Recordset retourne une valeur différente de zéro.

#### <a name="to-delete-a-record"></a>Pour supprimer un enregistrement

1. Assurez-vous que le jeu d’enregistrements peut être mis à jour.

1. Faites défiler jusqu’à l’enregistrement que vous souhaitez mettre à jour.

1. Appelez la fonction membre [Delete](../../mfc/reference/crecordset-class.md#delete) de l’objet Recordset.

   `Delete` marque immédiatement l’enregistrement comme supprimé, à la fois dans le jeu d’enregistrements et sur la source de données.

   Contrairement à `AddNew` et `Edit` , n' `Delete` a aucun `Update` appel correspondant.

1. Faites défiler jusqu’à un autre enregistrement.

   > [!NOTE]
   >  Lors du déplacement dans le jeu d’enregistrements, les enregistrements supprimés peuvent ne pas être ignorés. Pour plus d’informations, consultez la fonction membre [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted) .

L’exemple suivant illustre une `Delete` opération. Il part du principe que l’utilisateur a été déplacé vers un enregistrement que l’utilisateur souhaite supprimer. Une fois que `Delete` est appelé, il est important de passer à un nouvel enregistrement.

```
rsStudent.Delete( );
rsStudent.MoveNext( );
```

Pour plus d’informations sur les effets des `AddNew` `Edit` `Delete` fonctions membres, et, consultez [Recordset : comment les recordsets mettent à jour les enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : verrouillage d’enregistrements (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)

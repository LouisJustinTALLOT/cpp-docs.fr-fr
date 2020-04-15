---
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
ms.openlocfilehash: 628ffb2feee385a4114b0dbea074f81678c529d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367105"
---
# <a name="recordset-adding-updating-and-deleting-records-odbc"></a>Recordset : ajout, modification et suppression d'enregistrements (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

> [!NOTE]
> Vous pouvez maintenant ajouter des enregistrements en vrac plus efficacement. Pour plus d’informations, voir [Recordset: Adding Records in Bulk (ODBC)](../../data/odbc/recordset-adding-records-in-bulk-odbc.md).

> [!NOTE]
> Cette rubrique s’applique aux objets dérivés de `CRecordset` où l’extraction de lignes en bloc n’a pas été implémentée. Si vous utilisez la ligne en vrac aller chercher, voir [Recordset: Fetching Records en vrac (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Des instantanés et des colorants à jour vous permettent d’ajouter, modifier (mettre à jour) et supprimer des enregistrements. Cette rubrique répond aux questions suivantes :

- [Comment déterminer si votre dossier est updatable](#_core_determining_whether_your_recordset_is_updatable).

- [Comment ajouter un nouvel album](#_core_adding_a_record_to_a_recordset).

- [Comment modifier un enregistrement existant](#_core_editing_a_record_in_a_recordset).

- [Comment supprimer un enregistrement](#_core_deleting_a_record_from_a_recordset).

Pour plus d’informations sur la façon dont les mises à jour sont effectuées et comment vos mises à jour apparaissent à d’autres utilisateurs, voir [Recordset: How Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md). Normalement, lorsque vous ajoutez, modifiez ou supprimez un enregistrement, le nombre d’enregistrements modifie immédiatement la source de données. Vous pouvez plutôt regrouper des groupes de mises à jour connexes dans les transactions. Si une transaction est en cours, la mise à jour ne devient pas définitive tant que vous n’avez pas commis la transaction. Cela vous permet de reprendre ou de faire reculer les modifications. Pour plus d’informations sur les transactions, voir [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

Le tableau suivant résume les options disponibles pour les enregistrements présentant des caractéristiques de mise à jour différentes.

### <a name="recordset-readupdate-options"></a>Options de lecture/mise à jour De Recordset

|Type|Lire|Modifier un enregistrement|Supprimer un enregistrement|Ajouter de nouveaux (annexe)|
|----------|----------|-----------------|-------------------|------------------------|
|Lecture seule|O|N|N|N|
|Annexe seulement|O|N|N|O|
|Entièrement updatable|O|O|O|O|

## <a name="determining-whether-your-recordset-is-updateable"></a><a name="_core_determining_whether_your_recordset_is_updatable"></a>Déterminer si votre dossier est mis à jour

Un objet de la boîte de disques est mis à jour si la source de données est mise à jour et que vous avez ouvert le jeu d’enregistrement comme mise à jour. Sa mise à jour dépend également de l’énoncé SQL que vous utilisez, des capacités de votre chauffeur ODBC et de la mémoire de la bibliothèque ODBC Cursor. Vous ne pouvez pas mettre à jour un jeu d’enregistrement ou une source de données uniquement sur la lecture.

#### <a name="to-determine-whether-your-recordset-is-updatable"></a>Pour déterminer si votre dossier est updatable

1. Appelez la fonction de membre [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) de l’objet de l’enregistrement.

   `CanUpdate`retourne une valeur non zéro si le pack d’enregistrement est mis à jour.

Par défaut, les enregistrements sont entièrement `AddNew`mis `Edit`à `Delete` jour (vous pouvez effectuer, et les opérations). Mais vous pouvez également utiliser [l’option appendiceonnement](../../mfc/reference/crecordset-class.md#open) pour ouvrir des enregistrements à jour. Un recordet ouvert de cette façon ne `AddNew`permet que l’ajout de nouveaux enregistrements avec . Vous ne pouvez pas modifier ou supprimer les enregistrements existants. Vous pouvez tester si un enregistrement n’est ouvert que pour l’appending en appelant la fonction membre [CanAppend.](../../mfc/reference/crecordset-class.md#canappend) `CanAppend`retourne une valeur non zéro si le pack d’enregistrement est entièrement mis à jour ou ouvert uniquement pour l’appending.

Le code suivant montre `CanUpdate` comment vous pouvez `rsStudentSet`utiliser pour un objet de recordet appelé :

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
> Lorsque vous vous préparez à `Update`mettre à jour un ensemble d’enregistrements en appelant, veillez à ce que votre jeu d’enregistrement comprend toutes les colonnes constituant la clé principale de la table (ou toutes les colonnes de tout index unique sur la table). Dans certains cas, le cadre ne peut utiliser que les colonnes sélectionnées dans votre dossier pour identifier l’enregistrement dans votre table à mettre à jour. Sans toutes les colonnes nécessaires, plusieurs enregistrements peuvent être mis à jour dans le tableau, ce qui pourrait nuire à l’intégrité référentielle de la table. Dans ce cas, le cadre fait `Update`des exceptions lorsque vous appelez .

## <a name="adding-a-record-to-a-recordset"></a><a name="_core_adding_a_record_to_a_recordset"></a>Ajout d’un record à un Recordet

Vous pouvez ajouter de nouveaux enregistrements à un recordet si sa fonction de membre [CanAppend](../../mfc/reference/crecordset-class.md#canappend) renvoie une valeur non zéro.

#### <a name="to-add-a-new-record-to-a-recordset"></a>Pour ajouter un nouvel enregistrement à un record

1. Assurez-vous que l’enregistrement est appendice.

1. Appelez la fonction de membre [AddNew](../../mfc/reference/crecordset-class.md#addnew) de l’objet de l’enregistrement.

   `AddNew`prépare l’enregistrement à agir comme tampon de modification. Tous les membres de données sur le terrain sont réglés à la valeur spéciale Null et marqué comme inchangé de sorte que seules les valeurs modifiées (sales) sont écrites à la source de données lorsque vous appelez [mise à jour](../../mfc/reference/crecordset-class.md#update).

1. Définissez les valeurs des membres des données sur le terrain du nouvel enregistrement.

   Attribuer des valeurs aux membres des données sur le terrain. Ceux que vous n’attribuez pas ne sont pas écrits à la source de données.

1. Appelez la fonction de `Update` membre de l’objet de l’enregistrement.

   `Update`complète l’ajout en écrivant le nouvel enregistrement à la source de données. Pour plus d’informations sur `Update`les cas si vous omettez d’appeler , voir [Recordset: How Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

Pour plus d’informations sur le fonctionnement de l’ajout d’enregistrements et sur le moment où les enregistrements ajoutés sont visibles dans votre ensemble d’enregistrements, consultez [Recordset: How AddNew, Edit, and Delete Work (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md).

L’exemple suivant montre comment ajouter un nouvel enregistrement :

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
> Pour annuler `AddNew` `Edit` un ou appeler, `AddNew` il `Edit` suffit `Move` de passer un autre appel ou d’appeler avec le *paramètre AFX_MOVE_REFRESH.* Les membres de données sont réinitialisés à leurs valeurs précédentes et vous êtes toujours en `Edit` mode. `Add`

## <a name="editing-a-record-in-a-recordset"></a><a name="_core_editing_a_record_in_a_recordset"></a>Montage d’un record dans un Recordet

Vous pouvez modifier les enregistrements existants si la fonction de membre [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) de votre dossier renvoie une valeur non zéro.

#### <a name="to-edit-an-existing-record-in-a-recordset"></a>Modifier un enregistrement existant dans un dossier

1. Assurez-vous que le recordet est mis à jour.

1. Faites défiler vers l’enregistrement que vous souhaitez mettre à jour.

1. Appelez la fonction de membre [Edit](../../mfc/reference/crecordset-class.md#edit) de l’objet de l’enregistrement.

   `Edit`prépare l’enregistrement à agir comme tampon de modification. Tous les membres des données sur le terrain sont marqués afin que le dossier puisse savoir plus tard s’ils ont été modifiés. Les nouvelles valeurs pour les membres de données de terrain modifiées sont écrites à la source de données lorsque vous appelez [mise à jour](../../mfc/reference/crecordset-class.md#update).

1. Définissez les valeurs des membres des données sur le terrain du nouvel enregistrement.

   Attribuer des valeurs aux membres des données sur le terrain. Ceux que vous n’attribuez pas de valeurs restent inchangés.

1. Appelez la fonction de `Update` membre de l’objet de l’enregistrement.

   `Update`complète la modification en écrivant l’enregistrement modifié à la source de données. Pour plus d’informations sur `Update`les cas si vous omettez d’appeler , voir [Recordset: How Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

Après avoir modifié un enregistrement, l’enregistrement édité reste l’enregistrement actuel.

L’exemple suivant `Edit` montre une opération. Il suppose que l’utilisateur est passé à un enregistrement qu’il ou elle veut modifier.

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
> Pour annuler `AddNew` `Edit` un ou appeler, `AddNew` il `Edit` suffit `Move` de passer un autre appel ou d’appeler avec le *paramètre AFX_MOVE_REFRESH.* Les membres de données sont réinitialisés à leurs valeurs précédentes et vous êtes toujours en `Edit` mode. `Add`

## <a name="deleting-a-record-from-a-recordset"></a><a name="_core_deleting_a_record_from_a_recordset"></a>Suppression d’un record d’un Recordet

Vous pouvez supprimer des enregistrements si la fonction de membre [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) de votre dossier renvoie une valeur non zéro.

#### <a name="to-delete-a-record"></a>Supprimer un enregistrement

1. Assurez-vous que le recordet est mis à jour.

1. Faites défiler vers l’enregistrement que vous souhaitez mettre à jour.

1. Appelez la fonction de membre [Supprimer](../../mfc/reference/crecordset-class.md#delete) de l’objet de l’enregistrement.

   `Delete`indique immédiatement l’enregistrement tel qu’il est supprimé, tant dans l’enregistrement que sur la source de données.

   Contrairement `AddNew` `Edit`et `Delete` , `Update` n’a pas d’appel correspondant.

1. Faites défiler vers un autre enregistrement.

   > [!NOTE]
   >  Lorsque vous passez par le dossier, les enregistrements supprimés peuvent ne pas être ignorés. Pour plus d’informations, consultez la fonction membre [IsDeleted.](../../mfc/reference/crecordset-class.md#isdeleted)

L’exemple suivant `Delete` montre une opération. Il suppose que l’utilisateur est passé à un enregistrement que l’utilisateur veut supprimer. Après `Delete` est appelé, il est important de passer à un nouvel enregistrement.

```
rsStudent.Delete( );
rsStudent.MoveNext( );
```

Pour plus d’informations `AddNew`sur `Edit`les `Delete` effets de la , , et les fonctions des membres, voir [Recordset: How Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : verrouillage d'enregistrements (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)

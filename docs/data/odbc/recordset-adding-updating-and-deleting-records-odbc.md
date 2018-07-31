---
title: 'Recordset : Ajout, la mise à jour et suppression d’enregistrements (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5a8844da684d8afa3fe4dd13d8323d2bb3138d6c
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337997"
---
# <a name="recordset-adding-updating-and-deleting-records-odbc"></a>Recordset : ajout, modification et suppression d'enregistrements (ODBC)
Cette rubrique s’applique aux classes ODBC MFC.  
  
> [!NOTE]
>  Vous pouvez maintenant ajouter des enregistrements en bloc plus efficacement. Pour plus d’informations, consultez [Recordset : ajout global d’enregistrements (ODBC)](../../data/odbc/recordset-adding-records-in-bulk-odbc.md).  
  
> [!NOTE]
>  Cette rubrique s’applique aux objets dérivés de `CRecordset` dans les lignes en bloc l’extraction n’a pas été implémentée. Si vous utilisez l’extraction de lignes en bloc, consultez [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Les instantanés et les feuilles de réponse dynamiques permettent d’ajouter, modifier (update) et supprimer des enregistrements. Cette rubrique explique :  
  
-   [Comment déterminer si votre jeu d’enregistrements est modifiable](#_core_determining_whether_your_recordset_is_updatable).  
  
-   [Comment ajouter un nouvel enregistrement](#_core_adding_a_record_to_a_recordset).  
  
-   [Comment modifier un enregistrement existant](#_core_editing_a_record_in_a_recordset).  
  
-   [Comment supprimer un enregistrement](#_core_deleting_a_record_from_a_recordset).  
  
 Pour plus d’informations sur la façon dont les mises à jour sont effectuées et sur la façon dont vos mises à jour apparaissent à d’autres utilisateurs, consultez [Recordset : mise à jour des enregistrements par les Recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md). Normalement, lorsque vous ajoutez, modifiez ou supprimez un enregistrement, le jeu d’enregistrements change immédiatement la source de données. À la place de commandes mises à jour associées dans des transactions. Si une transaction est en cours d’exécution, la mise à jour ne devient-elle pas finale jusqu'à ce que vous validez la transaction. Cela vous permet de reprendre ou d’annuler les modifications. Pour plus d’informations sur les transactions, consultez [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).  
  
 Le tableau suivant récapitule les options disponibles pour les jeux d’enregistrements avec les caractéristiques de mise à jour différents.  
  
### <a name="recordset-readupdate-options"></a>Options de lecture/mise à jour de jeu d’enregistrements  
  
|Type|Lecture|Modifier l’enregistrement|Supprimer l’enregistrement|Ajouter un nouveau (ajouté)|  
|----------|----------|-----------------|-------------------|------------------------|  
|Propriétés en lecture seule|Y|N|N|N|  
|En mode Append-only|Y|N|N|Y|  
|Entièrement actualisable|Y|Y|Y|Y|  
  
##  <a name="_core_determining_whether_your_recordset_is_updatable"></a> Déterminer si votre jeu d’enregistrements est modifiable  
 Un objet recordset est modifiable si la source de données est modifiable et que vous avez ouvert le jeu d’enregistrements comme étant modifiable. Sa mise à jour dépend également de l’instruction SQL que vous utilisez, les fonctionnalités de votre pilote ODBC, et si la bibliothèque de curseurs ODBC est en mémoire. Vous ne pouvez pas mettre à jour une source de données ou le jeu d’enregistrements en lecture seule.  
  
#### <a name="to-determine-whether-your-recordset-is-updatable"></a>Pour déterminer si votre jeu d’enregistrements est modifiable  
  
1.  Appeler l’objet recordset [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) fonction membre.  
  
     `CanUpdate` Retourne une valeur différente de zéro si le recordset est modifiable.  
  
 Par défaut, les jeux d’enregistrements est entièrement modifiables (vous pouvez effectuer `AddNew`, `Edit`, et `Delete` operations). Mais vous pouvez également utiliser le [appendOnly](../../mfc/reference/crecordset-class.md#open) option pour ouvrir des recordsets modifiables. Un jeu d’enregistrements ouvert de cette façon permet uniquement l’ajout de nouveaux enregistrements avec `AddNew`. Vous ne pouvez pas modifier ou supprimer des enregistrements existants. Vous pouvez tester si un jeu d’enregistrements est ouvert uniquement pour l’ajout en appelant le [CanAppend](../../mfc/reference/crecordset-class.md#canappend) fonction membre. `CanAppend` Retourne une valeur différente de zéro si le recordset est modifiable ou ouvert uniquement pour l’ajout.  
  
 Le code suivant montre comment vous pouvez utiliser `CanUpdate` pour un objet recordset appelé `rsStudentSet`:  
  
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
>  Lorsque vous vous préparez à mettre à jour un jeu d’enregistrements en appelant `Update`, prenez soin que le jeu d’enregistrements comporte toutes les colonnes qui constituent la clé primaire de la table (ou toutes les colonnes d’un index unique sur la table). Dans certains cas, le framework peut utiliser uniquement les colonnes sélectionnées dans votre jeu d’enregistrements pour identifier l’enregistrement de la table à mettre à jour. Sans toutes les colonnes nécessaires, plusieurs enregistrements peuvent être mis à jour dans la table, éventuellement endommager l’intégrité référentielle de la table. Dans ce cas, le framework lève des exceptions lorsque vous appelez `Update`.  
  
##  <a name="_core_adding_a_record_to_a_recordset"></a> Ajout d’un enregistrement à un jeu d’enregistrements  
 Vous pouvez ajouter de nouveaux enregistrements à un jeu d’enregistrements si son [CanAppend](../../mfc/reference/crecordset-class.md#canappend) fonction membre retourne une valeur différente de zéro.  
  
#### <a name="to-add-a-new-record-to-a-recordset"></a>Pour ajouter un nouvel enregistrement à un jeu d’enregistrements  
  
1.  Assurez-vous que le jeu d’enregistrements est modifiable.  
  
2.  Appeler l’objet recordset [AddNew](../../mfc/reference/crecordset-class.md#addnew) fonction membre.  
  
     `AddNew` prépare le jeu d’enregistrements à agir en tant que tampon d’édition. Tous les membres de données de champ sont définies avec la valeur spéciale Null et marquées comme inchangées donc uniquement modifiées (modifié) valeurs sont écrites dans la source de données lorsque vous appelez [mise à jour](../../mfc/reference/crecordset-class.md#update).  
  
3.  Définissez les valeurs des membres de données de champ du nouvel enregistrement.  
  
     Affecter des valeurs aux données membres de champ. Ceux que vous n’affectez pas ne sont pas écrites dans la source de données.  
  
4.  Appeler l’objet recordset `Update` fonction membre.  
  
     `Update` termine l’ajout en écrivant le nouvel enregistrement dans la source de données. Pour plus d’informations sur se produit si vous n’appelez pas `Update`, consultez [Recordset : mise à jour des enregistrements par les Recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
 Pour plus d’informations sur le fonctionnement de l’ajout d’enregistrements et lorsque les enregistrements ajoutés sont visibles dans le jeu d’enregistrements, consultez [Recordset : fonctionnement d’AddNew, Edit et Delete (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md).  
  
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
>  Pour annuler un `AddNew` ou `Edit` appeler, simplement effectuer un autre appel à `AddNew` ou `Edit` ou appelez `Move` avec la *AFX_MOVE_REFRESH* paramètre. Les membres de données sont réinitialisés à leurs valeurs précédentes et vous êtes toujours dans `Edit` ou `Add` mode.  
  
##  <a name="_core_editing_a_record_in_a_recordset"></a> Modification d’un enregistrement dans un jeu d’enregistrements  
 Vous pouvez modifier les enregistrements existants si votre jeu d’enregistrements [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) fonction membre retourne une valeur différente de zéro.  
  
#### <a name="to-edit-an-existing-record-in-a-recordset"></a>Pour modifier un enregistrement existant dans un jeu d’enregistrements  
  
1.  Assurez-vous que le jeu d’enregistrements est modifiable.  
  
2.  Faites défiler jusqu'à l’enregistrement que vous souhaitez mettre à jour.  
  
3.  Appeler l’objet recordset [modifier](../../mfc/reference/crecordset-class.md#edit) fonction membre.  
  
     `Edit` prépare le jeu d’enregistrements à agir en tant que tampon d’édition. Tous les membres de données de champ sont marqués de sorte que le jeu d’enregistrements peut savoir ultérieurement s’ils ont été modifiés. Les nouvelles valeurs des membres de données de champ modifiés sont écrits dans la source de données lorsque vous appelez [mise à jour](../../mfc/reference/crecordset-class.md#update).  
  
4.  Définissez les valeurs des membres de données de champ du nouvel enregistrement.  
  
     Affecter des valeurs aux données membres de champ. Ceux que vous n’affectez pas de valeurs restent inchangés.  
  
5.  Appeler l’objet recordset `Update` fonction membre.  
  
     `Update` termine la modification en écrivant l’enregistrement modifié dans la source de données. Pour plus d’informations sur se produit si vous n’appelez pas `Update`, consultez [Recordset : mise à jour des enregistrements par les Recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
 Une fois que vous modifiez un enregistrement, celui-ci demeure l’enregistrement actif.  
  
 L’exemple suivant montre une `Edit` opération. Il suppose que l’utilisateur a été déplacé vers un enregistrement qu'il souhaite modifier.  
  
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
>  Pour annuler un `AddNew` ou `Edit` appeler, simplement effectuer un autre appel à `AddNew` ou `Edit` ou appelez `Move` avec la *AFX_MOVE_REFRESH* paramètre. Les membres de données sont réinitialisés à leurs valeurs précédentes et vous êtes toujours dans `Edit` ou `Add` mode.  
  
##  <a name="_core_deleting_a_record_from_a_recordset"></a> Suppression d’un enregistrement à partir d’un jeu d’enregistrements  
 Vous pouvez supprimer des enregistrements si votre jeu d’enregistrements [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) fonction membre retourne une valeur différente de zéro.  
  
#### <a name="to-delete-a-record"></a>Pour supprimer un enregistrement  
  
1.  Assurez-vous que le jeu d’enregistrements est modifiable.  
  
2.  Faites défiler jusqu'à l’enregistrement que vous souhaitez mettre à jour.  
  
3.  Appeler l’objet recordset [supprimer](../../mfc/reference/crecordset-class.md#delete) fonction membre.  
  
     `Delete` le marque immédiatement l’enregistrement comme supprimé, à la fois dans le jeu d’enregistrements et sur la source de données.  
  
     Contrairement aux `AddNew` et `Edit`, `Delete` n’a pas correspondante `Update` appeler.  
  
4.  Faites défiler vers un autre enregistrement.  
  
    > [!NOTE]
    >  Lors du déplacement dans le jeu d’enregistrements, enregistrements supprimés ne peuvent pas être ignorés. Pour plus d’informations, consultez le [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted) fonction membre.  
  
 L’exemple suivant montre un `Delete` opération. Il suppose que l’utilisateur a été déplacé vers un enregistrement de l’utilisateur souhaite supprimer. Après avoir `Delete` est appelée, il est important de se déplacer vers un nouvel enregistrement.  
  
```  
rsStudent.Delete( );  
rsStudent.MoveNext( );  
```  
  
 Pour plus d’informations sur les effets de la `AddNew`, `Edit`, et `Delete` fonctions membres, consultez [Recordset : mise à jour des enregistrements par les Recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Recordset (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Recordset : verrouillage d’enregistrements (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
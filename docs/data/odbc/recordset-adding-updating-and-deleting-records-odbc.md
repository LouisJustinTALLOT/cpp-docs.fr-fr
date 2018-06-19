---
title: 'Recordset : Ajout, modification et suppression d’enregistrements (ODBC) | Documents Microsoft'
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
ms.openlocfilehash: af3a3eb08ce5749c0cfe5ca2d1f59213826ff7ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095194"
---
# <a name="recordset-adding-updating-and-deleting-records-odbc"></a>Recordset : ajout, modification et suppression d'enregistrements (ODBC)
Cette rubrique s’applique aux classes ODBC MFC.  
  
> [!NOTE]
>  Vous pouvez maintenant ajouter des enregistrements en bloc plus efficacement. Pour plus d’informations, consultez [Recordset : ajout d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-adding-records-in-bulk-odbc.md).  
  
> [!NOTE]
>  Cette rubrique s’applique aux objets dérivés de `CRecordset` dans les lignes en bloc l’extraction n’a pas été implémentée. Si vous utilisez l’extraction de lignes en bloc, consultez [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Les instantanés et les feuilles de réponse dynamiques permettent d’ajouter, de modifier et supprimer des enregistrements. Cette rubrique explique :  
  
-   [Comment déterminer si le jeu d’enregistrements est modifiable](#_core_determining_whether_your_recordset_is_updatable).  
  
-   [Comment ajouter un nouvel enregistrement](#_core_adding_a_record_to_a_recordset).  
  
-   [Comment modifier un enregistrement existant](#_core_editing_a_record_in_a_recordset).  
  
-   [Comment supprimer un enregistrement](#_core_deleting_a_record_from_a_recordset).  
  
 Pour plus d’informations sur la façon dont les mises à jour sont effectuées et sur la façon dont vos mises à jour apparaissent à d’autres utilisateurs, consultez [Recordset : modification des enregistrements de jeux d’enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md). En règle générale, lorsque vous ajoutez, modifiez ou supprimez un enregistrement, le jeu d’enregistrements modifie immédiatement la source de données. Vous pouvez à la place par lot mises à jour associées dans des transactions. Si une transaction est en cours d’exécution, la mise à jour ne devient-elle pas final jusqu'à ce que vous validez la transaction. Cela vous permet de reprendre ou d’annuler les modifications. Pour plus d’informations sur les transactions, consultez [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).  
  
 Le tableau suivant résume les options disponibles pour les jeux d’enregistrements avec les caractéristiques de mise à jour différents.  
  
### <a name="recordset-readupdate-options"></a>Options de lecture/mise à jour de jeu d’enregistrements  
  
|Type|Lecture|Modifier l’enregistrement|Suppression de l’enregistrement|Ajouter de nouvelles (Ajouter)|  
|----------|----------|-----------------|-------------------|------------------------|  
|Propriétés en lecture seule|Y|N|N|N|  
|En mode Append-only|Y|N|N|Y|  
|Pleinement modifiable|Y|Y|Y|Y|  
  
##  <a name="_core_determining_whether_your_recordset_is_updatable"></a> Déterminer si votre jeu d’enregistrements est modifiable  
 Un objet recordset est modifiable si la source de données est modifiable et que vous avez ouvert le jeu d’enregistrements en tant que mise à jour. Sa mise à jour dépend également de l’instruction SQL que vous utilisez, les fonctionnalités du pilote ODBC, et si la bibliothèque de curseurs ODBC est en mémoire. Vous ne pouvez pas mettre à jour une source de données ou le jeu d’enregistrements en lecture seule.  
  
#### <a name="to-determine-whether-your-recordset-is-updatable"></a>Pour déterminer si le jeu d’enregistrements est modifiable  
  
1.  Appelez l’objet recordset [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) fonction membre.  
  
     `CanUpdate` Retourne une valeur différente de zéro si le jeu d’enregistrements est modifiable.  
  
 Par défaut, les jeux d’enregistrements est entièrement modifiables (vous pouvez effectuer `AddNew`, **modifier**, et **supprimer** operations). Mais vous pouvez également utiliser le [appendOnly](../../mfc/reference/crecordset-class.md#open) option pour ouvrir des recordsets modifiables. Un jeu d’enregistrements ouvert de cette façon permet uniquement l’ajout de nouveaux enregistrements avec `AddNew`. Vous ne pouvez pas modifier ou supprimer des enregistrements existants. Vous pouvez tester si un jeu d’enregistrements est ouvert uniquement pour l’ajout en appelant le [CanAppend](../../mfc/reference/crecordset-class.md#canappend) fonction membre. `CanAppend` Retourne une valeur différente de zéro si le jeu d’enregistrements est modifiable ou ouvert uniquement pour l’ajout.  
  
 Le code suivant montre comment vous pouvez utiliser `CanUpdate` pour un objet recordset appelé `rsStudentSet`:  
  
```  
if( !rsStudentSet.Open( ) )  
    return FALSE;  
if( !rsStudentSet.CanUpdate( ) )  
{  
    AfxMessageBox( "Unable to update the Student recordset." );  
    return;  
}  
```  
  
> [!CAUTION]
>  Lorsque vous vous préparez à mettre à jour un jeu d’enregistrements en appelant **mettre à jour**, prenez soin que le jeu d’enregistrements comporte toutes les colonnes constituant la clé primaire de la table (ou toutes les colonnes d’un index unique sur la table). Dans certains cas, l’infrastructure peut utiliser uniquement les colonnes sélectionnées dans le jeu d’enregistrements pour identifier l’enregistrement de la table à mettre à jour. Sans toutes les colonnes nécessaires, plusieurs enregistrements peuvent être mis à jour dans la table, éventuellement endommager l’intégrité référentielle de la table. Dans ce cas, le framework lève des exceptions lorsque vous appelez **mise à jour**.  
  
##  <a name="_core_adding_a_record_to_a_recordset"></a> Ajout d’un enregistrement à un jeu d’enregistrements  
 Vous pouvez ajouter de nouveaux enregistrements à un jeu d’enregistrements si sa [CanAppend](../../mfc/reference/crecordset-class.md#canappend) fonction membre retourne une valeur différente de zéro.  
  
#### <a name="to-add-a-new-record-to-a-recordset"></a>Pour ajouter un nouvel enregistrement à un jeu d’enregistrements  
  
1.  Assurez-vous que le jeu d’enregistrements est modifiable.  
  
2.  Appelez l’objet recordset [AddNew](../../mfc/reference/crecordset-class.md#addnew) fonction membre.  
  
     `AddNew` prépare le jeu d’enregistrements en tant que tampon d’édition. Tous les membres de données de champ sont définis sur la valeur spéciale Null et marqués comme non modifié afin que modifié (erronée) les valeurs sont écrites dans la source de données lorsque vous appelez [mise à jour](../../mfc/reference/crecordset-class.md#update).  
  
3.  Définir les valeurs des membres de données de champ du nouvel enregistrement.  
  
     Assigner des valeurs aux membres de données de champ. Ceux que vous n’affectez pas ne sont pas écrites dans la source de données.  
  
4.  Appelez l’objet recordset **mise à jour** fonction membre.  
  
     **Mise à jour** termine l’ajout en écrivant le nouvel enregistrement à la source de données. Pour plus d’informations sur se produit si vous ne pouvez pas appeler **mise à jour**, consultez [Recordset : modification des enregistrements de jeux d’enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
 Pour plus d’informations sur le fonctionnement de l’ajout d’enregistrements et lorsque les enregistrements ajoutés sont visibles dans le jeu d’enregistrements, consultez [Recordset : fonctionnement d’AddNew, Edit et Delete (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md).  
  
 L’exemple suivant montre comment ajouter un nouvel enregistrement :  
  
```  
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
>  Pour annuler un `AddNew` ou **modifier** appeler, rendez un autre appel à `AddNew` ou **modifier** ou appelez **déplacer** avec la **AFX_MOVE_REFRESH**  paramètre. Membres de données sont réinitialisés à leurs valeurs précédentes et vous êtes toujours dans **modifier** ou **ajouter** mode.  
  
##  <a name="_core_editing_a_record_in_a_recordset"></a> Modification d’un enregistrement dans un jeu d’enregistrements  
 Vous pouvez modifier des enregistrements existants si le jeu d’enregistrements [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) fonction membre retourne une valeur différente de zéro.  
  
#### <a name="to-edit-an-existing-record-in-a-recordset"></a>Pour modifier un enregistrement existant dans un jeu d’enregistrements  
  
1.  Assurez-vous que le jeu d’enregistrements est modifiable.  
  
2.  Accédez à l’enregistrement que vous souhaitez mettre à jour.  
  
3.  Appelez l’objet recordset [modifier](../../mfc/reference/crecordset-class.md#edit) fonction membre.  
  
     **Modifier** prépare le jeu d’enregistrements en tant que tampon d’édition. Tous les membres de données de champ sont marqués pour que le jeu d’enregistrements peut indiquer ultérieurement s’ils ont été modifiés. Les nouvelles valeurs des membres de données de champ modifiés sont écrites dans la source de données lorsque vous appelez [mise à jour](../../mfc/reference/crecordset-class.md#update).  
  
4.  Définir les valeurs des membres de données de champ du nouvel enregistrement.  
  
     Assigner des valeurs aux membres de données de champ. Ces derniers que vous n’affectez pas de valeurs rester inchangées.  
  
5.  Appelez l’objet recordset **mise à jour** fonction membre.  
  
     **Mise à jour** termine la modification en écrivant l’enregistrement modifié dans la source de données. Pour plus d’informations sur se produit si vous ne pouvez pas appeler **mise à jour**, consultez [Recordset : modification des enregistrements de jeux d’enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
 Après avoir modifié un enregistrement, celui-ci demeure l’enregistrement actif.  
  
 L’exemple suivant montre une **modifier** opération. Il suppose que l’utilisateur a été déplacé vers un enregistrement qu’il souhaite modifier.  
  
```  
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
>  Pour annuler un `AddNew` ou **modifier** appeler, rendez un autre appel à `AddNew` ou **modifier** ou appelez **déplacer** avec la **AFX_MOVE_REFRESH**  paramètre. Membres de données sont réinitialisés à leurs valeurs précédentes et vous êtes toujours dans **modifier** ou **ajouter** mode.  
  
##  <a name="_core_deleting_a_record_from_a_recordset"></a> Suppression d’un enregistrement à partir d’un jeu d’enregistrements  
 Vous pouvez supprimer des enregistrements si votre jeu d’enregistrements [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) fonction membre retourne une valeur différente de zéro.  
  
#### <a name="to-delete-a-record"></a>Pour supprimer un enregistrement  
  
1.  Assurez-vous que le jeu d’enregistrements est modifiable.  
  
2.  Accédez à l’enregistrement que vous souhaitez mettre à jour.  
  
3.  Appelez l’objet recordset [supprimer](../../mfc/reference/crecordset-class.md#delete) fonction membre.  
  
     **Supprimer** marque immédiatement l’enregistrement comme supprimé, à la fois dans le jeu d’enregistrements et sur la source de données.  
  
     Contrairement aux `AddNew` et **modifier**, **supprimer** n’est associée à aucun **mise à jour** appeler.  
  
4.  Accédez à un autre enregistrement.  
  
    > [!NOTE]
    >  Lorsque vous déplacez le jeu d’enregistrements, enregistrements supprimés ne peuvent pas être ignorés. Pour plus d’informations, consultez la [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted) fonction membre.  
  
 L’exemple suivant montre un **supprimer** opération. Il suppose que l’utilisateur a été déplacé vers un enregistrement de l’utilisateur souhaite supprimer. Après avoir **supprimer** est appelée, il est important de se déplacer vers un nouvel enregistrement.  
  
```  
rsStudent.Delete( );  
rsStudent.MoveNext( );  
```  
  
 Pour plus d’informations sur les effets de la `AddNew`, **modifier**, et **supprimer** fonctions membres, consultez [Recordset : mise à jour des enregistrements de jeux d’enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Jeu d’enregistrements (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Recordset : verrouillage d’enregistrements (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
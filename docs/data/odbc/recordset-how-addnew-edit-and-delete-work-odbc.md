---
title: 'Recordset : AddNew, Edit et Delete fonctionnement (ODBC) | Documents Microsoft'
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
- AddNew method
- ODBC recordsets [C++], deleting records
- records [C++], deleting in recordsets
- data in recordsets [C++]
- recordsets [C++], deleting records
- ODBC recordsets [C++], editing records
- records [C++], editing
ms.assetid: cab43d43-235a-4bed-ac05-67d10e94f34e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e3d9dc82f4ea31557c4ec330b9737579021a8d35
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094128"
---
# <a name="recordset-how-addnew-edit-and-delete-work-odbc"></a>Recordset : fonctionnement d'AddNew, Edit et Delete (ODBC)
Cette rubrique s’applique aux classes ODBC MFC.  
  
 Cette rubrique explique comment les `AddNew`, **modifier**, et **supprimer** fonctions membres de classe `CRecordset` de travail. Les sujets abordés sont les suivantes :  
  
-   [Fonctionnement de l’ajout d’enregistrements](#_core_adding_a_record)  
  
-   [Visibilité des enregistrements ajoutés](#_core_visibility_of_added_records)  
  
-   [Fonctionne de la modification d’enregistrements](#_core_editing_an_existing_record)  
  
-   [Fonctionnement de la suppression d’enregistrements](#_core_deleting_a_record)  
  
> [!NOTE]
>  Cette rubrique s’applique aux objets dérivés de `CRecordset` dans les lignes en bloc l’extraction n’a pas été implémentée. Si vous utilisez l’extraction de lignes en bloc, consultez [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 En tant que complément d’information, vous pouvez souhaiter lire [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md), qui décrit le rôle correspondant de RFX dans les opérations de mise à jour.  
  
##  <a name="_core_adding_a_record"></a> Ajout d’un enregistrement  

 Ajout d’un nouvel enregistrement à un jeu d’enregistrements implique l’appel de l’ensemble d’enregistrements [AddNew](../../mfc/reference/crecordset-class.md#addnew) , définition des valeurs des membres de données de champ du nouvel enregistrement et appel de fonction membre la [mise à jour](../../mfc/reference/crecordset-class.md#update) fonction membre à écrire l’enregistrement de la source de données.  
  
 Comme condition préalable de l’appel `AddNew`, le jeu d’enregistrements de ne doit pas avoir été ouvert en lecture seule. Le `CanUpdate` et `CanAppend` fonctions membres vous permettent de définir ces conditions.  
  
 Lorsque vous appelez `AddNew`:  
  
-   L’enregistrement dans le tampon d’édition est stocké, donc son contenu peut être restauré si l’opération est annulée.  
  
-   Données membres de champ sont marqués afin qu’il est possible de détecter les modifications dans les versions ultérieures. Les données des champs membres sont également marqués nettoyer (non modifié) et la valeur Null.  
  
 Après avoir appelé `AddNew`, le tampon d’édition représente une nouvelle, enregistrement vide, prêt à être remplie avec les valeurs. Pour ce faire, vous définissez manuellement les valeurs. Au lieu de spécifier une valeur réelle des données pour un champ, vous pouvez appeler `SetFieldNull` pour spécifier la valeur Null.  
  
 Pour valider vos modifications, vous appelez **mise à jour**. Lorsque vous appelez **mise à jour** pour le nouvel enregistrement :  
  
-   Si votre pilote ODBC prend en charge la **:: SQLSetPos** fonction d’API ODBC, MFC utilise la fonction pour ajouter l’enregistrement à la source de données. Avec **:: SQLSetPos**, MFC peut ajouter un enregistrement plus efficacement, car il n’a pas à construire et à traiter une instruction SQL.  
  
-   Si **:: SQLSetPos** ne peut pas être utilisé, MFC effectue les opérations suivantes :  
  
    1.  Si aucune modification n’est détectée, **mise à jour** ne fait rien et retourne 0.  
  
    2.  Si des modifications sont apportées, **mise à jour** construit SQL **insérer** instruction. Les colonnes représentées par tous les membres de données de champ incorrectes sont répertoriées dans le **insérer** instruction. Pour forcer une colonne à inclure, appelez le [SetFieldDirty](../../mfc/reference/crecordset-class.md#setfielddirty) fonction membre :  
  
        ```  
        SetFieldDirty( &m_dataMember, TRUE );  
        ```  
  
    3.  **Mise à jour** valide le nouvel enregistrement, la **insérer** instruction est exécutée et l’enregistrement est validé dans la table de la source de données (et le jeu d’enregistrements, si ce n’est pas un instantané), sauf si une transaction est en cours d’exécution.  
  
    4.  L’enregistrement stocké est restaurée dans le tampon d’édition. L’enregistrement en cours avant la `AddNew` appel est en cours à nouveau indépendamment du fait que la **insérer** instruction a été exécutée avec succès.  
  
    > [!TIP]
    >  Pour un contrôle complet d’un nouvel enregistrement, suivez la solution suivante : définissez les valeurs de tous les champs qui contiendront des valeurs, puis définissez explicitement les champs conserveront la valeur Null en appelant `SetFieldNull` avec un pointeur vers le champ et le paramètre **TRUE**  (la valeur par défaut). Si vous souhaitez vous assurer qu’un champ n’est pas écrit à la source de données, appel `SetFieldDirty` avec un pointeur vers le champ et le paramètre **FALSE**et ne modifiez pas la valeur du champ. Pour déterminer si un champ peut être Null, appelez `IsFieldNullable`.  
  
    > [!TIP]
    >  Pour détecter si les membres de données de jeu d’enregistrements changent de valeur, MFC utilise un **PSEUDO_NULL** valeur appropriée à chaque type de données que vous pouvez stocker dans un recordset. Si vous devez explicitement définir un champ la **PSEUDO_NULL** valeur et le champ a déjà été marqué Null, vous devez également appeler `SetFieldNull`, en passant l’adresse du champ dans le premier paramètre et **FALSE**dans le second paramètre.  
  
##  <a name="_core_visibility_of_added_records"></a> Visibilité des enregistrements ajoutés  
 Un enregistrement ajouté est visible pour le jeu d’enregistrements ? Les enregistrements ajoutés apparaissent parfois et parfois, ne sont pas visibles, en fonction de deux choses :  
  
-   Définition de votre pilote est capable de.  
  
-   Ce que l’infrastructure peut tirer parti de.  
  
 Si votre pilote ODBC prend en charge la **:: SQLSetPos** fonction d’API ODBC, MFC utilise la fonction pour ajouter des enregistrements. Avec **:: SQLSetPos**, enregistrements ajoutés sont visibles par tout recordset MFC modifiable. Sans la prise en charge pour la fonction, ajouté des enregistrements ne sont pas visibles et vous devez appeler **Requery** pour les afficher. À l’aide de **:: SQLSetPos** est également plus efficace.  
  
##  <a name="_core_editing_an_existing_record"></a> Modifier un enregistrement existant  
 Modifier un enregistrement existant dans un jeu d’enregistrements nécessite de faire défiler à l’enregistrement, l’appel de l’ensemble d’enregistrements [modifier](../../mfc/reference/crecordset-class.md#edit) , définition des valeurs des membres de données de champ du nouvel enregistrement et appel de fonction membre la [mettre à jour](../../mfc/reference/crecordset-class.md#update)fonction membre pour écrire l’enregistrement modifié dans la source de données.  
  
 Comme condition préalable de l’appel **modifier**, le jeu d’enregistrements doit être modifiable et d’un enregistrement. Le `CanUpdate` et `IsDeleted` fonctions membres vous permettent de définir ces conditions. L’enregistrement actif ne doit pas avoir été déjà supprimé et des enregistrements doivent être présents dans le jeu d’enregistrements (les deux `IsBOF` et `IsEOF` retournent 0).  
  
 Lorsque vous appelez **modifier**, l’enregistrement dans le tampon d’édition (l’enregistrement actif) est stocké. Les valeurs de l’enregistrement stocké sont ultérieurement utilisés pour détecter si tous les champs ont été modifiés.  
  
 Après avoir appelé **modifier**, le tampon d’édition est toujours représente l’enregistrement actif mais est maintenant prêt à accepter les modifications apportées aux données membres de champ. Pour modifier l’enregistrement, vous définissez manuellement les valeurs de tous les membres de données de champ à modifier. Au lieu de spécifier une valeur réelle des données pour un champ, vous pouvez appeler `SetFieldNull` pour spécifier la valeur Null. Pour valider vos modifications, appelez **mise à jour**.  
  
> [!TIP]
>  Pour tirer parti de `AddNew` ou **modifier** mode, appelez **déplacer** avec le paramètre **AFX_MOVE_REFRESH**.  
  
 Comme condition préalable de l’appel **mise à jour**, le jeu d’enregistrements ne doit pas être vide et l’enregistrement actif ne doit pas avoir été supprimé. `IsBOF`, `IsEOF`, et `IsDeleted` doit retourner la valeur 0.  
  
 Lorsque vous appelez **mise à jour** pour l’enregistrement modifié :  
  
-   Si votre pilote ODBC prend en charge la **:: SQLSetPos** fonction d’API ODBC, MFC utilise la fonction pour mettre à jour l’enregistrement de la source de données. Avec **:: SQLSetPos**, le pilote compare le tampon d’édition et l’enregistrement correspondant sur le serveur, la mise à jour de l’enregistrement sur le serveur si les deux sont différents. Avec **:: SQLSetPos**, MFC peut mettre à jour plus efficacement un enregistrement, car il n’a pas à construire et à traiter une instruction SQL.  
  
     - ou -  
  
-   Si **:: SQLSetPos** ne peut pas être utilisé, MFC effectue les opérations suivantes :  
  
    1.  Si aucune modification, n’ont été **mise à jour** ne fait rien et retourne 0.  
  
    2.  Si des modifications sont apportées, **mise à jour** construit SQL **mise à jour** instruction. Les colonnes répertoriées dans le **mise à jour** instruction sont basées sur les membres de données de champ qui ont été modifiés.  
  
    3.  **Mise à jour** valide les modifications — exécute la **mise à jour** instruction — et l’enregistrement est modifié sur la source de données, mais non validé si une transaction est en cours d’exécution (consultez [Transaction : exécution d’une Transaction dans un jeu d’enregistrements (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md) pour plus d’informations sur les effets de la transaction sur la mise à jour). ODBC conserve une copie de l’enregistrement, qui change également.  
  
    4.  Contrairement au processus de `AddNew`, le **modifier** processus ne restaure pas l’enregistrement stocké. L’enregistrement modifié reste en place en tant que l’enregistrement actif.  
  
    > [!CAUTION]
    >  Lorsque vous vous préparez à mettre à jour un jeu d’enregistrements en appelant **mettre à jour**, prenez soin que le jeu d’enregistrements comporte toutes les colonnes constituant la clé primaire de la table (ou toutes les colonnes de toute unique index unique sur la table ou de colonnes est insuffisant pour identification de la ligne). Dans certains cas, l’infrastructure peut utiliser uniquement les colonnes sélectionnées dans le jeu d’enregistrements pour identifier l’enregistrement de la table à mettre à jour. Sans toutes les colonnes nécessaires, plusieurs enregistrements peuvent être mis à jour dans la table. Dans ce cas, le framework lève des exceptions lorsque vous appelez **mise à jour**.  
  
    > [!TIP]
    >  Si vous appelez `AddNew` ou **modifier** après avoir appelé une fonction précédemment, mais avant d’appeler **mise à jour**, le tampon d’édition est actualisé avec l’enregistrement stocké, en remplaçant l’enregistrement de nouveaux ou modifié dans état d’avancement. Ce comportement vous permet d’annuler un `AddNew` ou **modifier** et commencer une nouvelle : Si vous déterminez que l’enregistrement en cours est erroné, appelez simplement **modifier** ou `AddNew` à nouveau.  
  
##  <a name="_core_deleting_a_record"></a> Suppression d’un enregistrement  
 Suppression d’un enregistrement à partir d’un jeu d’enregistrements nécessite le défilement à l’enregistrement et l’appel de l’ensemble d’enregistrements [supprimer](../../mfc/reference/crecordset-class.md#delete) fonction membre. Contrairement aux `AddNew` et **modifier**, **supprimer** ne nécessite pas un appel correspondant à **mise à jour**.  
  
 Comme condition préalable de l’appel **supprimer**, le jeu d’enregistrements doive être mis à jour et il doit s’agir d’un enregistrement. Le `CanUpdate`, `IsBOF`, `IsEOF`, et `IsDeleted` fonctions membres vous permettent de définir ces conditions.  
  
 Lorsque vous appelez **supprimer**:  
  
-   Si votre pilote ODBC prend en charge la **:: SQLSetPos** fonction d’API ODBC, MFC utilise la fonction pour supprimer l’enregistrement sur la source de données. À l’aide de **:: SQLSetPos** est généralement plus efficace que celle de SQL.  
  
     - ou -  
  
-   Si **:: SQLSetPos** ne peut pas être utilisé, MFC effectue les opérations suivantes :  
  
    1.  L’enregistrement actif dans le tampon d’édition n’est pas sauvegardé comme dans `AddNew` et **modifier**.  
  
    2.  **Supprimer** construit SQL **supprimer** instruction qui supprime l’enregistrement.  
  
         L’enregistrement actif dans le tampon d’édition n’est pas stockée comme dans `AddNew` et **modifier**.  
  
    3.  **Supprimer** valide la suppression : exécute le **supprimer** instruction. L’enregistrement est marqué comme supprimé sur la source de données et, si l’enregistrement est un instantané, dans ODBC.  
  
    4.  Les valeurs de l’enregistrement supprimé se trouvent toujours dans les données membres de champ de l’objet recordset, mais les membres de données de champ sont marqués valeur Null et le jeu d’enregistrements `IsDeleted` fonction membre retourne une valeur différente de zéro.  
  
    > [!NOTE]
    >  Après la suppression d’un enregistrement, vous devez défiler à un autre enregistrement pour le rechargement de la mémoire tampon de modification avec les données du nouvel enregistrement. Il s’agit d’une erreur d’appeler **supprimer** à nouveau ou appeler **modifier**.  
  
 Pour plus d’informations sur les instructions SQL utilisées dans les opérations de mise à jour, consultez [SQL](../../data/odbc/sql.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Jeu d’enregistrements (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Recordset : en savoir plus sur les mises à jour (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)   
 [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md)
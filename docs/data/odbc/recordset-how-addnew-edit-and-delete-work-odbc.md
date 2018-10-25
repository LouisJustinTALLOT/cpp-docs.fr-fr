---
title: 'Recordset : AddNew, Edit et Delete fonctionnement (ODBC) | Microsoft Docs'
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
ms.openlocfilehash: 38125a5808892593f270e178b2e585eb1ba47edb
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077242"
---
# <a name="recordset-how-addnew-edit-and-delete-work-odbc"></a>Recordset : fonctionnement d'AddNew, Edit et Delete (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Cette rubrique explique comment la `AddNew`, `Edit`, et `Delete` fonctions membres de classe `CRecordset` fonctionne. Les sujets abordés incluent :

- [Fonctionnement de l’ajout d’enregistrements](#_core_adding_a_record)

- [Visibilité des enregistrements ajoutés](#_core_visibility_of_added_records)

- [Fonctionne de la modification d’enregistrements](#_core_editing_an_existing_record)

- [Fonctionnement de la suppression d’enregistrements](#_core_deleting_a_record)

> [!NOTE]
>  Cette rubrique s’applique aux objets dérivés de `CRecordset` dans les lignes en bloc l’extraction n’a pas été implémentée. Si vous utilisez l’extraction de lignes en bloc, consultez [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

En complément, vous pouvez souhaiter lire [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md), qui décrit le rôle correspondant de RFX dans les opérations de mise à jour.

##  <a name="_core_adding_a_record"></a> Ajout d’un enregistrement

Ajout d’un nouvel enregistrement à un jeu d’enregistrements implique l’appel du jeu d’enregistrements [AddNew](../../mfc/reference/crecordset-class.md#addnew) , définissant les valeurs des membres de données de champ du nouvel enregistrement et appel de fonction membre la [mise à jour](../../mfc/reference/crecordset-class.md#update) fonction membre à écrire l’enregistrement à la source de données.

Comme condition préalable pour appeler `AddNew`, le jeu d’enregistrements ne doit pas avoir été ouvert en lecture seule. Le `CanUpdate` et `CanAppend` fonctions membres vous permettent de définir ces conditions.

Lorsque vous appelez `AddNew`:

- L’enregistrement dans la mémoire tampon d’édition est stocké, donc son contenu peut être restauré si l’opération est annulée.

- Les membres de données de champ sont marquées comme il est donc possible de détecter les modifications dans les versions ultérieures. Les données des champs membres sont également marqués nettoyer (inchangée) et la valeur est une valeur Null.

Après avoir appelé `AddNew`, la mémoire tampon d’édition représente une nouvelle, enregistrement vide, prêt à remplir avec les valeurs. Pour ce faire, vous définir manuellement les valeurs. Au lieu de spécifier une valeur réelle des données pour un champ, vous pouvez appeler `SetFieldNull` pour spécifier la valeur Null.

Pour valider vos modifications, vous appelez `Update`. Lorsque vous appelez `Update` pour le nouvel enregistrement :

- Si votre pilote ODBC prend en charge la `::SQLSetPos` fonction API ODBC, MFC utilise la fonction pour ajouter l’enregistrement à la source de données. Avec `::SQLSetPos`, MFC peut ajouter un enregistrement plus efficacement, car il n’a pas à construire et à traiter une instruction SQL.

- Si `::SQLSetPos` ne peut pas être utilisé, MFC effectue les opérations suivantes :

    1.  Si aucune modification n’est détectée, `Update` ne fait rien et retourne 0.

    2.  Si des modifications sont apportées, `Update` construit une instance SQL **insérer** instruction. Les colonnes représentées par tous les membres de données de champ incorrectes sont répertoriées dans le **insérer** instruction. Pour forcer une colonne à inclure, appelez le [SetFieldDirty](../../mfc/reference/crecordset-class.md#setfielddirty) fonction membre :

        ```
        SetFieldDirty( &m_dataMember, TRUE );
        ```

    3.  `Update` valide le nouvel enregistrement — le **insérer** instruction est exécutée et l’enregistrement est validé à la table sur la source de données (et le jeu d’enregistrements, si ce n’est pas un instantané), sauf si une transaction est en cours d’exécution.

    4.  L’enregistrement stocké est restaurée dans la mémoire tampon d’édition. L’enregistrement qui était actuel avant le `AddNew` appel est en cours à nouveau ait ou non la **insérer** instruction a été exécutée avec succès.

    > [!TIP]
    >  Pour un contrôle complet d’un nouvel enregistrement, adoptez l’approche suivante : définir les valeurs de tous les champs qui contiendront des valeurs, puis définissez explicitement tous les champs qui resteront Null en appelant `SetFieldNull` avec un pointeur vers le champ et le paramètre TRUE (valeur par défaut). Si vous souhaitez vous assurer qu’un champ n’est pas écrit à la source de données, appel `SetFieldDirty` avec un pointeur vers le champ et le paramètre FALSE et ne modifiez pas la valeur du champ. Pour déterminer si un champ est autorisé à avoir la valeur Null, appelez `IsFieldNullable`.

    > [!TIP]
    >  Pour détecter les membres de données de jeu d’enregistrements changent de valeur, MFC utilise la valeur PSEUDO_NULL appropriée à chaque type de données que vous pouvez stocker dans un jeu d’enregistrements. Si vous devez explicitement définir un champ avec la valeur PSEUDO_NULL et que le champ se trouve déjà être marquées Null, vous devez également appeler `SetFieldNull`, en passant l’adresse du champ dans le premier paramètre et FALSE dans le deuxième paramètre.

##  <a name="_core_visibility_of_added_records"></a> Visibilité des enregistrements ajoutés

Lorsque est un enregistrement ajouté visible pour le jeu d’enregistrements ? Les enregistrements ajoutés apparaissent parfois et parfois ne sont pas visibles, en fonction de deux choses :

- Définition de votre pilote est capable de.

- Ce que l’infrastructure peut tirer parti.

Si votre pilote ODBC prend en charge la `::SQLSetPos` fonction API ODBC, MFC utilise la fonction pour ajouter des enregistrements. Avec `::SQLSetPos`, enregistrements ajoutés sont visibles par tout recordset MFC modifiable. Sans prise en charge pour la fonction, ajouté les enregistrements ne sont pas visibles et vous devez appeler `Requery` pour les afficher. À l’aide de `::SQLSetPos` est également plus efficace.

##  <a name="_core_editing_an_existing_record"></a> Modifier un enregistrement existant

Modifier un enregistrement existant dans un jeu d’enregistrements nécessite de faire défiler à l’enregistrement, en appelant le jeu d’enregistrements [modifier](../../mfc/reference/crecordset-class.md#edit) , définissant les valeurs des membres de données de champ du nouvel enregistrement et appel de fonction membre la [mettre à jour](../../mfc/reference/crecordset-class.md#update)fonction membre pour écrire l’enregistrement modifié dans la source de données.

Comme condition préalable pour appeler `Edit`, le jeu d’enregistrements doit être modifiable et sur un enregistrement. Le `CanUpdate` et `IsDeleted` fonctions membres vous permettent de définir ces conditions. L’enregistrement en cours ne doit pas avoir été déjà supprimé, et il doit y avoir des enregistrements dans le jeu d’enregistrements (les deux `IsBOF` et `IsEOF` retournent 0).

Lorsque vous appelez `Edit`, l’enregistrement dans la mémoire tampon d’édition (l’enregistrement actif) est stocké. Les valeurs de d’enregistrement stockées sont utilisées ultérieurement pour détecter si tous les champs ont été modifiés.

Après avoir appelé `Edit`, la mémoire tampon d’édition est toujours représente l’enregistrement en cours mais est maintenant prêt à accepter les modifications apportées aux données membres de champ. Pour modifier l’enregistrement, vous définissez manuellement les valeurs des membres de données de champ que vous souhaitez modifier. Au lieu de spécifier une valeur réelle des données pour un champ, vous pouvez appeler `SetFieldNull` pour spécifier la valeur Null. Pour valider vos modifications, appelez `Update`.

> [!TIP]
>  Pour tirer parti de `AddNew` ou `Edit` mode, appelez `Move` avec le paramètre *AFX_MOVE_REFRESH*.

Comme condition préalable pour appeler `Update`, le jeu d’enregistrements ne doit pas être vide et l’enregistrement actif ne doit pas avoir été supprimé. `IsBOF`, `IsEOF`, et `IsDeleted` doit retourner la valeur 0.

Lorsque vous appelez `Update` pour l’enregistrement modifié :

- Si votre pilote ODBC prend en charge la `::SQLSetPos` fonction API ODBC, MFC utilise la fonction pour mettre à jour l’enregistrement sur la source de données. Avec `::SQLSetPos`, le pilote compare le tampon d’édition et l’enregistrement correspondant sur le serveur, la mise à jour de l’enregistrement sur le serveur si les deux sont différents. Avec `::SQLSetPos`, MFC peut mettre à jour plus efficacement un enregistrement, car il n’a pas à construire et à traiter une instruction SQL.

     - ou -

- Si `::SQLSetPos` ne peut pas être utilisé, MFC effectue les opérations suivantes :

    1.  S’il n’y a eu aucune modification, `Update` ne fait rien et retourne 0.

    2.  Si des modifications sont apportées, `Update` construit une instance SQL **mise à jour** instruction. Les colonnes répertoriées dans le **mise à jour** instruction sont basées sur les données membres de champ qui ont été modifiés.

    3.  `Update` valide les modifications — exécute la **mise à jour** instruction — et l’enregistrement est modifié sur la source de données, mais non validé si une transaction est en cours d’exécution (consultez [Transaction : exécution d’une Transaction dans un Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md) pour plus d’informations sur les effets de la transaction sur la mise à jour). ODBC conserve une copie de l’enregistrement, ce qui modifie également.

    4.  Contrairement au processus pour `AddNew`, le `Edit` processus ne restaure pas l’enregistrement stocké. L’enregistrement modifié reste en place comme enregistrement actif.

    > [!CAUTION]
    >  Lorsque vous vous préparez à mettre à jour un jeu d’enregistrements en appelant `Update`, prenez soin que le jeu d’enregistrements comporte toutes les colonnes qui constituent la clé primaire de la table (ou toutes les colonnes d’un index unique sur la table, ou de colonnes est insuffisant pour identifier la ligne). Dans certains cas, le framework peut utiliser uniquement les colonnes sélectionnées dans votre jeu d’enregistrements pour identifier l’enregistrement de la table à mettre à jour. Sans toutes les colonnes nécessaires, plusieurs enregistrements peuvent être mis à jour dans la table. Dans ce cas, le framework lève des exceptions lorsque vous appelez `Update`.

    > [!TIP]
    >  Si vous appelez `AddNew` ou `Edit` après avoir appelé une fonction précédemment mais avant d’appeler `Update`, la mémoire tampon d’édition est actualisé avec l’enregistrement stocké, en remplaçant l’enregistrement nouveau ou modifié en cours. Ce comportement vous donne un moyen d’interrompre une `AddNew` ou `Edit` et commencer une nouvelle : Si vous déterminez que l’enregistrement en cours est défectueux, appelez simplement `Edit` ou `AddNew` à nouveau.

##  <a name="_core_deleting_a_record"></a> Suppression d’un enregistrement

Suppression d’un enregistrement à partir d’un jeu d’enregistrements nécessite le défilement à l’enregistrement et l’appel de l’ensemble d’enregistrements [supprimer](../../mfc/reference/crecordset-class.md#delete) fonction membre. Contrairement aux `AddNew` et `Edit`, `Delete` ne nécessite pas un appel correspondant à `Update`.

Comme condition préalable pour appeler `Delete`, le jeu d’enregistrements doit être mis à jour et il doit se trouver sur un enregistrement. Le `CanUpdate`, `IsBOF`, `IsEOF`, et `IsDeleted` fonctions membres vous permettent de définir ces conditions.

Lorsque vous appelez `Delete`:

- Si votre pilote ODBC prend en charge la `::SQLSetPos` fonction API ODBC, MFC utilise la fonction pour supprimer l’enregistrement sur la source de données. À l’aide de `::SQLSetPos` est généralement plus efficace que celle de SQL.

     - ou -

- Si `::SQLSetPos` ne peut pas être utilisé, MFC effectue les opérations suivantes :

    1.  L’enregistrement actif dans la mémoire tampon d’édition n’est pas sauvegardé en tant que dans `AddNew` et `Edit`.

    2.  `Delete` construit une instance SQL **supprimer** instruction qui supprime l’enregistrement.

         L’enregistrement actif dans la mémoire tampon d’édition n’est pas stocké en tant que dans `AddNew` et `Edit`.

    3.  `Delete` valide la suppression — exécute la **supprimer** instruction. L’enregistrement est marqué comme supprimé sur la source de données et, si l’enregistrement est un instantané, dans ODBC.

    4.  Les valeurs de l’enregistrement supprimé se trouvent toujours dans les données membres de champ de l’objet recordset, mais les membres de données de champ sont marquées Null et le jeu d’enregistrements `IsDeleted` fonction membre retourne une valeur différente de zéro.

    > [!NOTE]
    >  Après avoir supprimé un enregistrement, vous devez faire défiler à un autre enregistrement pour le rechargement de la mémoire tampon d’édition avec les données du nouvel enregistrement. C’est une erreur d’appeler `Delete` à nouveau ou appeler `Edit`.

Pour plus d’informations sur les instructions SQL utilisées dans les opérations de mise à jour, consultez [SQL](../../data/odbc/sql.md).

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : informations complémentaires sur les mises à jour (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)<br/>
[Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md)
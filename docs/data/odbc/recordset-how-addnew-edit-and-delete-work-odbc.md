---
title: "Recordset : fonctionnement d'AddNew, Edit et Delete (ODBC)"
ms.date: 11/04/2016
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
ms.openlocfilehash: 8799ac36c443898f1e32b539f017e682bbf3e033
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212903"
---
# <a name="recordset-how-addnew-edit-and-delete-work-odbc"></a>Recordset : fonctionnement d'AddNew, Edit et Delete (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Cette rubrique explique comment les fonctions membres `AddNew`, `Edit`et `Delete` de la classe `CRecordset` fonctionnent. Sont abordés les sujets suivants :

- [Fonctionnement de l’ajout d’enregistrements](#_core_adding_a_record)

- [Visibilité des enregistrements ajoutés](#_core_visibility_of_added_records)

- [Fonctionnement de la modification des enregistrements](#_core_editing_an_existing_record)

- [Fonctionnement de la suppression d’enregistrements](#_core_deleting_a_record)

> [!NOTE]
>  Cette rubrique s’applique aux objets dérivés de `CRecordset` où l’extraction de lignes en bloc n’a pas été implémentée. Si vous utilisez l’extraction de lignes en bloc, consultez [Recordset : extraction globale d’enregistrements (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

En complément, vous pouvez lire [Record Field Exchange :](../../data/odbc/record-field-exchange-how-rfx-works.md)fonctionnement de RFX, qui décrit le rôle correspondant de RFX dans les opérations de mise à jour.

##  <a name="adding-a-record"></a><a name="_core_adding_a_record"></a>Ajout d’un enregistrement

L’ajout d’un nouvel enregistrement à un Recordset implique l’appel de la fonction membre [AddNew](../../mfc/reference/crecordset-class.md#addnew) du Recordset, la définition des valeurs des membres de données de champ du nouvel enregistrement et l’appel de la fonction membre [Update](../../mfc/reference/crecordset-class.md#update) pour écrire l’enregistrement dans la source de données.

Comme condition préalable à l’appel de `AddNew`, le jeu d’enregistrements ne doit pas avoir été ouvert en lecture seule. Les fonctions membres `CanUpdate` et `CanAppend` vous permettent de déterminer ces conditions.

Quand vous appelez `AddNew`:

- L’enregistrement dans le tampon d’édition étant stocké, son contenu peut être restauré si l’opération est annulée.

- Les membres de données de champ sont marqués d’un indicateur. il est donc possible de les détecter ultérieurement. Les données membres de champ sont également marquées Clean (inchangé) et ont la valeur null.

Une fois que vous avez appelé `AddNew`, le tampon d’édition représente un nouvel enregistrement vide, prêt à être renseigné avec des valeurs. Pour ce faire, vous devez définir manuellement les valeurs en leur affectant. Au lieu de spécifier une valeur de données réelle pour un champ, vous pouvez appeler `SetFieldNull` pour spécifier la valeur null.

Pour valider vos modifications, vous appelez `Update`. Lorsque vous appelez `Update` pour le nouvel enregistrement :

- Si votre pilote ODBC prend en charge la fonction API ODBC `::SQLSetPos`, MFC utilise la fonction pour ajouter l’enregistrement sur la source de données. Avec `::SQLSetPos`, les MFC peuvent ajouter plus efficacement un enregistrement, car il n’est pas nécessaire de construire et traiter une instruction SQL.

- Si `::SQLSetPos` ne peut pas être utilisé, MFC effectue les opérations suivantes :

   1. Si aucune modification n’est détectée, `Update` ne fait rien et retourne 0.

   1. En cas de modification, `Update` construit une instruction SQL **Insert** . Les colonnes représentées par tous les membres de données de champs non modifiés sont répertoriées dans l’instruction **Insert** . Pour forcer l’inclusion d’une colonne, appelez la fonction membre [SetFieldDirty](../../mfc/reference/crecordset-class.md#setfielddirty) :

        ```cpp
        SetFieldDirty( &m_dataMember, TRUE );
        ```

   1. `Update` valide le nouvel enregistrement : l’instruction **Insert** est exécutée et l’enregistrement est validé dans la table de la source de données (et le Recordset, s’il ne s’agit pas d’un instantané), à moins qu’une transaction soit en cours.

   1. L’enregistrement stocké est restauré dans le tampon d’édition. L’enregistrement qui était en cours avant l’appel de `AddNew` est à nouveau à jour, que l’instruction **Insert** ait été exécutée avec succès ou non.

   > [!TIP]
   > Pour le contrôle total d’un nouvel enregistrement, procédez comme suit : définissez les valeurs de tous les champs qui auront des valeurs, puis définissez explicitement tous les champs qui resteront null en appelant `SetFieldNull` avec un pointeur vers le champ et le paramètre TRUE (valeur par défaut). Si vous souhaitez vous assurer qu’un champ n’est pas écrit dans la source de données, appelez `SetFieldDirty` avec un pointeur vers le champ et le paramètre FALSe, et ne modifiez pas la valeur du champ. Pour déterminer si un champ peut être null, appelez `IsFieldNullable`.

   > [!TIP]
   > Pour détecter la modification de la valeur des membres de données du jeu d’enregistrements, MFC utilise une valeur de PSEUDO_NULL appropriée à chaque type de données que vous pouvez stocker dans un jeu d’enregistrements. Si vous devez définir explicitement la valeur de PSEUDO_NULL pour un champ et que le champ est déjà marqué comme null, vous devez également appeler `SetFieldNull`, en passant l’adresse du champ dans le premier paramètre et la valeur FALSe dans le deuxième paramètre.

##  <a name="visibility-of-added-records"></a><a name="_core_visibility_of_added_records"></a>Visibilité des enregistrements ajoutés

Quand un enregistrement ajouté est-il visible pour votre Recordset ? Les enregistrements ajoutés s’affichent parfois et ne sont parfois pas visibles, en fonction de deux éléments :

- Ce que votre pilote peut.

- Ce à quoi l’infrastructure peut tirer parti.

Si votre pilote ODBC prend en charge la fonction API ODBC `::SQLSetPos`, MFC utilise la fonction pour ajouter des enregistrements. Avec `::SQLSetPos`, les enregistrements ajoutés sont visibles par tous les jeux d’enregistrements MFC pouvant être mis à jour. Sans prise en charge de la fonction, les enregistrements ajoutés ne sont pas visibles et vous devez appeler `Requery` pour les afficher. L’utilisation de `::SQLSetPos` est également plus efficace.

##  <a name="editing-an-existing-record"></a><a name="_core_editing_an_existing_record"></a>Modification d’un enregistrement existant

La modification d’un enregistrement existant dans un Recordset implique de faire défiler l’enregistrement, d’appeler la fonction membre [Edit](../../mfc/reference/crecordset-class.md#edit) du Recordset, de définir les valeurs des membres de données de champ du nouvel enregistrement et d’appeler la fonction membre [Update](../../mfc/reference/crecordset-class.md#update) pour écrire l’enregistrement modifié dans la source de données.

En guise de condition préalable à l’appel de `Edit`, le Recordset doit pouvoir être mis à jour et se trouver sur un enregistrement. Les fonctions membres `CanUpdate` et `IsDeleted` vous permettent de déterminer ces conditions. L’enregistrement en cours ne doit pas avoir déjà été supprimé, et il doit y avoir des enregistrements dans le jeu d’enregistrements (`IsBOF` et `IsEOF` retourner 0).

Lorsque vous appelez `Edit`, l’enregistrement dans la mémoire tampon d’édition (enregistrement en cours) est stocké. Les valeurs de l’enregistrement stocké sont ensuite utilisées pour détecter si des champs ont été modifiés.

Une fois que vous avez appelé `Edit`, le tampon d’édition représente toujours l’enregistrement actif, mais il est maintenant prêt à accepter les modifications apportées aux membres de données de champ. Pour modifier l’enregistrement, vous devez définir manuellement les valeurs des membres de données de champ que vous souhaitez modifier. Au lieu de spécifier une valeur de données réelle pour un champ, vous pouvez appeler `SetFieldNull` pour spécifier la valeur null. Pour valider vos modifications, appelez `Update`.

> [!TIP]
> Pour sortir du mode `AddNew` ou `Edit`, appelez `Move` avec le *AFX_MOVE_REFRESH*de paramètres.

Comme condition préalable à l’appel de `Update`, le jeu d’enregistrements ne doit pas être vide et l’enregistrement actif ne doit pas avoir été supprimé. `IsBOF`, `IsEOF`et `IsDeleted` doivent tous retourner la valeur 0.

Lorsque vous appelez `Update` pour l’enregistrement modifié :

- Si votre pilote ODBC prend en charge la fonction API ODBC `::SQLSetPos`, MFC utilise la fonction pour mettre à jour l’enregistrement sur la source de données. Avec `::SQLSetPos`, le pilote compare votre tampon d’édition à l’enregistrement correspondant sur le serveur, en mettant à jour l’enregistrement sur le serveur si les deux sont différents. Avec `::SQLSetPos`, MFC peut mettre à jour un enregistrement plus efficacement, car il n’a pas besoin de construire et traiter une instruction SQL.

   \- ou -

- Si `::SQLSetPos` ne peut pas être utilisé, MFC effectue les opérations suivantes :

   1. Si aucune modification n’a été apportée, `Update` ne fait rien et retourne 0.

   1. En cas de modification, `Update` construit une instruction SQL **Update** . Les colonnes répertoriées dans l’instruction **Update** sont basées sur les données membres de champ qui ont changé.

   1. `Update` valide les modifications (exécute l’instruction **Update** ) et l’enregistrement est modifié sur la source de données, mais non validé si une transaction est en cours (consultez [transaction : exécution d’une transaction dans un Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md) pour plus d’informations sur la façon dont la transaction affecte la mise à jour). ODBC conserve une copie de l’enregistrement, qui change également.

   1. Contrairement au processus de `AddNew`, le processus de `Edit` ne restaure pas l’enregistrement stocké. L’enregistrement modifié reste en place en tant qu’enregistrement actif.

   > [!CAUTION]
   > Lorsque vous préparez la mise à jour d’un Recordset en appelant `Update`, veillez à ce que votre jeu d’enregistrements comprenne toutes les colonnes composant la clé primaire de la table (ou toutes les colonnes d’un index unique sur la table, ou suffisamment de colonnes pour identifier la ligne de façon unique). Dans certains cas, l’infrastructure peut utiliser uniquement les colonnes sélectionnées dans votre jeu d’enregistrements pour identifier l’enregistrement à mettre à jour dans votre table. Si vous ne disposez pas de toutes les colonnes nécessaires, plusieurs enregistrements peuvent être mis à jour dans la table. Dans ce cas, le Framework lève des exceptions lorsque vous appelez `Update`.

   > [!TIP]
   > Si vous appelez `AddNew` ou `Edit` après avoir appelé l’une ou l’autre des fonctions précédemment mais avant d’appeler `Update`, le tampon d’édition est actualisé avec l’enregistrement stocké, ce qui remplace l’enregistrement nouveau ou modifié en cours. Ce comportement vous permet d’abandonner une `AddNew` ou `Edit` et d’en commencer une nouvelle : Si vous déterminez que l’enregistrement en cours est défectueux, il vous suffit d’appeler `Edit` ou `AddNew`.

##  <a name="deleting-a-record"></a><a name="_core_deleting_a_record"></a>Suppression d’un enregistrement

La suppression d’un enregistrement d’un jeu d’enregistrements implique de faire défiler jusqu’à l’enregistrement et d’appeler la fonction membre [Delete](../../mfc/reference/crecordset-class.md#delete) du Recordset. Contrairement à `AddNew` et `Edit`, `Delete` ne requiert pas d’appel correspondant à `Update`.

Comme condition préalable à l’appel de `Delete`, le Recordset doit pouvoir être mis à jour et doit être sur un enregistrement. Les fonctions membres `CanUpdate`, `IsBOF`, `IsEOF`et `IsDeleted` vous permettent de déterminer ces conditions.

Quand vous appelez `Delete`:

- Si votre pilote ODBC prend en charge la fonction API ODBC `::SQLSetPos`, MFC utilise la fonction pour supprimer l’enregistrement sur la source de données. L’utilisation de `::SQLSetPos` est généralement plus efficace que l’utilisation de SQL.

   \- ou -

- Si `::SQLSetPos` ne peut pas être utilisé, MFC effectue les opérations suivantes :

   1. L’enregistrement actif dans le tampon d’édition n’est pas sauvegardé comme dans `AddNew` et `Edit`.

   1. `Delete` construit une instruction SQL **Delete** qui supprime l’enregistrement.

      L’enregistrement actif dans le tampon d’édition n’est pas stocké comme dans `AddNew` et `Edit`.

   1. `Delete` valide la suppression, exécute l’instruction **Delete** . L’enregistrement est marqué comme supprimé dans la source de données et, s’il s’agit d’un instantané, dans ODBC.

   1. Les valeurs de l’enregistrement supprimé se trouvent toujours dans les membres de données de champ de l’ensemble d’enregistrements, mais les membres de données de champ sont marqués comme null et la fonction membre `IsDeleted` du Recordset retourne une valeur différente de zéro.

   > [!NOTE]
   > Après la suppression d’un enregistrement, vous devez faire défiler vers un autre enregistrement pour recharger le tampon d’édition avec les données du nouvel enregistrement. L’appel de `Delete` à nouveau ou l’appel de `Edit`n’est pas une erreur.

Pour plus d’informations sur les instructions SQL utilisées dans les opérations de mise à jour, consultez [SQL](../../data/odbc/sql.md).

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : informations complémentaires sur les mises à jour (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)<br/>
[Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md)

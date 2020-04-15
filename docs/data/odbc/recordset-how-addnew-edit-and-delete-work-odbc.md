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
ms.openlocfilehash: 63718a6be3a9ce19ddbce923a84def21448c42a0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367003"
---
# <a name="recordset-how-addnew-edit-and-delete-work-odbc"></a>Recordset : fonctionnement d'AddNew, Edit et Delete (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Ce sujet explique `AddNew` `Edit`comment `Delete` le , , `CRecordset` et les fonctions des membres de la classe de travail. Sont abordés les sujets suivants :

- [Fonctionnement de l’ajout d’enregistrements](#_core_adding_a_record)

- [Visibilité des enregistrements ajoutés](#_core_visibility_of_added_records)

- [Fonctionnement des enregistrements d’édition](#_core_editing_an_existing_record)

- [Fonctionnement de la suppression des documents](#_core_deleting_a_record)

> [!NOTE]
> Cette rubrique s’applique aux objets dérivés de `CRecordset` où l’extraction de lignes en bloc n’a pas été implémentée. Si vous utilisez la ligne en vrac aller chercher, voir [Recordset: Fetching Records en vrac (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

En complément, vous voudrez peut-être lire [Record Field Exchange: How RFX Works](../../data/odbc/record-field-exchange-how-rfx-works.md), qui décrit le rôle correspondant de RFX dans les opérations de mise à jour.

## <a name="adding-a-record"></a><a name="_core_adding_a_record"></a>Ajout d’un enregistrement

L’ajout d’un nouvel enregistrement à un jeu d’enregistrement implique d’appeler la fonction de membre [AddNew](../../mfc/reference/crecordset-class.md#addnew) du recordet, d’établir les valeurs des membres des données sur le terrain du nouvel enregistrement et d’appeler la fonction membre [de la mise](../../mfc/reference/crecordset-class.md#update) à jour pour écrire l’enregistrement à la source de données.

Comme condition préalable `AddNew`à l’appel, le dossier ne doit pas avoir été ouvert comme lu seulement. Les `CanUpdate` `CanAppend` fonctions et les fonctions des membres vous permettent de déterminer ces conditions.

Lorsque vous `AddNew`appelez :

- L’enregistrement dans le tampon de modification est stocké, de sorte que son contenu peut être restauré si l’opération est annulée.

- Les membres des données sur le terrain sont signalés de sorte qu’il est possible de détecter les changements en eux plus tard. Les membres des données sur le terrain sont également marqués propres (inchangés) et réglés sur un Null.

Après votre `AddNew`appel, le tampon de modification représente un nouvel enregistrement vide, prêt à être rempli de valeurs. Pour ce faire, vous définissez manuellement les valeurs en leur assignant. Au lieu de spécifier une valeur `SetFieldNull` de données réelle pour un champ, vous pouvez appeler pour spécifier la valeur Null.

Pour valider vos `Update`modifications, vous appelez . Lorsque vous `Update` appelez pour le nouvel enregistrement:

- Si votre pilote ODBC prend en charge la `::SQLSetPos` fonction API ODBC, MFC utilise la fonction pour ajouter l’enregistrement sur la source de données. Avec `::SQLSetPos`, MFC peut ajouter un enregistrement plus efficacement parce qu’il n’a pas à construire et traiter une déclaration SQL.

- S’il `::SQLSetPos` n’est pas utilisé, MFC fait ce qui suit :

   1. Si aucun changement n’est détecté, `Update` ne fait rien et renvoie 0.

   1. S’il y `Update` a des changements, construit une déclaration SQL **INSERT.** Les colonnes représentées par tous les membres des données de champ sale sont répertoriées dans la déclaration **INSERT.** Pour forcer l’inclus dans une colonne, appelez la fonction membre [SetFieldDirty](../../mfc/reference/crecordset-class.md#setfielddirty) :

        ```cpp
        SetFieldDirty( &m_dataMember, TRUE );
        ```

   1. `Update`engage le nouvel enregistrement — la déclaration **INSERT** est exécutée et l’enregistrement est engagé à la table sur la source de données (et le jeu d’enregistrement, si ce n’est un instantané) à moins qu’une transaction soit en cours.

   1. L’enregistrement stocké est restauré dans le tampon de modification. Le dossier qui était `AddNew` à jour avant l’appel est à nouveau à jour, peu importe si la déclaration **INSERT** a été exécutée avec succès.

   > [!TIP]
   > Pour un contrôle complet d’un nouvel enregistrement, adoptez l’approche suivante : définissez les valeurs `SetFieldNull` de tous les champs qui auront des valeurs et fixez ensuite explicitement tous les champs qui resteront nuls en appelant avec un pointeur sur le terrain et le paramètre TRUE (la valeur). Si vous voulez vous assurer qu’un champ n’est pas écrit à la source de données, appelez `SetFieldDirty` avec un pointeur sur le terrain et le paramètre FALSE, et ne modifiez pas la valeur du champ. Pour déterminer si un champ est `IsFieldNullable`autorisé à être Null, appelez .

   > [!TIP]
   > Pour détecter quand les membres des données enregistrent changent de valeur, MFC utilise une valeur PSEUDO_NULL adaptée à chaque type de données que vous pouvez stocker dans un ensemble d’enregistrements. Si vous devez définir explicitement un champ à la valeur PSEUDO_NULL et que le `SetFieldNull`champ se trouve déjà être marqué Null, vous devez également appeler, en passant l’adresse du champ dans le premier paramètre et FALSE dans le deuxième paramètre.

## <a name="visibility-of-added-records"></a><a name="_core_visibility_of_added_records"></a>Visibilité des enregistrements ajoutés

Quand un enregistrement supplémentaire est-il visible à votre dossier ? Les enregistrements ajoutés apparaissent parfois et ne sont parfois pas visibles, selon deux choses :

- Ce dont votre chauffeur est capable.

- De quoi le cadre peut tirer profit.

Si votre pilote ODBC prend en charge la `::SQLSetPos` fonction API ODBC, MFC utilise la fonction pour ajouter des enregistrements. Avec `::SQLSetPos`, les enregistrements ajoutés sont visibles à n’importe quel recordet MFC updatable. Sans support pour la fonction, les enregistrements `Requery` ajoutés ne sont pas visibles et vous devez appeler pour les voir. L’utilisation `::SQLSetPos` est également plus efficace.

## <a name="editing-an-existing-record"></a><a name="_core_editing_an_existing_record"></a>Montage d’un disque existant

L’édition d’un enregistrement existant dans un jeu d’enregistrements implique de faire défiler l’enregistrement, d’appeler la fonction membre [Edit](../../mfc/reference/crecordset-class.md#edit) du recordet, d’établir les valeurs des membres des données de terrain du nouvel enregistrement et d’appeler la fonction membre [de la mise](../../mfc/reference/crecordset-class.md#update) à jour pour écrire l’enregistrement modifié à la source de données.

Comme condition préalable `Edit`à l’appel, le recordet doit être updatable et sur un dossier. Les `CanUpdate` `IsDeleted` fonctions et les fonctions des membres vous permettent de déterminer ces conditions. Le dossier actuel ne doit pas non plus avoir déjà été supprimé, et il doit y avoir des enregistrements dans le jeu d’enregistrement (les deux `IsBOF` et `IsEOF` le retour 0).

Lorsque vous `Edit`appelez, l’enregistrement dans le tampon de modification (l’enregistrement actuel) est stocké. Les valeurs de l’enregistrement stocké sont ensuite utilisées pour détecter si des champs ont changé.

Après votre `Edit`appel, le tampon de modification représente toujours l’enregistrement actuel, mais est maintenant prêt à accepter les modifications apportées aux membres des données sur le terrain. Pour modifier l’enregistrement, vous définissez manuellement les valeurs de tous les membres de données sur le terrain que vous souhaitez modifier. Au lieu de spécifier une valeur `SetFieldNull` de données réelle pour un champ, vous pouvez appeler pour spécifier la valeur Null. Pour valider vos `Update`modifications, appelez .

> [!TIP]
> Pour sortir `AddNew` ou `Edit` en `Move` mode, appelez avec le paramètre *AFX_MOVE_REFRESH*.

Comme condition préalable `Update`à l’appel, le dossier ne doit pas être vide et l’enregistrement actuel ne doit pas avoir été supprimé. `IsBOF`, `IsEOF`, `IsDeleted` et devrait tous retourner 0.

Lorsque vous `Update` appelez pour l’enregistrement édité:

- Si votre pilote ODBC prend en charge la `::SQLSetPos` fonction API ODBC, MFC utilise la fonction pour mettre à jour l’enregistrement sur la source de données. Avec `::SQLSetPos`, le pilote compare votre tampon de modification avec l’enregistrement correspondant sur le serveur, mise à jour de l’enregistrement sur le serveur si les deux sont différents. Avec `::SQLSetPos`, MFC peut mettre à jour un enregistrement plus efficacement parce qu’il n’a pas à construire et traiter une déclaration SQL.

   \- ou -

- S’il `::SQLSetPos` n’est pas utilisé, MFC fait ce qui suit :

   1. S’il n’y `Update` a eu aucun changement, ne fait rien et retourne 0.

   1. S’il y `Update` a des changements, construit une déclaration **DE MISE À JOUR** SQL. Les colonnes énumérées dans la déclaration **UPDATE** sont basées sur les données sur le terrain des membres qui ont changé.

   1. `Update`s’engage dans les modifications — exécute l’énoncé **UPDATE** — et l’enregistrement est modifié sur la source de données, mais pas validé si une transaction est en cours (voir [Transaction : Effectuer une transaction dans un Dossier (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md) pour obtenir de l’information sur l’incidence de la transaction sur la mise à jour). ODBC conserve une copie de l’enregistrement, qui change également.

   1. Contrairement au `AddNew`processus `Edit` pour , le processus ne restaure pas l’enregistrement stocké. L’enregistrement édité reste en place comme l’enregistrement actuel.

   > [!CAUTION]
   > Lorsque vous vous préparez à `Update`mettre à jour un ensemble d’enregistrements en appelant, veillez à ce que votre jeu d’enregistrement comporte toutes les colonnes constituant la clé principale de la table (ou toutes les colonnes de tout index unique sur la table, ou suffisamment de colonnes pour identifier uniquement la ligne). Dans certains cas, le cadre ne peut utiliser que les colonnes sélectionnées dans votre dossier pour identifier l’enregistrement dans votre table à mettre à jour. Sans toutes les colonnes nécessaires, plusieurs enregistrements peuvent être mis à jour dans le tableau. Dans ce cas, le cadre fait `Update`des exceptions lorsque vous appelez .

   > [!TIP]
   > Si vous `AddNew` `Edit` appelez ou après avoir appelé `Update`l’une ou l’autre fonction auparavant, mais avant d’appeler, le tampon de modification est actualisé avec l’enregistrement stocké, remplaçant le nouvel enregistrement ou édité en cours. Ce comportement vous donne un `AddNew` `Edit` moyen d’avorter un ou et commencer un nouveau: si `Edit` `AddNew` vous déterminez que l’enregistrement en cours est défectueux, il suffit d’appeler ou à nouveau.

## <a name="deleting-a-record"></a><a name="_core_deleting_a_record"></a>Suppression d’un record

La suppression d’un enregistrement à partir d’un enregistrement implique de faire défiler vers l’enregistrement et d’appeler la fonction de membre [Supprimer](../../mfc/reference/crecordset-class.md#delete) du recordet. Contrairement `AddNew` `Edit`et `Delete` , ne nécessite `Update`pas un appel correspondant à .

Comme condition préalable `Delete`à l’appel, le recordet doit être updatable et il doit être sur un dossier. Les `CanUpdate` `IsBOF`fonctions , , `IsEOF`et `IsDeleted` membres vous permettent de déterminer ces conditions.

Lorsque vous `Delete`appelez :

- Si votre pilote ODBC prend en charge la `::SQLSetPos` fonction API ODBC, MFC utilise la fonction pour supprimer l’enregistrement sur la source de données. L’utilisation `::SQLSetPos` est généralement plus efficace que l’utilisation de SQL.

   \- ou -

- S’il `::SQLSetPos` n’est pas utilisé, MFC fait ce qui suit :

   1. Le dossier actuel dans le tampon de `AddNew` `Edit`modification n’est pas sauvegardé comme dans et .

   1. `Delete`construit une déclaration SQL **DELETE** qui supprime l’enregistrement.

      L’enregistrement actuel dans le tampon `AddNew` de `Edit`modification n’est pas stocké dans et .

   1. `Delete`commits la suppression — exécute la déclaration **DELETE.** L’enregistrement est marqué supprimé sur la source de données et, si l’enregistrement est un instantané, dans ODBC.

   1. Les valeurs de l’enregistrement supprimé sont toujours dans les données de terrain des membres de l’enregistrement, mais les membres des données sur le terrain sont marqués Null et la fonction membre du `IsDeleted` recordet retourne une valeur non zéro.

   > [!NOTE]
   > Après la suppression d’un enregistrement, vous devez faire défiler vers un autre enregistrement pour remplir le tampon de modification avec les données du nouvel enregistrement. C’est une `Delete` erreur d’appeler à nouveau ou d’appeler `Edit`.

Pour plus d’informations sur les déclarations SQL utilisées dans les opérations de mise à jour, voir [SQL](../../data/odbc/sql.md).

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : informations complémentaires sur les mises à jour (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)<br/>
[Échange de terrain record (RFX)](../../data/odbc/record-field-exchange-rfx.md)

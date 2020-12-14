---
description: 'En savoir plus sur : Recordset : mode de mise à jour des enregistrements par les recordsets (ODBC)'
title: 'Recordset : modification des enregistrements par les recordsets (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- records, updating
- ODBC recordsets, updating
- recordsets, editing records
- updating recordsets
- recordsets, updating
ms.assetid: 5ceecc06-7a86-43b1-93db-a54fb1e717c7
ms.openlocfilehash: c5304bd30093a203efbd9ee4d02d07b2d35b4b18
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304504"
---
# <a name="recordset-how-recordsets-update-records-odbc"></a>Recordset : modification des enregistrements par les recordsets (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Outre leur capacité à sélectionner des enregistrements à partir d’une source de données, les recordsets peuvent (éventuellement) mettre à jour ou supprimer les enregistrements sélectionnés ou ajouter de nouveaux enregistrements. Trois facteurs déterminent la possibilité de mise à jour d’un jeu d’enregistrements : si la source de données connectée est modifiable, les options que vous spécifiez lorsque vous créez un objet Recordset et le SQL qui est créé.

> [!NOTE]
> Le SQL sur lequel votre `CRecordset` objet est basé peut affecter la mise à jour de votre jeu d’enregistrements. Par exemple, si votre SQL contient une clause Join ou **Group by** , MFC affecte la valeur false à la mise à jour.

> [!NOTE]
> Cette rubrique s’applique aux objets dérivés de `CRecordset` où l’extraction de lignes en bloc n’a pas été implémentée. Si vous utilisez l’extraction de lignes en bloc, consultez [Recordset : extraction globale d’enregistrements (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Cette rubrique répond aux questions suivantes :

- [Votre rôle dans la mise à jour](#_core_your_role_in_recordset_updating) de l’ensemble d’enregistrements et ce que l’infrastructure fait pour vous.

- [Le jeu d’enregistrements comme un tampon d’édition](#_core_the_edit_buffer) et les [différences entre les feuilles de réponse dynamiques et les instantanés](#_core_dynasets_and_snapshots).

[Recordset : la manière dont AddNew, Edit et Delete Work (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md) décrivent les actions de ces fonctions du point de vue du Recordset.

[Recordset : en savoir plus sur les mises à jour (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md) termine la mise à jour de l’ensemble d’enregistrements en expliquant comment les transactions affectent les mises à jour, la fermeture d’un jeu d’enregistrements ou le défilement affecte les mises à jour en cours et la façon dont vos mises à jour interagissent avec les mises à jour d’autres utilisateurs.

## <a name="your-role-in-recordset-updating"></a><a name="_core_your_role_in_recordset_updating"></a> Votre rôle dans la mise à jour de l’ensemble d’enregistrements

Le tableau suivant montre votre rôle dans l’utilisation des recordsets pour ajouter, modifier ou supprimer des enregistrements, ainsi que ce que fait l’infrastructure pour vous.

### <a name="recordset-updating-you-and-the-framework"></a>Mise à jour de l’ensemble d’enregistrements : vous et le Framework

|Vous|L'infrastructure|
|---------|-------------------|
|Déterminez si la source de données peut être mise à jour (ou peut être ajoutée).|Fournit des fonctions membres [CDatabase](../../mfc/reference/cdatabase-class.md) pour tester la mise à jour ou l’ajout de la source de données.|
|Ouvrez un jeu d’enregistrements pouvant être mis à jour (de n’importe quel type).||
|Déterminez si le jeu d’enregistrements peut être mis à jour en appelant des `CRecordset` fonctions de mise à jour telles que `CanUpdate` ou `CanAppend` .||
|Appelez les fonctions membres du Recordset pour ajouter, modifier et supprimer des enregistrements.|Gère le mécanisme d’échange de données entre votre objet Recordset et la source de données.|
|Si vous le souhaitez, utilisez des transactions pour contrôler le processus de mise à jour.|Fournit des `CDatabase` fonctions membres pour prendre en charge les transactions.|

Pour plus d’informations sur les transactions, consultez [transaction (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="the-edit-buffer"></a><a name="_core_the_edit_buffer"></a> La mémoire tampon d’édition

Pris collectivement, les données membres de champ d’un jeu d’enregistrements servent de tampon de modification qui contient un enregistrement, l’enregistrement en cours. Les opérations de mise à jour utilisent cette mémoire tampon pour fonctionner sur l’enregistrement en cours.

- Lorsque vous ajoutez un enregistrement, le tampon d’édition est utilisé pour créer un nouvel enregistrement. Lorsque vous avez terminé d’ajouter l’enregistrement, l’enregistrement qui était précédemment en cours redevient à jour.

- Lorsque vous mettez à jour (modifier) un enregistrement, le tampon d’édition est utilisé pour définir les membres de données de champ du Recordset sur de nouvelles valeurs. Une fois la mise à jour terminée, l’enregistrement mis à jour est toujours à jour.

Lorsque vous appelez [AddNew](../../mfc/reference/crecordset-class.md#addnew) ou [Edit](../../mfc/reference/crecordset-class.md#edit), l’enregistrement actif est stocké afin qu’il puisse être restauré plus tard en fonction des besoins. Lorsque vous appelez [Delete](../../mfc/reference/crecordset-class.md#delete), l’enregistrement actif n’est pas stocké, mais est marqué comme Deleted et vous devez faire défiler jusqu’à un autre enregistrement.

> [!NOTE]
> Le tampon d’édition ne joue aucun rôle dans la suppression des enregistrements. Lorsque vous supprimez l’enregistrement actif, l’enregistrement est marqué comme supprimé et le Recordset n’est pas sur un enregistrement tant que vous n’avez pas fait défiler vers un autre enregistrement.

## <a name="dynasets-and-snapshots"></a><a name="_core_dynasets_and_snapshots"></a> Feuilles de réponse dynamiques et instantanés

Les [feuilles de réponse dynamiques](../../data/odbc/dynaset.md) actualisent le contenu d’un enregistrement lorsque vous faites défiler l’enregistrement. Les [instantanés](../../data/odbc/snapshot.md) sont des représentations statiques des enregistrements, de sorte que le contenu d’un enregistrement n’est pas actualisé, sauf si vous appelez [Requery](../../mfc/reference/crecordset-class.md#requery). Pour utiliser toutes les fonctionnalités des feuilles de réponse dynamiques, vous devez travailler avec un pilote ODBC conforme au niveau de prise en charge correct de l’API ODBC. Pour plus d’informations, consultez [ODBC](../../data/odbc/odbc-basics.md) et [Dynaset](../../data/odbc/dynaset.md).

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : fonctionnement d’AddNew, Edit et Delete (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)

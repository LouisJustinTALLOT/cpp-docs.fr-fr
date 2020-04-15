---
title: 'Recordset : modification des enregistrements par les recordsets (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- records, updating
- ODBC recordsets, updating
- recordsets, editing records
- updating recordsets
- recordsets, updating
ms.assetid: 5ceecc06-7a86-43b1-93db-a54fb1e717c7
ms.openlocfilehash: 03fb696c1fadd834962d37c8e75b5f8910af819e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366980"
---
# <a name="recordset-how-recordsets-update-records-odbc"></a>Recordset : modification des enregistrements par les recordsets (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Outre leur capacité à sélectionner des enregistrements à partir d’une source de données, les enregistrements peuvent (optionnellement) mettre à jour ou supprimer les enregistrements sélectionnés ou ajouter de nouveaux enregistrements. Trois facteurs déterminent la mise à jour d’un jeu d’enregistrement : si la source de données connectée est mise à jour, les options que vous spécifiez lorsque vous créez un objet de l’ensemble d’enregistrements et la SQL qui est créée.

> [!NOTE]
> Le SQL sur `CRecordset` lequel votre objet est basé peut affecter la mise à jour de votre dossier. Par exemple, si votre SQL contient une clause de jointure ou de **GROUPE BY,** MFC définit la mise à jour à FALSE.

> [!NOTE]
> Cette rubrique s’applique aux objets dérivés de `CRecordset` où l’extraction de lignes en bloc n’a pas été implémentée. Si vous utilisez la ligne en vrac aller chercher, voir [Recordset: Fetching Records en vrac (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Cette rubrique répond aux questions suivantes :

- [Votre rôle dans la mise à jour de l’enregistrement](#_core_your_role_in_recordset_updating) et ce que le cadre fait pour vous.

- [Le livre d’enregistrement comme tampon de modification](#_core_the_edit_buffer) et les différences entre les [dynasets et les instantanés](#_core_dynasets_and_snapshots).

[Recordset: How AddNew, Edit, and Delete Work (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md) décrit les actions de ces fonctions du point de vue de l’ensemble d’enregistrements.

[Recordset: More About Updates (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md) complète l’histoire de mise à jour de l’ensemble d’enregistrements en expliquant comment les transactions affectent les mises à jour, comment la fermeture d’un ensemble d’enregistrements ou le défilement affecte les mises à jour en cours, et comment vos mises à jour interagissent avec les mises à jour d’autres utilisateurs.

## <a name="your-role-in-recordset-updating"></a><a name="_core_your_role_in_recordset_updating"></a>Votre rôle dans la mise à jour de Recordset

Le tableau suivant montre votre rôle dans l’utilisation d’enregistrements pour ajouter, modifier ou supprimer des enregistrements, ainsi que ce que le cadre fait pour vous.

### <a name="recordset-updating-you-and-the-framework"></a>Mise à jour de records : vous et le cadre

|Vous|L'infrastructure|
|---------|-------------------|
|Déterminez si la source de données est mise à jour (ou appendible).|Fournit des fonctions de membre [CDatabase](../../mfc/reference/cdatabase-class.md) pour tester la mise à jour ou l’appendabilité de la source de données.|
|Ouvrez un recordet updatable (de tout type).||
|Déterminez si le recordet est `CRecordset` updatable `CanUpdate` en `CanAppend`appelant des fonctions de mise à jour telles que ou .||
|Appelez les fonctions des membres de l’enregistrement pour ajouter, modifier et supprimer des enregistrements.|Gère la mécanique d’échange de données entre votre objet de recordet et la source de données.|
|Optionnellement, utilisez les transactions pour contrôler le processus de mise à jour.|Fournit `CDatabase` des fonctions de membre pour soutenir les transactions.|

Pour plus d’informations sur les transactions, voir [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="the-edit-buffer"></a><a name="_core_the_edit_buffer"></a>Le tampon d’édition

Prises collectivement, les membres des données sur le terrain d’un ensemble d’enregistrements servent de tampon de modification qui contient un enregistrement — le dossier actuel. Les opérations de mise à jour utilisent ce tampon pour fonctionner sur le dossier actuel.

- Lorsque vous ajoutez un enregistrement, le tampon de modification est utilisé pour construire un nouvel enregistrement. Lorsque vous avez fini d’ajouter l’enregistrement, l’enregistrement qui était auparavant à jour redevient à jour.

- Lorsque vous mettez à jour (éditez) un enregistrement, le tampon de modification est utilisé pour définir les données de champ des membres de l’ensemble d’enregistrements à de nouvelles valeurs. Lorsque vous avez terminé la mise à jour, l’enregistrement mis à jour est toujours à jour.

Lorsque vous appelez [AddNew](../../mfc/reference/crecordset-class.md#addnew) ou [Edit](../../mfc/reference/crecordset-class.md#edit), l’enregistrement actuel est stocké afin qu’il puisse être restauré plus tard au besoin. Lorsque vous appelez [Supprimer](../../mfc/reference/crecordset-class.md#delete), l’enregistrement actuel n’est pas stocké mais est marqué comme supprimé et vous devez faire défiler vers un autre enregistrement.

> [!NOTE]
> Le tampon de modification ne joue aucun rôle dans la suppression des dossiers. Lorsque vous supprimez l’enregistrement actuel, l’enregistrement est marqué comme supprimé, et le jeu d’enregistrement n’est « pas sur un enregistrement » jusqu’à ce que vous faites défiler vers un autre enregistrement.

## <a name="dynasets-and-snapshots"></a><a name="_core_dynasets_and_snapshots"></a>Dynasets et instantanés

[Dynasets](../../data/odbc/dynaset.md) actualise le contenu d’un enregistrement lorsque vous faites défiler vers l’enregistrement. [Les instantanés](../../data/odbc/snapshot.md) sont des représentations statiques des enregistrements, de sorte que le contenu d’un enregistrement ne sont pas actualisé à moins que vous n’appeliez [Requery](../../mfc/reference/crecordset-class.md#requery). Pour utiliser toutes les fonctionnalités des dynasets, vous devez travailler avec un pilote ODBC qui se conforme au niveau correct du support API ODBC. Pour plus d’informations, voir [ODBC](../../data/odbc/odbc-basics.md) et [Dynaset](../../data/odbc/dynaset.md).

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : fonctionnement d'AddNew, Edit et Delete (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)

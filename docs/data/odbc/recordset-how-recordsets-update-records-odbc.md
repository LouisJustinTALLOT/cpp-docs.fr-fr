---
title: 'Recordset : Modification des jeux d’enregistrements enregistrements (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- records, updating
- ODBC recordsets, updating
- recordsets, editing records
- updating recordsets
- recordsets, updating
ms.assetid: 5ceecc06-7a86-43b1-93db-a54fb1e717c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bafc3a47b02fc73a3252d0a7830fc989015a0628
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055045"
---
# <a name="recordset-how-recordsets-update-records-odbc"></a>Recordset : modification des enregistrements par les recordsets (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

En dehors de leur capacité à sélectionner des enregistrements à partir d’une source de données, les jeux d’enregistrements peut (éventuellement) mettre à jour ou supprimer les enregistrements sélectionnés ou ajouter de nouveaux enregistrements. Trois facteurs déterminent la mise à jour un jeu d’enregistrements : indique si la source de données connectée est modifiable, les options que vous spécifiez lorsque vous créez un objet recordset et l’instruction SQL qui est créé.

> [!NOTE]
>  Le code SQL sur lequel votre `CRecordset` objet repose peut affecter la mise à jour votre jeu d’enregistrements. Par exemple, si votre SQL contient une jointure ou un **GROUP BY** clause, MFC définit la mise à jour sur FALSE.

> [!NOTE]
>  Cette rubrique s’applique aux objets dérivés de `CRecordset` dans les lignes en bloc l’extraction n’a pas été implémentée. Si vous utilisez l’extraction de lignes en bloc, consultez [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Cette rubrique explique :

- [Votre rôle dans la mise à jour du jeu d’enregistrements](#_core_your_role_in_recordset_updating) et ce que l’infrastructure effectue pour vous.

- [Le jeu d’enregistrements en tant que tampon d’édition](#_core_the_edit_buffer) et [différences entre les feuilles de réponse dynamiques et les instantanés](#_core_dynasets_and_snapshots).

[Recordset : Comment AddNew, Edit et Delete (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md) décrit les actions de ces fonctions à partir du point de vue de l’objet recordset.

[Recordset : Informations complémentaires sur les mises à jour (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md) conclut la mise à jour des recordsets en expliquant comment les transactions affectent les mises à jour, comment la fermeture d’un recordset influe sur les mises à jour en cours d’exécution, et comment vos mises à jour interagissent avec les mises à jour des autres utilisateurs.

##  <a name="_core_your_role_in_recordset_updating"></a> Votre rôle dans la mise à jour du jeu d’enregistrements

Le tableau suivant illustre votre rôle dans l’aide de jeux d’enregistrements à ajouter, modifier ou supprimer des enregistrements, ainsi que ce que l’infrastructure effectue pour vous.

### <a name="recordset-updating-you-and-the-framework"></a>La mise à jour du jeu d’enregistrements : L’infrastructure et vous

|Vous|L'infrastructure|
|---------|-------------------|
|Déterminer si la source de données est modifiable (ou modifiable).|Fournitures [CDatabase](../../mfc/reference/cdatabase-class.md) fonctions membres pour tester le caractère modifiable ou extensible de la source de données.|
|Ouvrez un recordset modifiable (n’importe quel type).||
|Déterminer si le jeu d’enregistrements est modifiable en appelant `CRecordset` mettre à jour des fonctions comme `CanUpdate` ou `CanAppend`.||
|Appeler des fonctions membres à ajouter, modifier et supprimer des enregistrements recordset.|Gère les mécanismes d’échange de données entre votre objet recordset et la source de données.|
|Si vous le souhaitez, utiliser des transactions pour contrôler le processus de mise à jour.|Fournitures `CDatabase` fonctions membres pour prendre en charge des transactions.|

Pour plus d’informations sur les transactions, consultez [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="_core_the_edit_buffer"></a> La mémoire tampon d’édition

Pris collectivement, les membres de données de champ d’un recordset font Office de tampon d’édition qui contient un enregistrement, l’enregistrement actif. Les opérations de mise à jour utilisent cette mémoire tampon sur l’enregistrement en cours.

- Lorsque vous ajoutez un enregistrement, la mémoire tampon d’édition est utilisé pour générer un nouvel enregistrement. Lorsque vous avez ajouté l’enregistrement, l’enregistrement qui était précédemment actif redevient actif.

- Lorsque vous mettez à jour mémoire tampon (modifier) un enregistrement, la modification est utilisé pour définir les membres de données de champ de l’objet recordset avec de nouvelles valeurs. Lorsque vous avez terminé la mise à jour, l’enregistrement mis à jour est toujours en cours.

Lorsque vous appelez [AddNew](../../mfc/reference/crecordset-class.md#addnew) ou [modifier](../../mfc/reference/crecordset-class.md#edit), l’enregistrement actif est stocké, afin de restaurer ultérieurement si nécessaire. Lorsque vous appelez [supprimer](../../mfc/reference/crecordset-class.md#delete), l’enregistrement en cours n’est pas stocké, mais est marquée comme supprimée et vous devez accéder à un autre enregistrement.

> [!NOTE]
>  La mémoire tampon d’édition ne joue aucun rôle dans la suppression de l’enregistrement. Lorsque vous supprimez l’enregistrement en cours, l’enregistrement est marqué comme supprimé, et le jeu d’enregistrements est « pas sur un enregistrement » jusqu'à ce que vous faites défiler vers un autre enregistrement.

##  <a name="_core_dynasets_and_snapshots"></a> Les instantanés et les feuilles de réponse dynamiques

[Feuilles de réponse dynamiques](../../data/odbc/dynaset.md) actualiser le contenu d’un enregistrement que vous accédez à l’enregistrement. [Captures instantanées](../../data/odbc/snapshot.md) sont des représentations statiques des enregistrements, donc le contenu d’un enregistrement n’est pas actualisés, sauf si vous appelez [Requery](../../mfc/reference/crecordset-class.md#requery). Pour utiliser toutes les fonctionnalités de feuilles de réponse dynamiques, vous devez travailler avec un pilote ODBC qui est conforme au niveau correct de prise en charge de l’API ODBC. Pour plus d’informations, consultez [ODBC](../../data/odbc/odbc-basics.md) et [Dynaset](../../data/odbc/dynaset.md).

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : fonctionnement d’AddNew, Edit et Delete (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)
---
title: 'Transaction : répercussions des transactions sur les mises à jour (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
- ODBC recordsets, transactions
- transactions, rolling back
- CommitTrans method
- Rollback method, ODBC transactions
ms.assetid: 9e00bbf4-e9fb-4332-87fc-ec8ac61b3f68
ms.openlocfilehash: 8a87176ecb20beaf46583e1190b0ad458d508b31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376420"
---
# <a name="transaction-how-transactions-affect-updates-odbc"></a>Transaction : répercussions des transactions sur les mises à jour (ODBC)

Les mises à jour de la source de [données](../../data/odbc/data-source-odbc.md) sont gérées pendant les transactions par l’utilisation d’un tampon de modification (la même méthode utilisée en dehors des transactions). Les données sur le terrain des membres d’un ensemble d’enregistrements servent collectivement de tampon `AddNew` `Edit`de modification qui contient l’enregistrement actuel, que le dossier soutient temporairement au cours d’un ou . Au `Delete` cours d’une opération, le dossier actuel n’est pas sauvegardé dans le cadre d’une transaction. Pour plus d’informations sur le tampon de modification et comment les mises à jour stockent l’enregistrement actuel, voir [Recordset: How Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

> [!NOTE]
> Si vous avez implémenté la `AddNew` `Edit`ligne `Delete`en vrac aller chercher, vous ne pouvez pas appeler , , ou . Vous devez plutôt écrire vos propres fonctions pour effectuer des mises à jour de la source de données. Pour plus d’informations sur la ligne en vrac aller chercher, voir [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Pendant les `AddNew` `Edit`transactions, `Delete` , et les opérations peuvent être engagées ou annulées. Les effets `CommitTrans` `Rollback` de l’enregistrement actuel et pourraient ne pas être restaurés dans le tampon de modification. Pour s’assurer que le dossier actuel est correctement restauré, il est `CDatabase` important de comprendre `CRecordset`comment le fonctionnement et `Rollback` le `CommitTrans` membre du travail avec les fonctions de mise à jour de .

## <a name="how-committrans-affects-updates"></a><a name="_core_how_committrans_affects_updates"></a>Comment CommitTrans affecte les mises à jour

Le tableau suivant explique `CommitTrans` les effets des transactions.

### <a name="how-committrans-affects-updates"></a>Comment CommitTrans affecte les mises à jour

|Opération|État de la source de données|
|---------------|---------------------------|
|`AddNew`et `Update`, et puis`CommitTrans`|De nouveaux dossiers sont ajoutés à la source de données.|
|`AddNew`(sans `Update`), et puis`CommitTrans`|Un nouvel album est perdu. Enregistrement non ajouté à la source de données.|
|`Edit`et `Update`, et puis`CommitTrans`|Modifications validées par la source de données.|
|`Edit`(sans `Update`), et puis`CommitTrans`|Les modifications à l’enregistrement sont perdues. L’enregistrement reste inchangé sur la source de données.|
|`Delete`Puis`CommitTrans`|Enregistrements supprimés de la source de données.|

## <a name="how-rollback-affects-transactions"></a><a name="_core_how_rollback_affects_updates"></a>Comment la réduction affecte les transactions

Le tableau suivant explique `Rollback` les effets des transactions.

### <a name="how-rollback-affects-transactions"></a>Comment la réduction affecte les transactions

|Opération|État du record actuel|Vous devez également|État de la source de données|
|---------------|------------------------------|-------------------|---------------------------|
|`AddNew`et `Update`, puis`Rollback`|Le contenu de l’enregistrement actuel est stocké temporairement pour faire place à un nouvel enregistrement. Un nouvel enregistrement est entré dans le tampon de modification. Après `Update` est appelé, l’enregistrement actuel est restauré dans le tampon de modification.||L’ajout à `Update` la source de données effectuée par est inversé.|
|`AddNew`(sans `Update`), puis`Rollback`|Le contenu de l’enregistrement actuel est stocké temporairement pour faire place à un nouvel enregistrement. Edit buffer contient un nouvel enregistrement.|Appelez `AddNew` à nouveau pour restaurer le tampon de modification à un vide, nouvel enregistrement. Ou `Move`appelez (0) pour restaurer les anciennes valeurs dans le tampon de modification.|Parce `Update` qu’on ne l’a pas appelé, aucune modification n’a été apportée à la source de données.|
|`Edit`et `Update`, puis`Rollback`|Une version inédite de l’enregistrement actuel est stockée temporairement. Les modifications sont apportées au contenu du tampon de modification. Après `Update` est appelé, la version non éditée de l’enregistrement est toujours temporairement stocké.|*Dynaset*: Faites défiler l’enregistrement actuel puis revenez pour restaurer la version inédite de l’enregistrement dans le tampon de modification.<br /><br /> *Instantané*: `Requery` Appelez pour actualiser le jeu d’enregistrement à partir de la source de données.|Les modifications apportées `Update` à la source de données par sont inversées.|
|`Edit`(sans `Update`), puis`Rollback`|Une version inédite de l’enregistrement actuel est stockée temporairement. Les modifications sont apportées au contenu du tampon de modification.|Appelez `Edit` à nouveau pour restaurer la version inédite de l’enregistrement dans le tampon de modification.|Parce `Update` qu’on ne l’a pas appelé, aucune modification n’a été apportée à la source de données.|
|`Delete`Puis`Rollback`|Le contenu de l’enregistrement actuel est supprimé.|Appelez `Requery` pour restaurer le contenu de l’enregistrement actuel à partir de la source de données.|La suppression des données provenant de la source de données est inversée.|

## <a name="see-also"></a>Voir aussi

[Transaction (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[Transaction : exécution d’une transaction dans un recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)<br/>
[Classe CDatabase](../../mfc/reference/cdatabase-class.md)<br/>
[Classe CRecordset](../../mfc/reference/crecordset-class.md)

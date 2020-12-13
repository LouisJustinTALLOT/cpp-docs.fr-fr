---
description: 'En savoir plus sur : transaction : répercussions des transactions sur les mises à jour (ODBC)'
title: 'Transaction : répercussions des transactions sur les mises à jour (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
- ODBC recordsets, transactions
- transactions, rolling back
- CommitTrans method
- Rollback method, ODBC transactions
ms.assetid: 9e00bbf4-e9fb-4332-87fc-ec8ac61b3f68
ms.openlocfilehash: 56435d477ab11fe057ec20610a35e75d84cf7340
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333896"
---
# <a name="transaction-how-transactions-affect-updates-odbc"></a>Transaction : répercussions des transactions sur les mises à jour (ODBC)

Les mises à jour de la [source de données](../../data/odbc/data-source-odbc.md) sont gérées pendant les transactions à l’aide d’un tampon d’édition (méthode identique à celle utilisée en dehors des transactions). Les données membres de champ d’un jeu d’enregistrements servent collectivement de tampon de modification contenant l’enregistrement actif, que le Recordset sauvegarde temporairement pendant un `AddNew` ou un `Edit` . Pendant une `Delete` opération, l’enregistrement actif n’est pas sauvegardé dans une transaction. Pour plus d’informations sur la mémoire tampon d’édition et sur la manière dont les mises à jour stockent l’enregistrement actif, consultez [Recordset : modification des enregistrements par les recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

> [!NOTE]
> Si vous avez implémenté l’extraction de lignes en bloc, vous ne pouvez pas appeler `AddNew` , `Edit` ou `Delete` . Au lieu de cela, vous devez écrire vos propres fonctions pour effectuer des mises à jour de la source de données. Pour plus d’informations sur l’extraction de lignes en bloc, consultez [Recordset : extraction globale d’enregistrements (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Pendant les transactions `AddNew` , `Edit` les opérations,, et `Delete` peuvent être validées ou restaurées. Les effets de `CommitTrans` et `Rollback` peuvent entraîner la non-restauration de l’enregistrement actuel dans le tampon d’édition. Pour vous assurer que l’enregistrement actif est correctement restauré, il est important de comprendre comment les `CommitTrans` `Rollback` fonctions membres et de `CDatabase` fonctionnent avec les fonctions de mise à jour de `CRecordset` .

## <a name="how-committrans-affects-updates"></a><a name="_core_how_committrans_affects_updates"></a> Impact de CommitTrans sur les mises à jour

Le tableau suivant décrit les effets de `CommitTrans` sur les transactions.

### <a name="how-committrans-affects-updates"></a>Impact de CommitTrans sur les mises à jour

|Opération|État de la source de données|
|---------------|---------------------------|
|`AddNew` et `Update` , puis `CommitTrans`|Un nouvel enregistrement est ajouté à la source de données.|
|`AddNew` (sans `Update` ), puis `CommitTrans`|Un nouvel enregistrement est perdu. Enregistrement non ajouté à la source de données.|
|`Edit` et `Update` , puis `CommitTrans`|Modifications validées dans la source de données.|
|`Edit` (sans `Update` ), puis `CommitTrans`|Les modifications apportées à l’enregistrement sont perdues. L’enregistrement reste inchangé sur la source de données.|
|`Delete` Cliquez `CommitTrans`|Enregistrements supprimés de la source de données.|

## <a name="how-rollback-affects-transactions"></a><a name="_core_how_rollback_affects_updates"></a> Impact de la restauration sur les transactions

Le tableau suivant décrit les effets de `Rollback` sur les transactions.

### <a name="how-rollback-affects-transactions"></a>Impact de la restauration sur les transactions

|Opération|État de l’enregistrement actuel|Vous devez également|État de la source de données|
|---------------|------------------------------|-------------------|---------------------------|
|`AddNew` puis `Update` , `Rollback`|Le contenu de l’enregistrement actif est stocké temporairement pour libérer de l’espace pour le nouvel enregistrement. Un nouvel enregistrement est entré dans le tampon de modification. Après `Update` l’appel de, l’enregistrement actif est restauré dans la mémoire tampon d’édition.||L’ajout à la source de données effectuée par `Update` est inversé.|
|`AddNew` (sans `Update` ), puis `Rollback`|Le contenu de l’enregistrement actif est stocké temporairement pour libérer de l’espace pour le nouvel enregistrement. La mémoire tampon de modification contient un nouvel enregistrement.|Rappel `AddNew` pour restaurer la mémoire tampon d’édition dans un nouvel enregistrement vide. Ou appelez `Move` (0) pour restaurer les anciennes valeurs dans le tampon d’édition.|Étant donné que `Update` n’a pas été appelé, aucune modification n’a été apportée à la source de données.|
|`Edit` puis `Update` , `Rollback`|Une version non modifiée de l’enregistrement en cours est stockée temporairement. Les modifications sont apportées au contenu de la mémoire tampon d’édition. Une fois que `Update` est appelé, la version non modifiée de l’enregistrement est toujours stockée temporairement.|*Dynaset*: permet de faire défiler l’enregistrement actif, puis de revenir à la version non modifiée de l’enregistrement dans le tampon d’édition.<br /><br /> *Instantané*: appelez `Requery` pour actualiser l’ensemble d’enregistrements à partir de la source de données.|Les modifications apportées à la source de données par `Update` sont inversées.|
|`Edit` (sans `Update` ), puis `Rollback`|Une version non modifiée de l’enregistrement en cours est stockée temporairement. Les modifications sont apportées au contenu de la mémoire tampon d’édition.|Appelez à `Edit` nouveau pour restaurer la version non modifiée de l’enregistrement dans le tampon de modification.|Étant donné que `Update` n’a pas été appelé, aucune modification n’a été apportée à la source de données.|
|`Delete` Cliquez `Rollback`|Le contenu de l’enregistrement en cours est supprimé.|Appelez `Requery` pour restaurer le contenu de l’enregistrement en cours à partir de la source de données.|La suppression des données de la source de données est inversée.|

## <a name="see-also"></a>Voir aussi

[Transaction (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[Transaction : exécution d’une transaction dans un Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)<br/>
[CDatabase, classe](../../mfc/reference/cdatabase-class.md)<br/>
[Classe CRecordset](../../mfc/reference/crecordset-class.md)

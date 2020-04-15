---
title: "Recordset : verrouillage d'enregistrements (ODBC)"
ms.date: 11/04/2016
helpviewer_keywords:
- locks [C++], recordsets
- optimistic locking
- pessimistic locking in ODBC
- recordsets [C++], locking records
- optimistic locking, ODBC
- ODBC recordsets [C++], locking records
- data [C++], locking
ms.assetid: 8fe8fcfe-b55a-41a8-9136-94a7cd1e4806
ms.openlocfilehash: abd5f817ad321241df2d8565bd6bf346c0792088
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366966"
---
# <a name="recordset-locking-records-odbc"></a>Recordset : verrouillage d'enregistrements (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Cette rubrique répond aux questions suivantes :

- [Les types de verrouillage des dossiers disponibles](#_core_record.2d.locking_modes).

- [Comment verrouiller les enregistrements dans votre dossier lors des mises à jour](#_core_locking_records_in_your_recordset).

Lorsque vous utilisez un jeu d’enregistrement pour mettre à jour un enregistrement sur la source de données, votre application peut verrouiller l’enregistrement afin qu’aucun autre utilisateur ne puisse mettre à jour l’enregistrement en même temps. L’état d’un enregistrement mis à jour par deux utilisateurs en même temps n’est pas défini à moins que le système ne puisse garantir que deux utilisateurs ne peuvent pas mettre à jour un enregistrement simultanément.

> [!NOTE]
> Cette rubrique s’applique aux objets dérivés de `CRecordset` où l’extraction de lignes en bloc n’a pas été implémentée. Si vous avez mis en œuvre la mise en place de la ligne en vrac, certaines des informations ne s’appliquent pas. Par exemple, vous `Edit` ne `Update` pouvez pas appeler les fonctions et les membres. Pour plus d’informations sur la ligne en vrac aller chercher, voir [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="record-locking-modes"></a><a name="_core_record.2d.locking_modes"></a>Modes de verrouillage des dossiers

Les classes de base de données fournissent deux [modes de verrouillage des dossiers](../../mfc/reference/crecordset-class.md#setlockingmode):

- Verrouillage optimiste (par défaut)

- Verrouillage pessimiste

La mise à jour d’un enregistrement se fait en trois étapes :

1. Vous commencez l’opération en appelant la fonction membre [Edit.](../../mfc/reference/crecordset-class.md#edit)

1. Vous modifiez les champs appropriés de l’enregistrement actuel.

1. Vous mettez fin à l’opération — et si vous commettez normalement la mise à jour — en appelant la fonction membre [de mise à jour.](../../mfc/reference/crecordset-class.md#update)

Le verrouillage optimiste verrouille le dossier sur `Update` la source de données seulement pendant l’appel. Si vous utilisez un verrouillage optimiste dans un environnement `Update` multiutilisant, l’application doit gérer une condition de défaillance. Le verrouillage pessimiste verrouille le dossier `Edit` dès que vous appelez `Update` et ne le `CDBException` libère pas jusqu’à ce `Update`que vous l’appeliez (les défaillances sont indiquées par le mécanisme, pas par une valeur de FALSE retournée par ). Le verrouillage pessimiste a une pénalité de performance potentielle pour d’autres utilisateurs, parce que `Update` l’accès simultané au même enregistrement pourrait devoir attendre jusqu’à l’achèvement du processus de votre application.

## <a name="locking-records-in-your-recordset"></a><a name="_core_locking_records_in_your_recordset"></a>Enregistrement de verrouillage dans votre dossier

Si vous souhaitez modifier le mode de [verrouillage](#_core_record.2d.locking_modes) d’un objet de l’enregistrement par défaut, vous devez changer le mode avant d’appeler `Edit`.

#### <a name="to-change-the-current-locking-mode-for-your-recordset"></a>Pour changer le mode de verrouillage actuel pour votre dossier

1. Appelez la fonction [membre SetLockingMode,](../../mfc/reference/crecordset-class.md#setlockingmode) en spécifiant soit `CRecordset::pessimistic` ou `CRecordset::optimistic`.

Le nouveau mode de verrouillage reste en vigueur jusqu’à ce que vous le modifiiez à nouveau ou que le jeu d’enregistrement soit fermé.

> [!NOTE]
> Relativement peu de conducteurs d’ODBC soutiennent actuellement le verrouillage pessimiste.

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : création d'une jointure (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)<br/>
[Recordset : ajout, modification et suppression d'enregistrements (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)

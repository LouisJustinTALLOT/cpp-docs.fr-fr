---
description: 'En savoir plus sur : Recordset : verrouillage d’enregistrements (ODBC)'
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
ms.openlocfilehash: 1833aff2a1a68affe02cdcf5294007802452bbf9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304478"
---
# <a name="recordset-locking-records-odbc"></a>Recordset : verrouillage d'enregistrements (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Cette rubrique répond aux questions suivantes :

- [Types de verrouillage d’enregistrement disponibles](#_core_record.2d.locking_modes).

- [Comment verrouiller des enregistrements dans votre Recordset pendant les mises à jour](#_core_locking_records_in_your_recordset).

Lorsque vous utilisez un Recordset pour mettre à jour un enregistrement sur la source de données, votre application peut verrouiller l’enregistrement afin qu’aucun autre utilisateur ne puisse mettre à jour l’enregistrement en même temps. L’état d’un enregistrement mis à jour par deux utilisateurs en même temps n’est pas défini, à moins que le système ne puisse garantir que deux utilisateurs ne peuvent pas mettre à jour un enregistrement simultanément.

> [!NOTE]
> Cette rubrique s’applique aux objets dérivés de `CRecordset` où l’extraction de lignes en bloc n’a pas été implémentée. Si vous avez implémenté l’extraction de lignes en bloc, certaines des informations ne s’appliquent pas. Par exemple, vous ne pouvez pas appeler les `Edit` `Update` fonctions membres et. Pour plus d’informations sur l’extraction de lignes en bloc, consultez [Recordset : extraction globale d’enregistrements (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="record-locking-modes"></a><a name="_core_record.2d.locking_modes"></a> Modes de Record-Locking

Les classes de base de données fournissent deux [modes de verrouillage des enregistrements](../../mfc/reference/crecordset-class.md#setlockingmode):

- Verrouillage optimiste (valeur par défaut)

- Verrouillage pessimiste

La mise à jour d’un enregistrement se produit en trois étapes :

1. Vous commencez l’opération en appelant la fonction membre [Edit](../../mfc/reference/crecordset-class.md#edit) .

1. Vous modifiez les champs appropriés de l’enregistrement en cours.

1. Vous terminez l’opération, et validez normalement la mise à jour, en appelant la fonction membre [Update](../../mfc/reference/crecordset-class.md#update) .

Le verrouillage optimiste verrouille l’enregistrement sur la source de données uniquement pendant l' `Update` appel. Si vous utilisez le verrouillage optimiste dans un environnement multi-utilisateur, l’application doit gérer une `Update` condition d’échec. Le verrouillage pessimiste verrouille l’enregistrement dès que vous appelez `Edit` et ne le libère pas tant que vous n’appelez pas `Update` (les échecs sont signalés par le `CDBException` mécanisme, et non par la valeur false retournée par `Update` ). Le verrouillage pessimiste a une baisse potentielle des performances pour les autres utilisateurs, car l’accès simultané au même enregistrement peut être dû à l’attente jusqu’à la fin du processus de votre application `Update` .

## <a name="locking-records-in-your-recordset"></a><a name="_core_locking_records_in_your_recordset"></a> Verrouillage des enregistrements dans votre jeu d’enregistrements

Si vous souhaitez modifier le [mode de verrouillage](#_core_record.2d.locking_modes) par défaut d’un objet Recordset, vous devez modifier le mode avant d’appeler `Edit` .

#### <a name="to-change-the-current-locking-mode-for-your-recordset"></a>Pour modifier le mode de verrouillage actuel de votre jeu d’enregistrements

1. Appelez la fonction membre [SetLockingMode](../../mfc/reference/crecordset-class.md#setlockingmode) , en spécifiant `CRecordset::pessimistic` ou `CRecordset::optimistic` .

Le nouveau mode de verrouillage reste en vigueur jusqu’à ce que vous le modifiiez à nouveau ou que le Recordset soit fermé.

> [!NOTE]
> Relativement peu de pilotes ODBC prennent actuellement en charge le verrouillage pessimiste.

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : exécution d’une jointure (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)<br/>
[Recordset : ajout, mise à jour et suppression d’enregistrements (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)

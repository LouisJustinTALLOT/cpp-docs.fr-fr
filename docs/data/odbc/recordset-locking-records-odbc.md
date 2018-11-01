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
ms.openlocfilehash: 08d7ca1db474a5735ccaabaa7d7d87b359730bb5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438695"
---
# <a name="recordset-locking-records-odbc"></a>Recordset : verrouillage d'enregistrements (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Cette rubrique explique :

- [Les types de verrouillage des enregistrements](#_core_record.2d.locking_modes).

- [Comment verrouiller des enregistrements dans votre jeu d’enregistrements lors de mises à jour](#_core_locking_records_in_your_recordset).

Lorsque vous utilisez un jeu d’enregistrements à mettre à jour un enregistrement sur la source de données, votre application peut verrouiller l’enregistrement, aucun autre utilisateur peut mettre à jour l’enregistrement en même temps. L’état d’un enregistrement mis à jour par deux utilisateurs en même temps n’est pas défini, sauf si le système peut garantir que deux utilisateurs ne peuvent pas mettre à jour un enregistrement simultanément.

> [!NOTE]
>  Cette rubrique s’applique aux objets dérivés de `CRecordset` dans les lignes en bloc l’extraction n’a pas été implémentée. Si vous avez implémenté l’extraction de lignes en bloc, certaines informations ne s’applique pas. Par exemple, vous ne pouvez pas appeler le `Edit` et `Update` fonctions membres. Pour plus d’informations sur l’extraction de lignes en bloc, consultez [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="_core_record.2d.locking_modes"></a> Modes de verrouillage des enregistrements

Les classes de base de données fournissent deux [modes de verrouillage des enregistrements](../../mfc/reference/crecordset-class.md#setlockingmode):

- OPTIMISTIC verrouillage (il s’agit de la valeur par défaut)

- Verrouillage pessimiste

La mise à jour un enregistrement se produit en trois étapes :

1. Commencer l’opération en appelant le [modifier](../../mfc/reference/crecordset-class.md#edit) fonction membre.

1. Vous modifiez les champs appropriés de l’enregistrement en cours.

1. Terminez l’opération — et en principe validez la mise à jour, en appelant le [mettre à jour](../../mfc/reference/crecordset-class.md#update) fonction membre.

Le verrouillage optimiste verrouille l’enregistrement de la source de données uniquement pendant le `Update` appeler. Si vous utilisez le verrouillage optimiste dans un environnement multi-utilisateur, l’application doit gérer un `Update` condition d’échec. Le verrouillage pessimiste verrouille l’enregistrement dès que vous appelez `Edit` et ne libère pas jusqu'à ce que vous appel `Update` (échecs sont signalés via la `CDBException` mécanisme, pas par la valeur FALSE retournée par `Update`). Le verrouillage pessimiste a une altération potentielle des performances pour d’autres utilisateurs, car les accès simultanés au même enregistrement doivent attendre jusqu'à la fin de votre application `Update` processus.

##  <a name="_core_locking_records_in_your_recordset"></a> Verrouillage d’enregistrements dans le jeu d’enregistrements

Si vous souhaitez modifier un objet recordset [le mode de verrouillage](#_core_record.2d.locking_modes) à partir de la valeur par défaut, vous devez modifier le mode avant d’appeler `Edit`.

#### <a name="to-change-the-current-locking-mode-for-your-recordset"></a>Pour modifier le mode de verrouillage actuel pour votre jeu d’enregistrements

1. Appelez le [SetLockingMode](../../mfc/reference/crecordset-class.md#setlockingmode) fonction membre, en spécifiant `CRecordset::pessimistic` ou `CRecordset::optimistic`.

Le nouveau mode de verrouillage reste en vigueur jusqu'à ce que vous la modifiez à nouveau ou le recordset est fermé.

> [!NOTE]
>  Très peu de pilotes ODBC prend en charge le verrouillage pessimiste.

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : création d’une jointure (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)<br/>
[Recordset : ajout, modification et suppression d’enregistrements (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)
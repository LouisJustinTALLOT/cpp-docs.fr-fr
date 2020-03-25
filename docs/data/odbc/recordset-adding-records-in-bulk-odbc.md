---
title: "Recordset : ajout global d'enregistrements (ODBC)"
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, adding records
- recordsets, adding records
- bulk record additions to recordsets
ms.assetid: 4685f656-14b9-4f10-a1c5-147b2b89a0b4
ms.openlocfilehash: f561cb0275933a973e97ef0518148e81e14a0234
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213016"
---
# <a name="recordset-adding-records-in-bulk-odbc"></a>Recordset : ajout global d'enregistrements (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

La classe MFC [CRecordset](../../mfc/reference/crecordset-class.md) a une nouvelle optimisation qui améliore l’efficacité lorsque vous ajoutez de nouveaux enregistrements en bloc à une table.

> [!NOTE]
> Cette rubrique s’applique aux objets dérivés de `CRecordset` où l’extraction de lignes en bloc n’a pas été implémentée. Si vous utilisez l’extraction de lignes en bloc, consultez [Recordset : extraction globale d’enregistrements (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Une nouvelle option pour le paramètre *dwOptions* de la fonction membre [CRecordset :: Open](../../mfc/reference/crecordset-class.md#open) , `optimizeBulkAdd`, améliore les performances lorsque vous ajoutez plusieurs enregistrements de façon consécutive sans appeler `Requery` ou `Close`. Seuls les champs qui ont été modifiés avant le premier appel `AddNew`de `Update` sont marqués comme étant modifiés pour les appels de `Update` de /.

Si vous utilisez les classes de base de données pour tirer parti de la fonction API ODBC `::SQLSetPos` pour l’ajout, la modification et la suppression d’enregistrements, cette optimisation n’est pas nécessaire.

Si la bibliothèque de curseurs ODBC est chargée ou si le pilote ODBC ne prend pas en charge l’ajout, la modification et la suppression via `::SQLSetPos`, cette optimisation doit améliorer les performances de l’ajout en bloc. Pour activer cette optimisation, définissez le paramètre *dwOptions* dans le `Open` appel de votre jeu d’enregistrements comme suit :

```
appendOnly | optimizeBulkAdd
```

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : ajout, modification et suppression d’enregistrements (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[Recordset : verrouillage d’enregistrements (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)

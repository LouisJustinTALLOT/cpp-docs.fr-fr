---
title: 'Recordset : Ajout d’enregistrements en bloc (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets, adding records
- recordsets, adding records
- bulk record additions to recordsets
ms.assetid: 4685f656-14b9-4f10-a1c5-147b2b89a0b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c870861d11a27b5343888e62259a585720274190
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068583"
---
# <a name="recordset-adding-records-in-bulk-odbc"></a>Recordset : ajout global d'enregistrements (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.  
  
La bibliothèque MFC [CRecordset](../../mfc/reference/crecordset-class.md) classe a une nouvelle fonction d’optimisation qui améliore l’efficacité lorsque vous ajoutez de nouveaux enregistrements en bloc dans une table.  
  
> [!NOTE]
>  Cette rubrique s’applique aux objets dérivés de `CRecordset` dans les lignes en bloc l’extraction n’a pas été implémentée. Si vous utilisez l’extraction de lignes en bloc, consultez [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
Une nouvelle option pour le *dwOptions* paramètre à la [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) fonction membre, `optimizeBulkAdd`, améliore les performances lorsque vous ajoutez plusieurs enregistrements à la suite sans appeler `Requery` ou `Close`. Seuls les champs qui sont modifiés avant la première `Update` appel sont marqués comme modifiés pour la suivantes `AddNew` / `Update` appels.  
  
Si vous utilisez les classes de base de données pour tirer parti de la `::SQLSetPos` fonction API ODBC pour l’ajout, modification, et suppression d’enregistrements, cette optimisation n’est pas nécessaire.  
  
Si la bibliothèque de curseurs ODBC est chargée ou le pilote ODBC ne prend pas en charge l’ajout, modification et suppression via `::SQLSetPos`, cette optimisation doit améliorer en bloc ajouter des performances. Pour activer l’optimisation, définissez le *dwOptions* paramètre dans le `Open` appeler pour votre jeu d’enregistrements à ce qui suit :  
  
```  
appendOnly | optimizeBulkAdd  
```  
  
## <a name="see-also"></a>Voir aussi  

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : ajout, modification et suppression d’enregistrements (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[Recordset : verrouillage d’enregistrements (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
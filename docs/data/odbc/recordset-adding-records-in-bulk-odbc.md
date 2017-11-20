---
title: "Recordset : Ajout d’enregistrements en bloc (ODBC) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ODBC recordsets, adding records
- recordsets, adding records
- bulk record additions to recordsets
ms.assetid: 4685f656-14b9-4f10-a1c5-147b2b89a0b4
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 937e5273a0b999672dbbc98a927d34909d04136b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="recordset-adding-records-in-bulk-odbc"></a>Recordset : ajout global d'enregistrements (ODBC)
Cette rubrique s’applique aux classes ODBC MFC.  
  
 La bibliothèque MFC [CRecordset](../../mfc/reference/crecordset-class.md) classe a une nouvelle optimisation qui améliore l’efficacité lorsque vous ajoutez de nouveaux enregistrements en bloc dans une table.  
  
> [!NOTE]
>  Cette rubrique s’applique aux objets dérivés de `CRecordset` dans les lignes en bloc l’extraction n’a pas été implémentée. Si vous utilisez l’extraction de lignes en bloc, consultez [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Une nouvelle option pour le **dwOptions** paramètre à la [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) fonction membre, **optimizeBulkAdd**, améliore les performances lorsque vous ajoutez plusieurs enregistrements consécutivement sans appeler **Requery** ou **fermer**. Seuls les champs qui sont modifiées avant la première **mise à jour** appel sont marqués comme modifiés pour l’ultérieures `AddNew` / **mise à jour** appels.  
  
 Si vous utilisez les classes de base de données pour tirer parti de la **:: SQLSetPos** fonction d’API ODBC pour l’ajout, modification, et suppression d’enregistrements, cette optimisation n’est pas nécessaire.  
  
 Si la bibliothèque de curseurs ODBC est chargée ou le pilote ODBC ne prend pas en charge l’ajout, modification et suppression via **:: SQLSetPos**, cette optimisation doit améliorer en bloc ajouter les performances. Pour activer l’optimisation, définissez le **dwOptions** paramètre dans le **ouvrir** appeler pour votre jeu d’enregistrements à ce qui suit :  
  
```  
appendOnly | optimizeBulkAdd  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Jeu d’enregistrements (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Recordset : Ajout, modification et suppression d’enregistrements (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)   
 [Recordset : verrouillage d’enregistrements (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
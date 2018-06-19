---
title: CRowset::GetOriginalData | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CRowset<TAccessor>.GetOriginalData
- CRowset<TAccessor>::GetOriginalData
- GetOriginalData
- ATL::CRowset<TAccessor>::GetOriginalData
- ATL.CRowset.GetOriginalData
- CRowset::GetOriginalData
- ATL::CRowset::GetOriginalData
- CRowset.GetOriginalData
dev_langs:
- C++
helpviewer_keywords:
- GetOriginalData method
ms.assetid: 5b69d30e-34f4-41a4-a82d-cd175be88d53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 65c0966d60b2498117ac30dc137307a274911e54
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098405"
---
# <a name="crowsetgetoriginaldata"></a>CRowset::GetOriginalData
Appels **IRowsetUpdate::GetOriginalData** pour récupérer les données récemment extraites ou transmise à la source de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetOriginalData() throw();  
  
```  
  
## <a name="return-value"></a>Valeur de retour  
 `HRESULT` standard.  
  
## <a name="remarks"></a>Notes  
 Cette méthode récupère les données extraites le plus récemment à partir d’ou transmise à la source de données ; Il ne récupère pas de valeurs basées sur les modifications en attente.  
  
 Cette méthode requiert l’interface facultative `IRowsetUpdate`, qui ne peut pas être pris en charge sur tous les fournisseurs ; si c’est le cas, la méthode retourne **E_NOINTERFACE**. Vous devez également définir **DBPROP_IRowsetUpdate** à `VARIANT_TRUE` avant d’appeler **ouvrir** sur la table ou d’une commande qui contient l’ensemble de lignes.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CRowset (classe)](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::GetOriginalData](https://msdn.microsoft.com/en-us/library/ms709947.aspx)
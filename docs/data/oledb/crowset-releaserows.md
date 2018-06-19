---
title: CRowset::ReleaseRows | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ReleaseRows
- CRowset::ReleaseRows
- ATL::CRowset<TAccessor>::ReleaseRows
- CRowset<TAccessor>.ReleaseRows
- CRowset.ReleaseRows
- ATL.CRowset.ReleaseRows
- ATL.CRowset<TAccessor>.ReleaseRows
- CRowset<TAccessor>::ReleaseRows
- ATL::CRowset::ReleaseRows
dev_langs:
- C++
helpviewer_keywords:
- ReleaseRows method
ms.assetid: fa7254f5-566f-4754-bdf7-d0874256926f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 606e5887d226c2ed9dae909bf04716efcb5de737
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096910"
---
# <a name="crowsetreleaserows"></a>CRowset::ReleaseRows
Appels [IRowset::ReleaseRows](https://msdn.microsoft.com/en-us/library/ms719771.aspx) pour libérer le handle de ligne actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ReleaseRows() throw();  
  
```  
  
## <a name="return-value"></a>Valeur de retour  
 `HRESULT` standard.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CRowset, classe](../../data/oledb/crowset-class.md)
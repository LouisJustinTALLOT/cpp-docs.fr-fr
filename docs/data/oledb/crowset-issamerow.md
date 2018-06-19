---
title: CRowset::IsSameRow | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowset::IsSameRow
- CRowset.IsSameRow
- IsSameRow
- ATL::CRowset::IsSameRow
- ATL.CRowset.IsSameRow
- CRowset<TAccessor>::IsSameRow
- ATL.CRowset<TAccessor>.IsSameRow
- CRowset<TAccessor>.IsSameRow
- ATL::CRowset<TAccessor>::IsSameRow
dev_langs:
- C++
helpviewer_keywords:
- IsSameRow method
ms.assetid: 53cba847-52f5-4dd9-973f-bbe7454c425c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5cbe8179c04b8d7ab855942a4e6190341cc03128
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097118"
---
# <a name="crowsetissamerow"></a>CRowset::IsSameRow
Compare la ligne spécifiée à la ligne actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT IsSameRow(HROW hRow) const throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 `hRow`  
 [in] Un descripteur de la ligne à comparer à la ligne actuelle.  
  
## <a name="return-value"></a>Valeur de retour  
 `HRESULT` standard. `S_OK` Indique les lignes sont les mêmes. Pour les autres valeurs, consultez [IRowsetIndentity::IsSameRow](https://msdn.microsoft.com/en-us/library/ms719629.aspx) dans les *de référence du programmeur OLE DB* dans le Kit de développement logiciel Windows.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CRowset, classe](../../data/oledb/crowset-class.md)
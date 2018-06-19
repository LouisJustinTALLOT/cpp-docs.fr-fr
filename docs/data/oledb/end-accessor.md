---
title: END_ACCESSOR | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- END_ACCESSOR
dev_langs:
- C++
helpviewer_keywords:
- END_ACCESSOR macro
ms.assetid: 26f74167-68c4-4909-a474-73dc7ebc9542
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f7bab52df0ed05886933a3df827fae5198651b39
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33099236"
---
# <a name="endaccessor"></a>END_ACCESSOR
Marque la fin d’une entrée de l’accesseur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
END_ACCESSOR()  
  
```  
  
## <a name="remarks"></a>Notes  
 Pour les accesseurs multiples sur un ensemble de lignes, vous devez spécifier `BEGIN_ACCESSOR_MAP` et utiliser le `BEGIN_ACCESSOR` macro pour chaque accesseur individuel. La macro `BEGIN_ACCESSOR` se termine avec la macro `END_ACCESSOR` . Le `BEGIN_ACCESSOR_MAP` macro s’est terminée avec le `END_ACCESSOR_MAP` (macro).  
  
## <a name="example"></a>Exemple  
 Consultez [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [Macros et fonctions globales pour les modèles du consommateur OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)
---
title: BEGIN_ACCESSOR | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- BEGIN_ACCESSOR
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_ACCESSOR macro, syntax
- BEGIN_ACCESSOR macro
ms.assetid: 59d0ff3e-7cfd-4ce8-9a1c-d664c0892a52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0ffb1d506a198586a5a625664f21c29954aada40
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089843"
---
# <a name="beginaccessor"></a>BEGIN_ACCESSOR
Marque le début d’une entrée de l’accesseur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BEGIN_ACCESSOR(num, bAuto)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *num*  
 [in] Le nombre de décalage de zéro pour l’accesseur dans ce mappage d’accesseur.  
  
 *bAuto*  
 [in] Spécifie si cet accesseur est un accesseur automatique ou un accesseur manuel. Si **true**, l’accesseur est automatique ; si **false**, l’accesseur est manuel. Un accesseur automatique signifie les données sont extraites pour vous sur les opérations de déplacement.  
  
## <a name="remarks"></a>Notes  
 Dans le cas de plusieurs accesseurs dans un ensemble de lignes, vous devez spécifier `BEGIN_ACCESSOR_MAP` et utiliser le `BEGIN_ACCESSOR` macro pour chaque accesseur individuel. La macro `BEGIN_ACCESSOR` se termine avec la macro `END_ACCESSOR` . Le `BEGIN_ACCESSOR_MAP` macro s’est terminée avec le `END_ACCESSOR_MAP` (macro).  
  
## <a name="example"></a>Exemple  
 Consultez [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [Macros et fonctions globales pour les modèles du consommateur OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [END_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)
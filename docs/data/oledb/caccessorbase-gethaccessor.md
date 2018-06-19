---
title: CAccessorBase::GetHAccessor | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- GetHAccessor
- CAccessorBase::GetHAccessor
- CAccessorBase.GetHAccessor
dev_langs:
- C++
helpviewer_keywords:
- GetHAccessor method
ms.assetid: 1bb98762-0752-4aae-a0b6-ba96bec03621
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2bacc7f24d112fc6714200c6347e66bb66866831
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33088783"
---
# <a name="caccessorbasegethaccessor"></a>CAccessorBase::GetHAccessor
Récupère le handle d’accesseur d’un accesseur spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      HACCESSOR GetHAccessor(ULONG nAccessor) const;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `nAccessor`  
 [in] Le nombre de décalage de zéro pour l’accesseur.  
  
## <a name="return-value"></a>Valeur de retour  
 Le handle d’accesseur.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CAccessorBase, classe](../../data/oledb/caccessorbase-class.md)
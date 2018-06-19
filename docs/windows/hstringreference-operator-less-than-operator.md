---
title: HStringReference::Operator&lt; opérateur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator<
dev_langs:
- C++
ms.assetid: 55aa48e8-7c96-4123-9ebe-42b4cd8b9377
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5b486157fb42883af724f2356e7f85701e405035
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877291"
---
# <a name="hstringreferenceoperatorlt-operator"></a>HStringReference::Operator&lt; (opérateur)
Indique si le premier paramètre est inférieur au second paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline bool operator<(  
    const HStringReference& lhs,   
    const HStringReference& rhs) throw()  
```  
  
#### <a name="parameters"></a>Paramètres  
 `lhs`  
 Le premier paramètre à comparer. `lhs` peut être une référence à un HStringReference.  
  
 `rhs`  
 Le deuxième paramètre à comparer.  `rhs` peut être une référence à un HStringReference.  
  
## <a name="return-value"></a>Valeur de retour  
 `true` Si le `lhs` paramètre est inférieure à la `rhs` paramètre ; sinon, `false`.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [HStringReference, classe](../windows/hstringreference-class.md)
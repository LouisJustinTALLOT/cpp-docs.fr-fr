---
title: HStringReference::Operator&lt; opérateur | Microsoft Docs
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
ms.openlocfilehash: 489d97252dcb4d20b7ef2f8557991a4e6016743d
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605530"
---
# <a name="hstringreferenceoperatorlt-operator"></a>HStringReference::Operator&lt; opérateur
Indique si le premier paramètre est inférieur au second.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline bool operator<(  
    const HStringReference& lhs,   
    const HStringReference& rhs) throw()  
```  
  
### <a name="parameters"></a>Paramètres  
 *LHS*  
 Le premier paramètre à comparer. *LHS* peut être une référence à un **HStringReference**.  
  
 *terme de droite*  
 Le deuxième paramètre à comparer.  *RHS* peut être une référence à un **HStringReference**.  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si le *lhs* paramètre est inférieure à la *rhs* paramètre ; sinon, **false**.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [HStringReference, classe](../windows/hstringreference-class.md)
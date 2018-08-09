---
title: HString::Operator&lt; opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator<
dev_langs:
- C++
ms.assetid: 48a051cb-4609-42be-b48c-d35fc99d1eab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1bdc6d54a6c9b60036d7434edec960715db304e2
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017680"
---
# <a name="hstringoperatorlt-operator"></a>HString::Operator&lt; opérateur
Indique si le premier paramètre est inférieur au second.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline bool operator<(  
    const HString& lhs,   
    const HString& rhs) throw()  
```  
  
### <a name="parameters"></a>Paramètres  
 *LHS*  
 Le premier paramètre à comparer. *LHS* peut être une référence à un **HString**.  
  
 *terme de droite*  
 Le deuxième paramètre à comparer. *RHS* peut être une référence à un **HString**.  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si le *lhs* paramètre est inférieure à la *rhs* paramètre ; sinon, **false**.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [HString, classe](../windows/hstring-class.md)
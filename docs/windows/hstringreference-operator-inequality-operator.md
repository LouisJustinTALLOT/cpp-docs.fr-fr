---
title: HStringReference::Operator ! =, opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator!=
dev_langs:
- C++
ms.assetid: 01ab6691-1fc7-4feb-85f0-fe795593a160
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3e2fc27d47fa218dd4378538bb193d650727ed22
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606525"
---
# <a name="hstringreferenceoperator-operator"></a>HStringReference::Operator!=, opérateur
Indique si les deux paramètres ne sont pas égales.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline bool operator==(  
               const HStringReference& lhs,   
               const HSTRING& rhs) throw()  
  
inline bool operator!=(  
               const HStringReference& lhs,   
               const HStringReference& rhs) throw()  
  
inline bool operator!=(  
               const HSTRING& lhs,   
               const HStringReference& rhs) throw()  
  
inline bool operator!=(  
               const HStringReference& lhs,   
               const HSTRING& rhs) throw()  
```  
  
### <a name="parameters"></a>Paramètres  
 *LHS*  
 Le premier paramètre à comparer. *LHS* peut être un **HStringReference** objet ou un handle HSTRING.  
  
 *terme de droite*  
 Le deuxième paramètre à comparer.  *RHS* peut être un **HStringReference** objet ou un handle HSTRING.  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si le *lhs* et *rhs* paramètres ne sont pas égales ; sinon, **false**.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [HStringReference, classe](../windows/hstringreference-class.md)
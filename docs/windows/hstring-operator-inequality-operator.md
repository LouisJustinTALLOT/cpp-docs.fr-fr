---
title: HString::Operator ! =, opérateur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator!=
dev_langs:
- C++
ms.assetid: dcdd2aca-e7d6-4bf1-b2de-03efbb430a93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 74fc15d10818d14467b866ec37c9e353348ce882
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877029"
---
# <a name="hstringoperator-operator"></a>HString::Operator!=, opérateur
Indique si les deux paramètres ne sont pas égales.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline bool operator!=( const HString& lhs,   
                        const HString& rhs) throw()  
  
inline bool operator!=( const HStringReference& lhs,   
                        const HString& rhs) throw()  
  
inline bool operator!=( const HString& lhs,   
                        const HStringReference& rhs) throw()  
  
inline bool operator!=( const HSTRING& lhs,   
                        const HString& rhs) throw()  
  
inline bool operator!=( const HString& lhs,   
                        const HSTRING& rhs) throw()  
```  
  
#### <a name="parameters"></a>Paramètres  
 `lhs`  
 Le premier paramètre à comparer. `lhs` peut être un objet HString ou HStringReference, ou un handle HSTRING.  
  
 `rhs`  
 Le deuxième paramètre à comparer.`rhs` peut être un objet HString ou HStringReference, ou un handle HSTRING.  
  
## <a name="return-value"></a>Valeur de retour  
 `true` Si le `lhs` et `rhs` paramètres ne sont pas égaux ; sinon, `false`.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [HString, classe](../windows/hstring-class.md)
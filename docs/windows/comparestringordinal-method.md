---
title: Comparestringordinal, méthode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::CompareStringOrdinal
dev_langs:
- C++
ms.assetid: ffa997fd-8cd7-40a5-b9e7-f55d40b072f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e3abf87340671d1ac4851b055a57896e340d0c20
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33860809"
---
# <a name="comparestringordinal-method"></a>CompareStringOrdinal, méthode
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline INT32 CompareStringOrdinal(  
   HSTRING lhs,   
   HSTRING rhs)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `lhs`  
 La première HSTRING à comparer.  
  
 `rhs`  
 La deuxième HSTRING à comparer.  
  
## <a name="return-value"></a>Valeur de retour  
  
|Value|Condition|  
|-----------|---------------|  
|-1|`lhs` est inférieur à `rhs`.|  
|0|`lhs` est égal à `rhs`.|  
|1|`lhs` est supérieur à `rhs`.|  
  
## <a name="remarks"></a>Notes  
 Compare deux objets HSTRING spécifiés et retourne un entier qui indique leur position relative dans un ordre de tri.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Wrappers::Details, espace de noms](../windows/microsoft-wrl-wrappers-details-namespace.md)
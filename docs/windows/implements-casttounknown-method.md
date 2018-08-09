---
title: Implements::casttounknown, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements::CastToUnknown
dev_langs:
- C++
helpviewer_keywords:
- CastToUnknown method
ms.assetid: ca3324f7-4136-406b-8698-7389f4f3d3c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: efaf7b51da1e4a4e744133884b92ac78db3b3f66
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017766"
---
# <a name="implementscasttounknown-method"></a>Implements::CastToUnknown, méthode
Obtient un pointeur vers sous-jacent `IUnknown` interface.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
__forceinline IUnknown* CastToUnknown();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Cette opération réussit et retourne toujours le `IUnknown` pointeur.  
  
## <a name="remarks"></a>Notes  
 Fonction d’assistance interne.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** implements.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Implements, structure](../windows/implements-structure.md)
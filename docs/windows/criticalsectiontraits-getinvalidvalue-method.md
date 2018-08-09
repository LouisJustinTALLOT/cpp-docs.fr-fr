---
title: Criticalsectiontraits::getinvalidvalue, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue
dev_langs:
- C++
helpviewer_keywords:
- GetInvalidValue method
ms.assetid: 665f30a6-ca9c-4968-8c03-8f84e6b2329b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 01efd9bf3941a5b19e1f0fe6c106d47f1b6e9fcf
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642059"
---
# <a name="criticalsectiontraitsgetinvalidvalue-method"></a>CriticalSectionTraits::GetInvalidValue, méthode
Spécialise une **CriticalSection** modèle afin que le modèle est toujours non valide.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline static Type GetInvalidValue();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne toujours un pointeur vers une section critique non valide.  
  
## <a name="remarks"></a>Notes  
 Le `Type` modificateur est défini comme `typedef CRITICAL_SECTION* Type;`.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Voir aussi  
 [CriticalSectionTraits, structure](../windows/criticalsectiontraits-structure.md)
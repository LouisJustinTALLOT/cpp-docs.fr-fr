---
title: Criticalsectiontraits::Unlock, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Unlock method
ms.assetid: 8fb382f5-6eda-407e-9673-71d77bda4962
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b64f44e2188848a25e607c53171e25aa721e9bc4
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641364"
---
# <a name="criticalsectiontraitsunlock-method"></a>CriticalSectionTraits::Unlock, méthode
Spécialise une `CriticalSection` modèle afin qu’il prend en charge la libération de la propriété de l’objet de section critique spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline static void Unlock(  
   _In_ Type cs  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 *cs*  
 Pointeur vers un objet de section critique.  
  
## <a name="remarks"></a>Notes  
 Le `Type` modificateur est défini comme `typedef CRITICAL_SECTION* Type;`.  
  
 Pour plus d’informations, consultez **LeaveCriticalSection fonction** dans le **des fonctions de synchronisation** section de la documentation de l’API de Windows.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Voir aussi  
 [CriticalSectionTraits, structure](../windows/criticalsectiontraits-structure.md)
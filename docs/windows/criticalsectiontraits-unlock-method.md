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
ms.openlocfilehash: 2f66f185692c200ea459b88363143c0cc1af9d55
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39466008"
---
# <a name="criticalsectiontraitsunlock-method"></a>CriticalSectionTraits::Unlock, méthode
Spécialise un modèle CriticalSection afin qu’il prend en charge la libération de la propriété de l’objet de section critique spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
inline static void Unlock(  
   _In_ Type cs  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *cs*  
 Pointeur vers un objet de section critique.  
  
## <a name="remarks"></a>Notes  
 Le *Type* modificateur est défini comme `typedef CRITICAL_SECTION* Type;`.  
  
 Pour plus d’informations, consultez « Fonction LeaveCriticalSection » dans la section « Fonctions de synchronisation » de la documentation de l’API de Windows.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Voir aussi  
 [CriticalSectionTraits, structure](../windows/criticalsectiontraits-structure.md)
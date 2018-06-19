---
title: Criticalsectiontraits::Unlock, méthode | Documents Microsoft
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
ms.openlocfilehash: 35a632a6c88ed29ef5e30e942c1341246de75e71
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33883496"
---
# <a name="criticalsectiontraitsunlock-method"></a>CriticalSectionTraits::Unlock, méthode
Spécialiser un modèle CriticalSection afin qu’il prend en charge la propriété de libération de l’objet spécifié de section critique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
inline static void Unlock(  
   _In_ Type cs  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cs`  
 Pointeur vers un objet de section critique.  
  
## <a name="remarks"></a>Notes  
 Le *Type* modificateur est défini en tant que `typedef CRITICAL_SECTION* Type;`.  
  
 Pour plus d’informations, consultez « Fonction LeaveCriticalSection », dans la section « Fonctions de synchronisation » de la documentation de l’API Windows.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Voir aussi  
 [CriticalSectionTraits, structure](../windows/criticalsectiontraits-structure.md)
---
title: Modulebase::decrementobjectcount, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ModuleBase::DecrementObjectCount
dev_langs:
- C++
helpviewer_keywords:
- DecrementObjectCount method
ms.assetid: a016fb07-a36e-40cd-bc7b-8f6e85e256e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 65dc4dbca2e152a62bb79ed104f9533d2fa20569
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40019980"
---
# <a name="modulebasedecrementobjectcount-method"></a>ModuleBase::DecrementObjectCount, méthode
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
virtual long DecrementObjectCount() = 0;  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Le nombre avant l’opération de décrémentation.  
  
## <a name="remarks"></a>Notes  
 En cas d’implémentation, décrémente le nombre d’objets suivis par le module.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** implements.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Modulebase, classe](../windows/modulebase-class.md)   
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)
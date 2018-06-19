---
title: Modulebase::decrementobjectcount, méthode | Documents Microsoft
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
ms.openlocfilehash: daf27930261c0350c1e48b851fe989decd52dde2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876291"
---
# <a name="modulebasedecrementobjectcount-method"></a>ModuleBase::DecrementObjectCount, méthode
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
virtual long DecrementObjectCount() = 0;  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Le nombre avant l’opération de décrémentation.  
  
## <a name="remarks"></a>Notes  
 En cas d’implémentation, décrémente le nombre d’objets suivis par le module.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** implements.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [ModuleBase (classe)](../windows/modulebase-class.md)   
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)
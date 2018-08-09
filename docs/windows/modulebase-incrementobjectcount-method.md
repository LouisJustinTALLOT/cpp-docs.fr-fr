---
title: Modulebase::incrementobjectcount, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ModuleBase::IncrementObjectCount
dev_langs:
- C++
helpviewer_keywords:
- IncrementObjectCount method
ms.assetid: 2d70b472-684c-4bb7-8bab-09505cfcaf28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1ee6c71ba6de195386cda78f2e44902c43523143
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011073"
---
# <a name="modulebaseincrementobjectcount-method"></a>ModuleBase::IncrementObjectCount, méthode
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
virtual long IncrementObjectCount() = 0;  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Le nombre avant l’opération d’incrémentation.  
  
## <a name="remarks"></a>Notes  
 En cas d’implémentation, incrémente le nombre d’objets suivis par le module.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** implements.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Modulebase, classe](../windows/modulebase-class.md)   
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)
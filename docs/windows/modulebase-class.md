---
title: Modulebase, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ModuleBase
dev_langs:
- C++
helpviewer_keywords:
- ModuleBase class
ms.assetid: edce7591-6893-46f7-94a7-382827775548
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b298bcab4c2b3547f2b285fe21d4967f4696fb9d
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605056"
---
# <a name="modulebase-class"></a>ModuleBase, classe
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class ModuleBase;  
```  
  
## <a name="remarks"></a>Notes  
 Représente la classe de base de la [Module](../windows/module-class.md) classes.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[ModuleBase::ModuleBase, constructeur](../windows/modulebase-modulebase-constructor.md)|Initialise une instance de la classe `Module`.|  
|[ModuleBase::~ModuleBase, destructeur](../windows/modulebase-tilde-modulebase-destructor.md)|Annule l’initialisation de l’instance actuelle de la `Module` classe.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[ModuleBase::DecrementObjectCount, méthode](../windows/modulebase-decrementobjectcount-method.md)|En cas d’implémentation, décrémente le nombre d’objets suivis par le module.|  
|[ModuleBase::IncrementObjectCount, méthode](../windows/modulebase-incrementobjectcount-method.md)|En cas d’implémentation, incrémente le nombre d’objets suivis par le module.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `ModuleBase`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** implements.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)
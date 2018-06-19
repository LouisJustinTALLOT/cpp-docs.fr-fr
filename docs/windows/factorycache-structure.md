---
title: FactoryCache (Structure) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::FactoryCache
dev_langs:
- C++
helpviewer_keywords:
- FactoryCache structure
ms.assetid: 624544e6-0989-47f6-a3e9-edb60e1ee6d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 04356316b67f3c341fe1dd1821750fcd3136aa40
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874029"
---
# <a name="factorycache-structure"></a>FactoryCache (structure)
Prend en charge l’infrastructure de la bibliothèque de modèles Windows Runtime C++ et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct FactoryCache;  
```  
  
## <a name="remarks"></a>Notes  
 Contient l’emplacement d’une fabrique de classe et une valeur qui identifie un inscrits wrt ou un objet de classe COM.  
  
## <a name="members"></a>Membres  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[FactoryCache::cookie, données de membre](../windows/factorycache-cookie-data-member.md)|Contient une valeur qui identifie un objet de classe Windows Runtime ou COM inscrit et est utilisée ultérieurement pour annuler l’inscription de l’objet.|  
|[FactoryCache::factory, données de membre](../windows/factorycache-factory-data-member.md)|Pointe vers une fabrique de classe COM ou Windows Runtime.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `FactoryCache`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** module.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)
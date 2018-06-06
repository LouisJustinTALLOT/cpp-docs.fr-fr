---
title: Roinitializewrapper, classe | Documents Microsoft
ms.custom: ''
ms.date: 05/20/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper
dev_langs:
- C++
ms.assetid: 4055fbe0-63a7-4c06-b5a0-414fda5640e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cac71857e6b472f11d1c9eaba48d181ea78fb456
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705590"
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper, classe
Initialise le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class RoInitializeWrapper  
```  
  
## <a name="remarks"></a>Notes  
 RoInitializeWrapper est un outil qui initialise l’exécution de Windows et retourne un HRESULT qui indique si l’opération a réussi. Étant donné que le destructeur de classe appelle `::Windows::Foundation::Uninitialize`, instances de `RoInitializeWrapper` doit être déclarée au niveau de portée globale ou de niveau supérieur.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[RoInitializeWrapper::RoInitializeWrapper, constructeur](../windows/roinitializewrapper-roinitializewrapper-constructor.md)|Initialise une nouvelle instance de la classe RoInitializeWrapper.|  
|[RoInitializeWrapper::~RoInitializeWrapper, destructeur](../windows/roinitializewrapper-tilde-roinitializewrapper-destructor.md)|Détruit l’instance actuelle de la classe RoInitializeWrapper.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[RoInitializeWrapper::HRESULT(), opérateur](../windows/roinitializewrapper-hresult-parens-operator.md)|Récupère la valeur HRESULT produite par le constructeur RoInitializeWrapper.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `RoInitializeWrapper`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Wrappers, espace de noms](../windows/microsoft-wrl-wrappers-namespace.md)
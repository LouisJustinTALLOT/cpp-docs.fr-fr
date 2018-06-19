---
title: ArgTraitsHelper (Structure) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraitsHelper
dev_langs:
- C++
helpviewer_keywords:
- ArgTraitsHelper structure
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6205d69962d70d9da76c932fdd8b3f66f491ebc9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857699"
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper (structure)
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename TDelegateInterface>  
struct ArgTraitsHelper;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `TDelegateInterface`  
 Une interface de délégué.  
  
## <a name="remarks"></a>Notes  
 Permet de définir les caractéristiques communes des arguments de délégué.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`methodType`|Synonyme de `decltype(&TDelegateInterface::Invoke)`.|  
|`Traits`|Synonyme de `ArgTraits<methodType>`.|  
  
### <a name="public-constants"></a>Constantes publiques  
  
|Name|Description|  
|----------|-----------------|  
|[ArgTraitsHelper::args, constante](../windows/argtraitshelper-args-constant.md)|Permet de [ArgTraits::args](../windows/argtraits-args-constant.md) conserver le nombre de paramètres de la méthode Invoke d’une interface de délégué.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `ArgTraitsHelper`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** event.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)
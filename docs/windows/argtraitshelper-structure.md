---
title: ArgTraitsHelper (Structure) | Microsoft Docs
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
ms.openlocfilehash: 1bb8dfeff0e1f3e659e0d3c6514904df39286c45
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39466635"
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper (structure)
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename TDelegateInterface>  
struct ArgTraitsHelper;  
```  
  
#### <a name="parameters"></a>Paramètres  
 *TDelegateInterface*  
 Une interface de délégué.  
  
## <a name="remarks"></a>Notes  
 Permet de définir les caractéristiques communes d’arguments du délégué.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`methodType`|Synonyme de `decltype(&TDelegateInterface::Invoke)`.|  
|`Traits`|Synonyme de `ArgTraits<methodType>`.|  
  
### <a name="public-constants"></a>Constantes publiques  
  
|Name|Description|  
|----------|-----------------|  
|[ArgTraitsHelper::args, constante](../windows/argtraitshelper-args-constant.md)|Vous aide à [ArgTraits::args](../windows/argtraits-args-constant.md) conserver le nombre de paramètres sur le `Invoke` méthode d’une interface de délégué.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `ArgTraitsHelper`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** event.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)
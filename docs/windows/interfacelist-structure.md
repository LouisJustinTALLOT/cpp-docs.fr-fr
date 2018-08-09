---
title: InterfaceList (Structure) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceList
dev_langs:
- C++
helpviewer_keywords:
- InterfaceList structure
ms.assetid: 6ec3228d-eb3e-4b7e-aef1-7dcf17bdf61a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 318738e5f4ac623987b1002e5204739407adcdb9
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017756"
---
# <a name="interfacelist-structure"></a>InterfaceList (structure)
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template <  
   typename T,  
   typename U  
>  
struct InterfaceList;  
```  
  
### <a name="parameters"></a>Paramètres  
 *T*  
 Un nom d’interface ; la première interface dans la liste récursive.  
  
 *U*  
 Un nom d’interface ; les interfaces restantes dans la liste récursive.  
  
## <a name="remarks"></a>Notes  
 Utilisé pour créer une liste récursive des interfaces.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`FirstT`|Synonyme du paramètre modèle *T*.|  
|`RestT`|Synonyme du paramètre modèle *U*.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `InterfaceList`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** implements.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)
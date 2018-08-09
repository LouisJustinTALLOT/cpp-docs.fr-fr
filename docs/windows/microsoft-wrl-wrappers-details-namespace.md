---
title: Microsoft::wrl::wrappers::Details Namespace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details
- internal/Microsoft::WRL::Details
- async/Microsoft::WRL::Details
- corewrappers/Microsoft::WRL::Wrappers::Details
- client/Microsoft::WRL::Details
- module/Microsoft::WRL::Details
- event/Microsoft::WRL::Details
dev_langs:
- C++
helpviewer_keywords:
- Details namespace
ms.assetid: 6d3f04ac-9b53-4a82-a188-a85309ec34a4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3f74f8fe3e5b637869af7b03bb2eaf5e13df9550
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020160"
---
# <a name="microsoftwrlwrappersdetails-namespace"></a>Microsoft::WRL::Wrappers::Details, espace de noms
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
namespace Microsoft::WRL::Wrappers::Details;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="classes"></a>Classes  
  
|Nom|Description|  
|----------|-----------------|  
|[SyncLockT, classe](../windows/synclockt-class.md)|Représente un type qui peut prendre exclusif ou la propriété d’une ressource partagée.|  
|[SyncLockWithStatusT, classe](../windows/synclockwithstatust-class.md)|Représente un type qui peut prendre exclusif ou la propriété d’une ressource partagée.|  
  
### <a name="methods"></a>Méthodes  
  
|Nom|Description|  
|----------|-----------------|  
|[CompareStringOrdinal, méthode](../windows/comparestringordinal-method.md)|Compare deux spécifié `HSTRING` objets et retourne un entier qui indique leur position relative dans un ordre de tri.|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Wrappers, espace de noms](../windows/microsoft-wrl-wrappers-namespace.md)
---
title: Classe d’événements (Windows Runtime C++ modèle bibliothèque) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event
dev_langs:
- C++
ms.assetid: 55dfc9fc-62d4-4bb2-9d85-5b6dd88569e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 12c9e5bfe01de0a9864ff1e94364e0c42178ad11
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33872924"
---
# <a name="event-class-windows-runtime-c-template-library"></a>Event, classe (bibliothèque de modèles Windows Runtime C++)
Représente un événement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class Event : public HandleT<HandleTraits::EventTraits>;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[Event::Event, constructeur (bibliothèque de modèles Windows Runtime C++)](../windows/event-event-constructor-windows-runtime-cpp-template-library.md)|Initialise une nouvelle instance de la classe Event.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[Event::operator=, opérateur](../windows/event-operator-assign-operator.md)|Assigne la référence Event spécifiée à l'instance Event actuelle.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `HandleT`  
  
 `Event`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Wrappers, espace de noms](../windows/microsoft-wrl-wrappers-namespace.md)
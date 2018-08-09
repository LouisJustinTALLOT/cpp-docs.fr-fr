---
title: Classe d’événements (Windows Runtime bibliothèque de modèles C++) | Microsoft Docs
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
ms.openlocfilehash: c07d58f244bf2e7e6c9329196bae7b5bb323ce12
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644162"
---
# <a name="event-class-windows-runtime-c-template-library"></a>Event, classe (bibliothèque de modèles Windows Runtime C++)
Représente un événement.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
class Event : public HandleT<HandleTraits::EventTraits>;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[Event::Event, constructeur (bibliothèque de modèles Windows Runtime C++)](../windows/event-event-constructor-windows-runtime-cpp-template-library.md)|Initialise une nouvelle instance de la **événement** classe.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[Event::operator=, opérateur](../windows/event-operator-assign-operator.md)|Assigne le texte spécifié **événement** référence à le **événement** instance.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `HandleT`  
  
 `Event`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Wrappers, espace de noms](../windows/microsoft-wrl-wrappers-namespace.md)
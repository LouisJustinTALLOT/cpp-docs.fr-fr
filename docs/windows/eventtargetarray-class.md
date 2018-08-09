---
title: Eventtargetarray, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray
dev_langs:
- C++
helpviewer_keywords:
- EventTargetArray class
ms.assetid: e3cadb7c-2160-4cbb-a2f8-c28733d1e96d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4cf5f885a002ede8a715eb4850eef5a8810a0309
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648358"
---
# <a name="eventtargetarray-class"></a>EventTargetArray, classe
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
class EventTargetArray : public Microsoft::WRL::RuntimeClass<Microsoft::WRL::RuntimeClassFlags<ClassicCom>, IUnknown>;  
```  
  
## <a name="remarks"></a>Notes  
 Représente un tableau des gestionnaires d’événements.  
  
 Les gestionnaires d’événements qui sont associés un [EventSource](../windows/eventsource-class.md) objet sont stockées dans un document protégé **EventTargetArray** membre de données.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[EventTargetArray::EventTargetArray, constructeur](../windows/eventtargetarray-eventtargetarray-constructor.md)|Initialise une nouvelle instance de la **EventTargetArray** classe.|  
|[EventTargetArray::~EventTargetArray, destructeur](../windows/eventtargetarray-tilde-eventtargetarray-destructor.md)|Annule l’initialisation en cours **EventTargetArray** classe.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[EventTargetArray::AddTail, méthode](../windows/eventtargetarray-addtail-method.md)|Ajoute le Gestionnaire d’événements spécifié à la fin du tableau interne de gestionnaires d’événements.|  
|[EventTargetArray::Begin, méthode](../windows/eventtargetarray-begin-method.md)|Obtient l’adresse du premier élément dans le tableau interne de gestionnaires d’événements.|  
|[EventTargetArray::End, méthode](../windows/eventtargetarray-end-method.md)|Obtient l’adresse du dernier élément dans le tableau interne de gestionnaires d’événements.|  
|[EventTargetArray::Length, méthode](../windows/eventtargetarray-length-method.md)|Obtient le nombre actuel d’éléments dans le tableau interne des gestionnaires d’événements.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `EventTargetArray`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** event.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)
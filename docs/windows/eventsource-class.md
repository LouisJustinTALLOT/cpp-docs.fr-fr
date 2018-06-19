---
title: EventSource, classe | Documents Microsoft
ms.custom: ''
ms.date: 03/22/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource
dev_langs:
- C++
helpviewer_keywords:
- EventSource class
ms.assetid: 91f1c072-6af4-44e6-b6d8-ac6d0c688dde
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b2d466b317927cd8de259637450b68b6aaf13bd5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876512"
---
# <a name="eventsource-class"></a>EventSource (classe)
Représente un événement non agile. Les fonctions membres EventSource ajouter, supprimer et appellent des gestionnaires d’événements. Pour les événements agiles, utilisez [AgileEventSource](agileeventsource-class.md). 
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename TDelegateInterface>  
class EventSource;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `TDelegateInterface`  
 L’interface d’un délégué qui représente un gestionnaire d’événements.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[EventSource::EventSource, constructeur](../windows/eventsource-eventsource-constructor.md)|Initialise une nouvelle instance de la classe EventSource.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[EventSource::Add, méthode](../windows/eventsource-add-method.md)|Ajoute le Gestionnaire d’événements représenté par l’interface de délégué spécifié à l’ensemble des gestionnaires d’événements pour l’objet source d’événement actuel.|  
|[EventSource::GetSize, méthode](../windows/eventsource-getsize-method.md)|Récupère le nombre de gestionnaires d’événements associés à l’objet en cours de la source d’événement|  
|[EventSource::InvokeAll, méthode](../windows/eventsource-invokeall-method.md)|Appelle chaque gestionnaire d’événements associé à l’objet source d’événement actuel avec les types d’arguments spécifiés et les arguments.|  
|[EventSource::Remove, méthode](../windows/eventsource-remove-method.md)|Supprime le Gestionnaire d’événements représenté par le jeton d’inscription d’événement spécifié à l’ensemble des gestionnaires d’événements associés à l’objet source d’événement actuel.|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|[EventSource::addRemoveLock_, données de membre](../windows/eventsource-addremovelock-data-member.md)|Synchronise l’accès à la [targets_](../windows/eventsource-targets-data-member.md) tableau lors de l’ajout, la suppression ou appeler des gestionnaires d’événements.|  
|[EventSource::targets_, données de membre](../windows/eventsource-targets-data-member.md)|Tableau d’un ou plusieurs gestionnaires d’événements.|  
|[EventSource::targetsPointerLock_, données de membre](../windows/eventsource-targetspointerlock-data-member.md)|Synchronise l’accès aux membres de données internes, même si les gestionnaires d’événements pour cette source d’événement sont ajoutés, supprimés ou appelé.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `EventSource`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** event.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::wrl Namespace](../windows/microsoft-wrl-namespace.md)
[AgileEventSource classe](agileeventsource-class.md)
---
title: Classe EventSource | Microsoft Docs
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
ms.openlocfilehash: 8805547c5803ae665178330063e6b77b1b3c662e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42596209"
---
# <a name="eventsource-class"></a>EventSource (classe)

Représente un événement non agile. **EventSource** fonctions membres à ajouter, supprimer et appeler des gestionnaires d’événements. Pour les événements agiles, utiliser [AgileEventSource](agileeventsource-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template<typename TDelegateInterface>
class EventSource;
```

### <a name="parameters"></a>Paramètres

*TDelegateInterface*  
L’interface à un délégué qui représente un gestionnaire d’événements.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[EventSource::EventSource, constructeur](../windows/eventsource-eventsource-constructor.md)|Initialise une nouvelle instance de la **EventSource** classe.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[EventSource::Add, méthode](../windows/eventsource-add-method.md)|Ajoute le Gestionnaire d’événements représenté par l’interface de délégué spécifié à l’ensemble des gestionnaires d’événements pour actuel **EventSource** objet.|
|[EventSource::GetSize, méthode](../windows/eventsource-getsize-method.md)|Récupère le nombre de gestionnaires d’événements associés à l’actuel **EventSource** objet|
|[EventSource::InvokeAll, méthode](../windows/eventsource-invokeall-method.md)|Appelle chaque gestionnaire d’événements associé actuel **EventSource** avec les types d’arguments spécifiés et les arguments de l’objet.|
|[EventSource::Remove, méthode](../windows/eventsource-remove-method.md)|Supprime le Gestionnaire d’événements représenté par le jeton d’inscription d’événement spécifié à partir de l’ensemble des gestionnaires d’événements associés à l’actuel **EventSource** objet.|

### <a name="protected-data-members"></a>Membres de données protégés

|Name|Description|
|----------|-----------------|
|[EventSource::addRemoveLock_, données de membre](../windows/eventsource-addremovelock-data-member.md)|Synchronise l’accès à la [targets_](../windows/eventsource-targets-data-member.md) tableau lors de l’ajout, suppression ou appeler des gestionnaires d’événements.|
|[EventSource::targets_, données de membre](../windows/eventsource-targets-data-member.md)|Tableau d’un ou plusieurs gestionnaires d’événements.|
|[EventSource::targetsPointerLock_, données de membre](../windows/eventsource-targetspointerlock-data-member.md)|Synchronise l’accès aux membres de données internes, même lorsque des gestionnaires d’événements pour cette source d’événement sont ajoutés, supprimés ou appelé.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`EventSource`

## <a name="requirements"></a>Configuration requise

**En-tête :** event.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)  
[AgileEventSource, classe](agileeventsource-class.md)
---
title: EventSource::Remove, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::Remove
dev_langs:
- C++
helpviewer_keywords:
- Remove method
ms.assetid: afafedf5-3665-4408-a639-fb6884f7c5f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 00f3275095648a41eb25d10bac1f34637b2ac242
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604570"
---
# <a name="eventsourceremove-method"></a>EventSource::Remove, méthode

Supprime le Gestionnaire d’événements représenté par le jeton d’inscription d’événement spécifié à partir de l’ensemble des gestionnaires d’événements associés à l’actuel **EventSource** objet.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Remove(
   EventRegistrationToken token
);
```

### <a name="parameters"></a>Paramètres

*Jeton*  
Handle qui représente un gestionnaire d’événements. Ce jeton a été retourné lorsque le Gestionnaire d’événements a été inscrit par le [Add()](../windows/eventsource-add-method.md) (méthode).

## <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="remarks"></a>Notes

Pour plus d’informations sur la `EventRegistrationToken` structure, consultez la **Windows::Foundation :: eventregistrationtoken Structure** rubrique dans le **Windows Runtime** documentation de référence.

## <a name="requirements"></a>Configuration requise

**En-tête :** event.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi
[EventSource, classe](../windows/eventsource-class.md)
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
ms.openlocfilehash: 9dd026158a2bbc76e7a3e195bc5346f65821f2b7
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39569493"
---
# <a name="eventsourceremove-method"></a>EventSource::Remove, méthode
Supprime le Gestionnaire d’événements représenté par le jeton d’inscription d’événement spécifié à partir de l’ensemble des gestionnaires d’événements associés à l’actuel **EventSource** objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 Pour plus d’informations sur la structure EventRegistrationToken, consultez le `Windows::Foundation::EventRegistrationToken` rubrique de Structure dans la documentation de référence Windows Runtime.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** event.h  
  
 **Espace de noms :** Microsoft::WRL
 
 ## <a name="see-also"></a>Voir aussi
 [EventSource, classe](../windows/eventsource-class.md)
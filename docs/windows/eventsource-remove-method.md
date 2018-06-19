---
title: EventSource::Remove, méthode | Documents Microsoft
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
ms.openlocfilehash: bbf0480252fca342b8a690e93f92ae14ca5e84c0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874380"
---
# <a name="eventsourceremove-method"></a>EventSource::Remove, méthode
Supprime le Gestionnaire d’événements représenté par le jeton d’inscription d’événement spécifié à l’ensemble des gestionnaires d’événements associés à l’objet source d’événement actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Remove(  
   EventRegistrationToken token  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `token`  
 Handle qui représente un gestionnaire d’événements. Ce jeton a été retourné lorsque le Gestionnaire d’événements a été inscrit par le [Add()](../windows/eventsource-add-method.md) (méthode).  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur la structure EventRegistrationToken, consultez la rubrique de la Structure de Windows::Foundation :: eventregistrationtoken dans la documentation de référence Windows Runtime.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** event.h  
  
 **Espace de noms :** Microsoft::WRL
 
 ## <a name="see-also"></a>Voir aussi
 [EventSource, classe](../windows/eventsource-class.md)
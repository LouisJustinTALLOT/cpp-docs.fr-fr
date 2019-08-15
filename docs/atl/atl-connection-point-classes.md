---
title: Classes de point de connexion ATL
ms.date: 11/04/2016
helpviewer_keywords:
- CFirePropNotifyEvent class, connection point classes
- connection points [C++], ATL classes
- ATL, connection points
- CComDynamicUnkArray class, connection point classes
- CFirePropNotifyEvent class
- CComUnkArray class, connection point classes
ms.assetid: 9582ba71-7ace-4df4-9c9b-1b0636953efc
ms.openlocfilehash: 8644fc087d7f0a651724c40d2868e96c9b6ec96a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491825"
---
# <a name="atl-connection-point-classes"></a>Classes de point de connexion ATL

ATL utilise les classes suivantes pour prendre en charge les points de connexion:

- [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) implémente un point de connexion. L’IID de l’interface sortante qu’il représente est passé en tant que paramètre de modèle.

- [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) implémente le conteneur de point de connexion et gère la `IConnectionPointImpl` liste d’objets.

- [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) implémente un point de connexion représentant l’interface [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) .

- [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) gère un nombre arbitraire de connexions entre le point de connexion et ses récepteurs.

- [CComUnkArray](../atl/reference/ccomunkarray-class.md) gère un nombre prédéfini de connexions comme spécifié par le paramètre de modèle.

- [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) avertit le récepteur d’un client que la propriété d’un objet a été modifiée ou qu’il va être modifié.

- [IDispEventImpl](../atl/reference/idispeventimpl-class.md) prend en charge les points de connexion pour un objet ATL com. Ces points de connexion sont mappés à un mappage de récepteur d’événements, fourni par votre objet COM.

- [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) fonctionne conjointement avec le mappage de récepteur d’événements dans votre classe pour acheminer les événements vers la fonction de gestionnaire appropriée.

## <a name="see-also"></a>Voir aussi

[Point de connexion](../atl/atl-connection-points.md)

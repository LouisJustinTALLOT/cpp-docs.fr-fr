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
ms.openlocfilehash: f3794b5c9e4f6297cca6611929c75d0b0133557e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265234"
---
# <a name="atl-connection-point-classes"></a>Classes de point de connexion ATL

ATL utilise les classes suivantes pour prendre en charge des points de connexion :

- [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) implémente un point de connexion. IID de l’interface sortante qu’il représente est passé comme paramètre de modèle.

- [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) implémente le conteneur de point de connexion et gère la liste des `IConnectionPointImpl` objets.

- [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) implémente un point de connexion représentant la [IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) interface.

- [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) gère un nombre arbitraire de connexions entre le point de connexion et ses récepteurs.

- [CComUnkArray](../atl/reference/ccomunkarray-class.md) gère un nombre prédéfini de connexions spécifié par le paramètre de modèle.

- [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) informe un récepteur de client qui a changé de propriété d’un objet ou va être modifiée.

- [IDispEventImpl](../atl/reference/idispeventimpl-class.md) prend en charge les points de connexion pour un objet COM ATL. Ces points de connexion sont mappés avec une table de récepteur d’événements, qui est fournie par votre objet COM.

- [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) fonctionne conjointement avec la table de récepteur d’événements dans votre classe pour acheminer les événements à la fonction gestionnaire approprié.

## <a name="see-also"></a>Voir aussi

[Point de connexion](../atl/atl-connection-points.md)

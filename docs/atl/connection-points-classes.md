---
title: Classes de Points de connexion (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- classes [C++], connection points
- connection points classes
ms.assetid: 076365fa-299a-4dce-84c3-a5dff0e0da1f
ms.openlocfilehash: 8e1ee67f75af1fa38693f7ddb487580ab733cc58
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62250812"
---
# <a name="connection-points-classes"></a>Classes de Points de connexion

Les classes suivantes fournissent la prise en charge des points de connexion :

- [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) implémente un conteneur de point de connexion.

- [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) implémente un point de connexion.

- [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) implémente un point de connexion représentant la [IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) interface.

- [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) gère un nombre illimité de connexions entre un point de connexion et ses récepteurs.

- [CComUnkArray](../atl/reference/ccomunkarray-class.md) gère un nombre fixe de connexions entre un point de connexion et ses récepteurs.

- [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) informe un récepteur de client qui a changé de propriété d’un objet ou va être modifiée.

- [IDispEventImpl](../atl/reference/idispeventimpl-class.md) prend en charge les points de connexion pour un objet COM ATL. Ces points de connexion sont mappés avec une table de récepteur d’événements, qui est fournie par votre objet COM.

- [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) fonctionne conjointement avec le récepteur d’événements mappe dans votre classe pour acheminer les événements à la fonction gestionnaire approprié.

## <a name="related-articles"></a>Articles connexes

[Points de connexion](../atl/atl-connection-points.md)

[Gestion des événements et ATL](../atl/event-handling-and-atl.md)

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../atl/atl-class-overview.md)<br/>
[Macros de point de connexion](../atl/reference/connection-point-macros.md)<br/>
[Fonctions globales de point de connexion](../atl/reference/connection-point-global-functions.md)

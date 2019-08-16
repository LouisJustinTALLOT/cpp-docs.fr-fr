---
title: Classes de points de connexion (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- classes [C++], connection points
- connection points classes
ms.assetid: 076365fa-299a-4dce-84c3-a5dff0e0da1f
ms.openlocfilehash: 0dba06b072e1e9ca545ccbea196fcfe371b02157
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492445"
---
# <a name="connection-points-classes"></a>Classes des points de connexion

Les classes suivantes fournissent la prise en charge des points de connexion:

- [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) Implémente un conteneur de point de connexion.

- [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) Implémente un point de connexion.

- [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) Implémente un point de connexion représentant l’interface [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) .

- [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) Gère des connexions illimitées entre un point de connexion et ses récepteurs.

- [CComUnkArray](../atl/reference/ccomunkarray-class.md) Gère un nombre fixe de connexions entre un point de connexion et ses récepteurs.

- [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) Avertit le récepteur d’un client que la propriété d’un objet a été modifiée ou qu’il est sur le paragraphe d’être modifié.

- [IDispEventImpl](../atl/reference/idispeventimpl-class.md) Fournit la prise en charge des points de connexion pour un objet ATL COM. Ces points de connexion sont mappés à un mappage de récepteur d’événements, fourni par votre objet COM.

- [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) Fonctionne conjointement avec le mappage de récepteur d’événements dans votre classe pour acheminer les événements vers la fonction de gestionnaire appropriée.

## <a name="related-articles"></a>Articles connexes

[Points de connexion](../atl/atl-connection-points.md)

[Gestion des événements et ATL](../atl/event-handling-and-atl.md)

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../atl/atl-class-overview.md)<br/>
[Macros de point de connexion](../atl/reference/connection-point-macros.md)<br/>
[Fonctions globales de point de connexion](../atl/reference/connection-point-global-functions.md)

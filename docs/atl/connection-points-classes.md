---
title: Classes de Points de connexion (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.connection
dev_langs:
- C++
helpviewer_keywords:
- classes [C++], connection points
- connection points classes
ms.assetid: 076365fa-299a-4dce-84c3-a5dff0e0da1f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e24d6333faee842227edb09ea05aa6a1f8b0d9a0
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43763599"
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

[Vue d’ensemble de la classe](../atl/atl-class-overview.md)   
[Macros de Point de connexion](../atl/reference/connection-point-macros.md)   
[Fonctions globales de point de connexion](../atl/reference/connection-point-global-functions.md)


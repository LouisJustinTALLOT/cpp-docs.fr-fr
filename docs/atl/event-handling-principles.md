---
title: Principes de manipulation d’événements (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, implementing
- event handling, advising event sources
- interfaces, event and event sink
- dual interfaces, event interfaces
- event handling, dual event interfaces
ms.assetid: d17ca7cb-54f2-4658-ab8b-b721ac56801d
ms.openlocfilehash: 2e810853e7c81f279039e0b3dfda5199d38deee2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319563"
---
# <a name="event-handling-principles"></a>Principes de manipulation d’événements

Il y a trois étapes communes à toutes les manipulations d’événements. Vous devrez :

- Implémentez l’interface événement sur votre objet.

- Informez la source de l’événement que votre objet veut recevoir des événements.

- Déconsevez la source de l’événement lorsque votre objet n’a plus besoin de recevoir des événements.

La façon dont vous implémenterez l’interface événementiel dépendra de son type. Une interface événementiel peut être vtable, double, ou un dispinterface. C’est au concepteur de la source de l’événement de définir l’interface; c’est à vous de mettre en œuvre cette interface.

> [!NOTE]
> Bien qu’il n’y ait aucune raison technique qu’une interface d’événement ne peut pas être double, il ya un certain nombre de bonnes raisons de conception pour éviter l’utilisation de duels. Cependant, il s’agit d’une décision prise par le concepteur / implémenteur de la *source*de l’événement . Puisque vous travaillez du point `sink`de vue de l’événement, vous devez tenir compte de la possibilité que vous n’ayez pas d’autre choix que de mettre en œuvre une interface double événement. Pour plus d’informations sur les interfaces doubles, voir [Double Interfaces et ATL](../atl/dual-interfaces-and-atl.md).

Conseiller la source de l’événement peut être décomposé en trois étapes:

- Requête de l’objet source pour [IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer).

- Appelez [IConnectionPointContainer::FindConnectionPoint](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) passant l’IID de l’interface événementiel qui vous intéresse. En cas de succès, cela retournera l’interface [IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint) sur un objet point de connexion.

- Appelez [IConnectionPoint::Conseiller](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-advise) `IUnknown` de passer le puits de l’événement. En cas de succès, cela retournera un `DWORD` cookie représentant la connexion.

Une fois que vous avez enregistré avec succès votre intérêt à recevoir des événements, les méthodes sur l’interface événementiel de votre objet seront appelées en fonction des événements déclenchés par l’objet source. Lorsque vous n’avez plus besoin de recevoir des événements, vous pouvez passer le cookie vers le point de connexion via [IConnectionPoint::Unadvise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-unadvise). Cela brisera la connexion entre la source et l’évier.

Veillez à éviter les cycles de référence lors de la gestion des événements.

## <a name="see-also"></a>Voir aussi

[Manipulation de l’événement](../atl/event-handling-and-atl.md)

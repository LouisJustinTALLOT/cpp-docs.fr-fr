---
description: En savoir plus sur les principes de gestion des événements
title: Principes de gestion des événements (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, implementing
- event handling, advising event sources
- interfaces, event and event sink
- dual interfaces, event interfaces
- event handling, dual event interfaces
ms.assetid: d17ca7cb-54f2-4658-ab8b-b721ac56801d
ms.openlocfilehash: 29b9542b4e026d320857990a0ef6253f310535e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147977"
---
# <a name="event-handling-principles"></a>Principes de gestion des événements

Il existe trois étapes communes à la gestion des événements. Vous devez :

- Implémentez l’interface d’événement sur votre objet.

- Conseillez à la source de l’événement que votre objet souhaite recevoir des événements.

- Désconseillez la source de l’événement lorsque votre objet n’a plus besoin de recevoir des événements.

La façon dont vous implémenterez l’interface d’événement dépend de son type. Une interface d’événement peut être vtable, double ou dispinterface. C’est au concepteur de la source d’événements de définir l’interface ; C’est à vous de mettre en œuvre cette interface.

> [!NOTE]
> Bien qu’il n’existe aucune raison technique pour laquelle une interface d’événement ne peut pas être double, il existe un certain nombre de bonnes raisons de conception afin d’éviter l’utilisation de doubles. Toutefois, il s’agit d’une décision prise par le concepteur/implémenteur de la *source* de l’événement. Dans la mesure où vous travaillez du point de vue de l’événement `sink` , vous devez autoriser la possibilité que vous ne disposiez pas d’un choix, mais d’implémenter une interface d’événement double. Pour plus d’informations sur les interfaces doubles, consultez [interfaces doubles et ATL](../atl/dual-interfaces-and-atl.md).

L’avertissement de la source de l’événement peut être divisé en trois étapes :

- Interrogez l’objet source pour [IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer).

- Appelez [IConnectionPointContainer :: FindConnectionPoint](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) en passant l’IID de l’interface d’événement qui vous intéresse. En cas de réussite, l’interface [IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint) est retournée sur un objet point de connexion.

- Appelez [IConnectionPoint :: Advise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-advise) en passant le `IUnknown` du récepteur d’événements. En cas de réussite, un `DWORD` cookie représentant la connexion est retourné.

Une fois que vous avez correctement enregistré votre intérêt pour la réception d’événements, les méthodes de l’interface d’événement de votre objet sont appelées en fonction des événements déclenchés par l’objet source. Lorsque vous n’avez plus besoin de recevoir des événements, vous pouvez retransmettre le cookie au point de connexion via [IConnectionPoint :: Unadvise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-unadvise). Cela rompt la connexion entre la source et le récepteur.

Veillez à éviter les cycles de référence lors de la gestion des événements.

## <a name="see-also"></a>Voir aussi

[Gestion des événements](../atl/event-handling-and-atl.md)

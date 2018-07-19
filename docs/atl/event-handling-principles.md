---
title: Événements de gestion des principes (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- event handling, implementing
- event handling, advising event sources
- interfaces, event and event sink
- dual interfaces, event interfaces
- event handling, dual event interfaces
ms.assetid: d17ca7cb-54f2-4658-ab8b-b721ac56801d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 239ea94343652d379048bbeee87d2650d3f1ed72
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852534"
---
# <a name="event-handling-principles"></a>Principes de gestion des événements
Il existe trois étapes communes à la gestion des événements. Vous devrez :  
  
-   Implémentez l’interface d’événement sur votre objet.  
  
-   Avertir la source d’événements que votre objet souhaite recevoir des événements.  
  
-   Unadvise sur la source d’événements lorsque votre objet n’a plus besoin de recevoir des événements.  
  
 La façon que vous allez implémenter l’interface d’événement dépend de son type. Une interface d’événement peut être vtable, double ou une dispinterface. Il incombe au Concepteur de la source d’événement pour définir l’interface ; C’est à vous permettent d’implémenter cette interface.  
  
> [!NOTE]
>  Bien qu’il n’y a aucune raison technique une interface d’événement ne peut pas être double, il existe de nombreuses raisons d’une bonne conception afin d’éviter l’utilisation de duals. Toutefois, il s’agit une décision prise par le concepteur/implémenteur de l’événement *source*. Dans la mesure où vous travaillez à partir de la perspective de l’événement `sink`, vous devez tenir compte du fait que vous ne disposez pas de n’importe quel choix mais pour implémenter une interface d’événement double. Pour plus d’informations sur les interfaces doubles, consultez [Interfaces doubles et ATL](../atl/dual-interfaces-and-atl.md).  
  
 Avertissement de la source d’événement peut être divisé en trois étapes :  
  
-   Interroger l’objet source pour [IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857).  
  
-   Appelez [IConnectionPointContainer::FindConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms692476) en passant l’IID de l’interface d’événement qui vous intéresse. Si réussie, elle retournera le [IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318) interface sur un objet de point de connexion.  
  
-   Appelez [IConnectionPoint::Advise](http://msdn.microsoft.com/library/windows/desktop/ms678815) en passant le `IUnknown` du récepteur d’événements. Si réussie, elle retournera un `DWORD` cookie représentant la connexion.  
  
 Une fois que vous avez correctement enregistré votre intérêt pour la réception d’événements, les méthodes sur votre interface de l’objet événement sont appelées selon les événements déclenchés par l’objet source. Lorsque vous n’avez plus besoin de recevoir des événements, vous pouvez transmettre le cookie au point de connexion par le biais de [IConnectionPoint::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms686608). Cela arrêtera la connexion entre la source et récepteur.  
  
 Veillez à éviter de référence des cycles de traitement des événements.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des événements](../atl/event-handling-and-atl.md)


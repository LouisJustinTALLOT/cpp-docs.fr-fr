---
title: Principes (ATL) de la gestion des événements | Documents Microsoft
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
ms.openlocfilehash: cb7577dc7d9fb58f43ee67d5e5b8f00393dca1bf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32355446"
---
# <a name="event-handling-principles"></a>Principes de la gestion des événements
Il existe trois étapes communes à la gestion des événements. Vous devez :  
  
-   Implémentez l’interface d’événement sur votre objet.  
  
-   Informer la source d’événements que votre objet souhaite recevoir des événements.  
  
-   Déconseiller la source d’événements lorsque votre objet n’a plus besoin de recevoir des événements.  
  
 La méthode que vous allez implémenter l’interface d’événement dépend de son type. Une interface d’événement peut être vtable, double ou une dispinterface. Il incombe au Concepteur de la source d’événements pour définir l’interface ; C’est à vous pour implémenter cette interface.  
  
> [!NOTE]
>  Bien qu’il n’y a pas d’ordre technique et une interface d’événement ne doit pas être en double, il existe de nombreuses raisons d’une bonne conception pour éviter l’utilisation de duals. Toutefois, c’est une décision effectuée par le concepteur/implémenteur de l’événement *source*. Étant donné que vous travaillez à partir de la perspective de l’événement `sink`, vous avez besoin pour permettre la possibilité que vous n’êtes pas un choix mais pour implémenter une interface d’événement double. Pour plus d’informations sur les interfaces doubles, consultez [Interfaces doubles et ATL](../atl/dual-interfaces-and-atl.md).  
  
 Avertissement de la source d’événement peut être répartie en trois étapes :  
  
-   Interroger l’objet source pour [IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857).  
  
-   Appelez [IConnectionPointContainer::FindConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms692476) en passant l’IID de l’interface d’événement qui vous intéresse. Si réussie, elle retournera le [IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318) interface sur un objet de point de connexion.  
  
-   Appelez [IConnectionPoint::Advise](http://msdn.microsoft.com/library/windows/desktop/ms678815) en passant le **IUnknown** du récepteur d’événements. Si réussie, elle retournera un `DWORD` cookie qui représente la connexion.  
  
 Une fois que vous avez correctement inscrit votre intérêt de recevoir des événements, méthodes sur l’interface d’événement de votre objet sont appelées selon les événements déclenchés par l’objet source. Lorsque vous n’avez plus besoin de recevoir des événements, vous pouvez passer le cookie au point de connexion via [IConnectionPoint::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms686608). Cela rompt la connexion entre la source et le récepteur.  
  
 Soyez prudent afin d’éviter de référence des cycles de la gestion des événements.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des événements](../atl/event-handling-and-atl.md)


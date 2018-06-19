---
title: 'Conteneurs : États d’élément Client | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE containers [MFC], client-item states
- states, OLE container client-item
- lifetime, lifetime states and OLE container client items
- client items and OLE containers
ms.assetid: e7021caa-bd07-4adb-976e-f5f3d025bc53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5046ea7f3f3775cfe0009afe50f33a6ce6723cc0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342171"
---
# <a name="containers-client-item-states"></a>Conteneurs : états d'élément client
Cet article explique les différents états par lesquels passe un élément client pendant son cycle de vie.  
  
 Un élément client passe par plusieurs états lorsqu'il est créé, activé, modifié et enregistré. Chaque fois qu’état change l’élément, le framework appelle [COleClientItem::OnChange](../mfc/reference/coleclientitem-class.md#onchange) avec la `OLE_CHANGED_STATE` notification. Le deuxième paramètre est une valeur à partir de la **COleClientItem::ItemState** énumération. Il peut avoir l'une des valeurs suivantes :  
  
-   **COleClientItem::emptyState**  
  
-   **COleClientItem::loadedState**  
  
-   **COleClientItem::openState**  
  
-   **COleClientItem::activeState**  
  
-   **COleClientItem::activeUIState**  
  
 Dans l'état vide, un élément client n'est pas encore complètement un élément. De la mémoire lui a été allouée, mais elle n'a pas encore été initialisée avec les données de l'élément OLE. Il s’agit d’état est un élément client lorsqu’il a été créé via un appel à **nouveau** mais n’a ne pas encore passé la deuxième étape de la création en deux étapes.  
  
 Dans la deuxième étape, effectuée via un appel à `COleClientItem::CreateFromFile` ou un autre **CreateFrom *** xxxx* (fonction), l’élément est complètement créé. Les données OLE (d'un fichier ou d'une autre source, telle que le Presse-papiers) ont été associées à l'objet dérivé de `COleClientItem`. Maintenant l'élément se trouve dans l'état chargé.  
  
 Lorsqu'un élément a été ouvert dans la fenêtre du serveur au lieu d'être ouvert sur place dans le document du conteneur, il se trouve dans l'état ouvert (ou entièrement ouvert). Dans cet état, une hachure croisée est généralement dessinée sur la représentation de l'élément dans la fenêtre du conteneur pour indiquer que l'élément est actif ailleurs.  
  
 Lorsqu'un élément a été activé sur place, il ne passe généralement que brièvement par l'état actif. Il passe ensuite à l’état actif de l’interface utilisateur, dans lequel le serveur a fusionné ses menus, barres d’outils et autres composants d’interface utilisateur avec ceux du conteneur. La présence de ces composants d'interface utilisateur fait la distinction entre l'état actif de l'interface utilisateur et l'état actif. Sinon, l'état actif s'apparente à l'état actif de l'interface utilisateur. Si le serveur prend en charge l'annulation, il doit conserver les informations d'état d'annulation de l'élément OLE jusqu'à ce que ce dernier atteigne l'état chargé ou ouvert.  
  
## <a name="see-also"></a>Voir aussi  
 [Conteneurs](../mfc/containers.md)   
 [Activation](../mfc/activation-cpp.md)   
 [Conteneurs : Notifications d’élément Client](../mfc/containers-client-item-notifications.md)   
 [Dispositifs de suivi](../mfc/trackers.md)   
 [CRectTracker, classe](../mfc/reference/crecttracker-class.md)

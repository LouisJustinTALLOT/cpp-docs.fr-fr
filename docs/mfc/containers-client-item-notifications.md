---
title: 'Conteneurs : Notifications d’élément Client | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], container client item
- OLE containers [MFC], client-item notifications
- client items and OLE containers
ms.assetid: e1f1c427-01f5-45f2-b496-c5bce3d76340
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d76717e68e37769cf55dceb4492ed78031c49e10
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928222"
---
# <a name="containers-client-item-notifications"></a>Conteneurs : notifications d'élément client
Cet article présente les fonctions substituables que le framework MFC appelle lorsque les applications serveur modifient des éléments dans le document de votre application cliente.  
  
 [COleClientItem](../mfc/reference/coleclientitem-class.md) définit plusieurs fonctions substituables qui sont appelées en réponse aux demandes à partir de l’application du composant, également appelé l’application serveur. Ces fonctions substituables agissent généralement comme des notifications. Elles informent l'application conteneur de divers événements, par exemple, un défilement, une activation ou un changement de position, ainsi que des changements effectués par l'utilisateur en modifiant ou en manipulant autrement l'élément.  
  
 Le framework informe votre application conteneur des modifications via un appel à `COleClientItem::OnChange`, une fonction substituable dont l'implémentation est requise. Cette fonction protégée reçoit deux arguments. Le premier spécifie la raison pour laquelle le serveur a modifié l'élément :  
  
|Notification|Signification|  
|------------------|-------------|  
|**OLE_CHANGED**|L'apparence de l'élément OLE a changé.|  
|**OLE_SAVED**|L'élément OLE a été enregistré.|  
|**OLE_CLOSED**|L'élément OLE a été fermé.|  
|**OLE_RENAMED**|Le document du serveur contenant l'élément OLE a été renommé.|  
|**OLE_CHANGED_STATE**|L'élément OLE est passé d'un état à un autre.|  
|**OLE_CHANGED_ASPECT**|L'aspect de l'élément OLE a été modifié par le framework.|  
  
 Ces valeurs sont comprises entre le **OLE_NOTIFICATION** énumération, qui est définie dans AFXOLE. H.  
  
 Le deuxième argument de cette fonction spécifie la manière dont l’élément est modifié ou l’état dans lequel il est passé :  
  
|Lorsque le premier argument est|Deuxième argument|  
|----------------------------|---------------------|  
|**OLE_SAVED** ou **OLE_CLOSED**|N'est pas utilisé.|  
|**OLE_CHANGED**|Spécifie l'aspect de l'élément OLE modifié.|  
|**OLE_CHANGED_STATE**|Décrit l’état en cours (*emptyState*, *loadedState*, *openState*, *activeState*, ou  *activeUIState*).|  
  
 Pour plus d’informations sur les États d’un élément client peut assumer, consultez [conteneurs : États Client-élément](../mfc/containers-client-item-states.md).  
  
 Le framework appelle `COleClientItem::OnGetItemPosition` lorsqu'un élément est activé pour la modification sur place. L'implémentation est requise pour les applications qui prennent en charge la modification sur place. L'Assistant Application MFC fournit une implémentation de base, qui assigne les coordonnées de l'élément à l'objet `CRect` passé comme argument à `OnGetItemPosition`.  
  
 Si la position ou la taille d'un élément OLE change lors de la modification sur place, les informations du conteneur relatives aux rectangles de découpage et à la position de l'élément doivent être mises à jour et le serveur doit recevoir les informations concernant ces modifications. Le framework appelle `COleClientItem::OnChangeItemPosition` à cet effet. L'Assistant Application MFC fournit une substitution qui appelle la fonction de la classe de base. Vous devez modifier la fonction que l'Assistant Application écrit pour votre classe dérivée de `COleClientItem` afin qu'elle puisse mettre à jour les informations conservées par votre objet d'élément client.  
  
## <a name="see-also"></a>Voir aussi  
 [Conteneurs](../mfc/containers.md)   
 [Conteneurs : États d’élément Client](../mfc/containers-client-item-states.md)   
 [COleClientItem::OnChangeItemPosition](../mfc/reference/coleclientitem-class.md#onchangeitemposition)


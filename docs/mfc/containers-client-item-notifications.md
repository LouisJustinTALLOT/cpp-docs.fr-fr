---
title: "Conteneurs : notifications d'élément client"
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], container client item
- OLE containers [MFC], client-item notifications
- client items and OLE containers
ms.assetid: e1f1c427-01f5-45f2-b496-c5bce3d76340
ms.openlocfilehash: 54b1b2a64685b00fb265e0f80c1f6ad878a7da85
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623017"
---
# <a name="containers-client-item-notifications"></a>Conteneurs : notifications d'élément client

Cet article présente les fonctions substituables que le framework MFC appelle lorsque les applications serveur modifient des éléments dans le document de votre application cliente.

[COleClientItem](reference/coleclientitem-class.md) définit plusieurs fonctions substituables qui sont appelées en réponse aux demandes de l’application de composant, également appelée application serveur. Ces fonctions substituables agissent généralement comme des notifications. Elles informent l'application conteneur de divers événements, par exemple, un défilement, une activation ou un changement de position, ainsi que des changements effectués par l'utilisateur en modifiant ou en manipulant autrement l'élément.

Le framework informe votre application conteneur des modifications via un appel à `COleClientItem::OnChange`, une fonction substituable dont l'implémentation est requise. Cette fonction protégée reçoit deux arguments. Le premier spécifie la raison pour laquelle le serveur a modifié l'élément :

|Notification|Signification|
|------------------|-------------|
|**OLE_CHANGED**|L'apparence de l'élément OLE a changé.|
|**OLE_SAVED**|L'élément OLE a été enregistré.|
|**OLE_CLOSED**|L'élément OLE a été fermé.|
|**OLE_RENAMED**|Le document du serveur contenant l'élément OLE a été renommé.|
|**OLE_CHANGED_STATE**|L'élément OLE est passé d'un état à un autre.|
|**OLE_CHANGED_ASPECT**|L'aspect de l'élément OLE a été modifié par le framework.|

Ces valeurs proviennent de l’énumération **OLE_NOTIFICATION** , qui est définie dans AFXOLE. Manutention.

Le deuxième argument de cette fonction spécifie la manière dont l'élément est modifié ou l'état dans lequel il est passé :

|Lorsque le premier argument est|Deuxième argument|
|----------------------------|---------------------|
|**OLE_SAVED** ou **OLE_CLOSED**|N'est pas utilisé.|
|**OLE_CHANGED**|Spécifie l'aspect de l'élément OLE modifié.|
|**OLE_CHANGED_STATE**|Décrit l’État entré (*emptyState*, *loadedState*, *openState*, *ActiveState*ou *activeUIState*).|

Pour plus d’informations sur les États qu’un élément client peut supposer, consultez [conteneurs : États du client-élément](containers-client-item-states.md).

Le framework appelle `COleClientItem::OnGetItemPosition` lorsqu'un élément est activé pour la modification sur place. L'implémentation est requise pour les applications qui prennent en charge la modification sur place. L'Assistant Application MFC fournit une implémentation de base, qui assigne les coordonnées de l'élément à l'objet `CRect` passé comme argument à `OnGetItemPosition`.

Si la position ou la taille d'un élément OLE change lors de la modification sur place, les informations du conteneur relatives aux rectangles de découpage et à la position de l'élément doivent être mises à jour et le serveur doit recevoir les informations concernant ces modifications. Le framework appelle `COleClientItem::OnChangeItemPosition` à cet effet. L'Assistant Application MFC fournit une substitution qui appelle la fonction de la classe de base. Vous devez modifier la fonction que l'Assistant Application écrit pour votre classe dérivée de `COleClientItem` afin qu'elle puisse mettre à jour les informations conservées par votre objet d'élément client.

## <a name="see-also"></a>Voir aussi

[Containers](containers.md)<br/>
[Conteneurs : états d’élément client](containers-client-item-states.md)<br/>
[COleClientItem :: OnChangeItemPosition](reference/coleclientitem-class.md#onchangeitemposition)

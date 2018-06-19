---
title: 'Serveurs : Éléments du serveur | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- server items, implementing
- servers [MFC], server items
- architecture [MFC], server-item
- server items
- OLE server applications [MFC], server items
ms.assetid: 28ba81a1-726a-4728-a52d-68bc7efd5a3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e83b75183fe226b4ff384a00b0b5260caba01efa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382500"
---
# <a name="servers-server-items"></a>Serveurs : éléments du serveur
Lorsqu'un conteneur lance un serveur afin qu'un utilisateur puisse modifier un élément OLE incorporé ou lié, l'application serveur "crée un élément du serveur." L'élément du serveur, qui est un objet d'une classe dérivé de `COleServerItem`, fournit une interface entre le document serveur et l'application conteneur.  
  
 La classe `COleServerItem` définit plusieurs fonctions membres substituables appelées par OLE, généralement en réponse aux requêtes du conteneur. Les éléments du serveur peuvent représenter une partie du document serveur ou le document entier. Lorsqu'un élément d'OLE est incorporé dans le document conteneur, l'élément du serveur représente le document serveur tout entier. Lorsque l'élément OLE est lié, l'élément du serveur peut représenter une partie du document serveur ou le document entier, selon que la liaison est faite vers une partie ou vers le tout.  
  
 Dans le [HIERSVR](../visual-cpp-samples.md) exemple, par exemple, la classe d’élément de serveur, **CServerItem**, a un membre qui est un pointeur vers un objet de la classe **CServerNode**. Le **CServerNode** objet est un nœud dans le document de l’application HIERSVR, qui est une arborescence. Lorsque le **CServerNode** objet est le nœud racine, le **CServerItem** objet représente l’ensemble du document. Lorsque le **CServerNode** objet est un nœud enfant, le **CServerItem** objet représente une partie du document. Consultez l’exemple OLE MFC [HIERSVR](../visual-cpp-samples.md) pour obtenir un exemple de cette interaction.  
  
##  <a name="_core_implementing_server_items"></a> Implémenter des éléments de serveur  
 Si vous utilisez l’Assistant Application pour générer le code de démarrage pour votre application, tout ce que vous devez effectuer pour inclure les éléments du serveur dans votre code de démarrage est de choisir l’une des options de serveur à partir de la page Options OLE. Si vous ajoutez des éléments du serveur à une application existante, procédez comme suit :  
  
#### <a name="to-implement-a-server-item"></a>Pour implémenter un élément du serveur  
  
1.  Dérivez une classe de `COleServerItem`.  
  
2.  Dans votre classe dérivée, substituez la fonction membre `OnDraw`.  
  
     Le framework appelle `OnDraw` pour afficher l'élément OLE dans un métafichier. L'application conteneur utilise ce métafichier pour afficher l'élément. La classe d'affichage de votre application a également une fonction membre `OnDraw`, utilisée pour afficher l'élément lorsque l'application serveur est active.  
  
3.  Implémentez une substitution de `OnGetEmbeddedItem` pour votre classe de document serveur. Pour plus d’informations, consultez l’article [serveurs : implémentation des Documents serveur](../mfc/servers-implementing-server-documents.md) et l’exemple OLE MFC [HIERSVR](../visual-cpp-samples.md).  
  
4.  Implémentez la fonction membre `OnGetExtent` de la classe d'élément du serveur. Le framework appelle cette fonction pour extraire la taille de l'élément. L'implémentation par défaut n'exécute aucune opération.  
  
##  <a name="_core_a_tip_for_server.2d.item_architecture"></a> Une info-bulle pour l’Architecture de l’élément de serveur  
 Comme indiqué dans [implémentation des éléments serveur](#_core_implementing_server_items), serveur d’applications doit être en mesure d’afficher les éléments dans la vue du serveur et dans un métafichier utilisé par l’application conteneur. Dans architecture d’application de la bibliothèque Microsoft Foundation classes, la classe d’affichage `OnDraw` fonction membre restitue l’élément lorsqu’il est modifié (voir [CView::OnDraw](../mfc/reference/cview-class.md#ondraw) dans le *référence de bibliothèque de classes* ). L’élément du serveur `OnDraw` restitue l’élément dans un métafichier dans tous les autres cas (consultez [COleServerItem::OnDraw](../mfc/reference/coleserveritem-class.md#ondraw)).  
  
 Vous pouvez éviter la duplication de code en écrivant des fonctions d'assistance dans la classe du document serveur et en les appelant à partir des fonctions `OnDraw` dans vos classes d'affichage et d'éléments du serveur. L’exemple OLE MFC [HIERSVR](../visual-cpp-samples.md) utilise cette stratégie : les fonctions **CServerView::OnDraw** et **CServerItem::OnDraw** appellent toutes deux **CServerDoc::DrawTree**  pour restituer l’élément.  
  
 La vue et l'élément ont tous deux des fonctions membres `OnDraw` car le dessin est effectué dans différentes conditions. L'affichage doit prendre en compte des facteurs tels que le zoom, la taille et l'extension de la sélection, la réduction et les éléments d'interface utilisateur tels que les barres de défilement. L'élément du serveur, en revanche, dessine toujours l'objet OLE entier.  
  
 Pour plus d’informations, consultez [CView::OnDraw](../mfc/reference/cview-class.md#ondraw), [COleServerItem](../mfc/reference/coleserveritem-class.md), [COleServerItem::OnDraw](../mfc/reference/coleserveritem-class.md#ondraw), et [COleServerDoc::OnGetEmbeddedItem](../mfc/reference/coleserverdoc-class.md#ongetembeddeditem)dans les *référence de bibliothèque de classe*.  
  
## <a name="see-also"></a>Voir aussi  
 [Serveurs](../mfc/servers.md)


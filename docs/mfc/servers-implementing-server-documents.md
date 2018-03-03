---
title: "Serveurs : Implémentation des Documents serveur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- OLE server applications [MFC], managing server documents
- OLE server applications [MFC], implementing OLE servers
- servers, server documents
- server documents [MFC], implementing
ms.assetid: cca1451a-ad09-47ed-b56e-bccd78fc86d1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1c4b8618e4951ac499d504cc68b0552ea45eed03
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="servers-implementing-server-documents"></a>Serveurs : implémentation de documents de serveur
Cet article explique les étapes à suivre pour implémenter correctement un document serveur si vous n’avez pas spécifié l’option serveur OLE dans l’Assistant application.  
  
#### <a name="to-define-a-server-document-class"></a>Pour définir une classe de document serveur  
  
1.  Dérivez votre classe de document de `COleServerDoc` au lieu de **CDocument**.  
  
2.  Créer une classe d’élément serveur dérivée `COleServerItem`.  
  
3.  Implémentez la `OnGetEmbeddedItem` fonction membre de votre classe de document serveur.  
  
     `OnGetEmbeddedItem`est appelée lorsque l’utilisateur d’une application conteneur crée ou modifie un élément incorporé. Elle doit retourner un élément qui représente l’ensemble du document. Cela doit être un objet de votre `COleServerItem`-classe dérivée.  
  
4.  Remplacer la `Serialize` fonction membre à sérialiser le contenu du document. Vous n’avez pas besoin de sérialiser la liste des éléments de serveur, sauf si vous les utilisez pour représenter les données natives dans votre document. Pour plus d’informations, consultez *implémentation des éléments serveur* dans l’article [serveurs : éléments du serveur](../mfc/servers-server-items.md).  
  
 Lorsqu’un document serveur est créé, le framework enregistre automatiquement le document avec les DLL système OLE. Ainsi, les DLL d’identifier les documents de serveur.  
  
 Pour plus d’informations, consultez [COleServerItem](../mfc/reference/coleserveritem-class.md) et [COleServerDoc](../mfc/reference/coleserverdoc-class.md) dans les *Class Library Reference*.  
  
## <a name="see-also"></a>Voir aussi  
 [Serveurs](../mfc/servers.md)   
 [Serveurs : Éléments du serveur](../mfc/servers-server-items.md)   
 [Serveurs : Implémentation d’un serveur](../mfc/servers-implementing-a-server.md)   
 [Serveurs : implémentations de fenêtres frame sur place](../mfc/servers-implementing-in-place-frame-windows.md)


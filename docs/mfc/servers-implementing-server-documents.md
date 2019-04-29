---
title: 'serveurs : Implémentation de Documents de serveur'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], managing server documents
- OLE server applications [MFC], implementing OLE servers
- servers, server documents
- server documents [MFC], implementing
ms.assetid: cca1451a-ad09-47ed-b56e-bccd78fc86d1
ms.openlocfilehash: 17ced1cdb0b40b13fbda68150030efde5735ba7b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307911"
---
# <a name="servers-implementing-server-documents"></a>serveurs : Implémentation de Documents de serveur

Cet article explique les étapes à suivre pour implémenter correctement un document serveur si vous n’avez pas spécifié l’option de serveur OLE dans l’Assistant application.

#### <a name="to-define-a-server-document-class"></a>Pour définir une classe de document serveur

1. Dérivez votre classe de document à partir de `COleServerDoc` au lieu de `CDocument`.

1. Créer une classe d’élément serveur dérivée `COleServerItem`.

1. Implémentez le `OnGetEmbeddedItem` fonction membre de votre classe de document serveur.

   `OnGetEmbeddedItem` est appelée lorsque l’utilisateur d’une application conteneur crée ou modifie un élément incorporé. Elle doit retourner un élément qui représente la totalité du document. Cela doit être un objet de votre `COleServerItem`-classe dérivée.

1. Remplacer le `Serialize` fonction membre à sérialiser le contenu du document. Vous n’avez pas besoin de sérialiser la liste des éléments de serveur, sauf si vous les utilisez pour représenter les données natives dans votre document. Pour plus d’informations, consultez *implémentation des éléments serveur* dans l’article [serveurs : Éléments de serveur](../mfc/servers-server-items.md).

Lorsqu’un document serveur est créé, le framework enregistre automatiquement le document avec les DLL système OLE. Ainsi, les DLL identifier les documents de serveur.

Pour plus d’informations, consultez [COleServerItem](../mfc/reference/coleserveritem-class.md) et [COleServerDoc](../mfc/reference/coleserverdoc-class.md) dans le *Class Library Reference*.

## <a name="see-also"></a>Voir aussi

[Serveurs](../mfc/servers.md)<br/>
[Serveurs : Éléments du serveur](../mfc/servers-server-items.md)<br/>
[Serveurs : Implémentation d’un serveur](../mfc/servers-implementing-a-server.md)<br/>
[Serveurs : Implémentations de fenêtres frame sur place](../mfc/servers-implementing-in-place-frame-windows.md)

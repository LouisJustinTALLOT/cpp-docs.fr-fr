---
description: 'En savoir plus sur : serveurs : implémentation de documents de serveur'
title: 'Serveurs : implémentation de documents de serveur'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], managing server documents
- OLE server applications [MFC], implementing OLE servers
- servers, server documents
- server documents [MFC], implementing
ms.assetid: cca1451a-ad09-47ed-b56e-bccd78fc86d1
ms.openlocfilehash: b8843d3e2ac662cbb018a3063c9f04f5dd8d6f10
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217326"
---
# <a name="servers-implementing-server-documents"></a>Serveurs : implémentation de documents de serveur

Cet article explique les étapes à suivre pour implémenter un document serveur si vous n’avez pas spécifié l’option serveur OLE dans l’Assistant Application.

#### <a name="to-define-a-server-document-class"></a>Pour définir une classe de document serveur

1. Dérivez votre classe de document à partir de `COleServerDoc` au lieu de `CDocument`.

1. Créez une classe d’élément de serveur dérivée de `COleServerItem` .

1. Implémentez la `OnGetEmbeddedItem` fonction membre de la classe de document de votre serveur.

   `OnGetEmbeddedItem` est appelé lorsque l’utilisateur d’une application conteneur crée ou modifie un élément incorporé. Elle doit retourner un élément représentant le document entier. Il doit s’agir d’un objet de votre `COleServerItem` classe dérivée de.

1. Substituez la `Serialize` fonction membre pour sérialiser le contenu du document. Vous n’avez pas besoin de sérialiser la liste des éléments de serveur, sauf si vous les utilisez pour représenter les données natives dans votre document. Pour plus d’informations, consultez *implémentation d’éléments de serveur* dans l’article [serveurs : éléments de serveur](../mfc/servers-server-items.md).

Lorsqu’un document serveur est créé, le Framework inscrit automatiquement le document avec les DLL système OLE. Cela permet aux DLL d’identifier les documents du serveur.

Pour plus d’informations, consultez [COleServerItem](../mfc/reference/coleserveritem-class.md) et [COleServerDoc](../mfc/reference/coleserverdoc-class.md) dans la référence de la *bibliothèque de classes*.

## <a name="see-also"></a>Voir aussi

[Serveurs](../mfc/servers.md)<br/>
[Serveurs : éléments du serveur](../mfc/servers-server-items.md)<br/>
[Serveurs : implémentation d’un serveur](../mfc/servers-implementing-a-server.md)<br/>
[Serveurs : implémentation de fenêtres Frame In-Place](../mfc/servers-implementing-in-place-frame-windows.md)

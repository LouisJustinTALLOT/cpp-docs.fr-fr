---
title: 'Serveurs : Implémentation de Documents de serveur | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE server applications [MFC], managing server documents
- OLE server applications [MFC], implementing OLE servers
- servers, server documents
- server documents [MFC], implementing
ms.assetid: cca1451a-ad09-47ed-b56e-bccd78fc86d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7907935971fae7d990c651410e5b76982b798075
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060518"
---
# <a name="servers-implementing-server-documents"></a>Serveurs : implémentation de documents de serveur

Cet article explique les étapes à suivre pour implémenter correctement un document serveur si vous n’avez pas spécifié l’option de serveur OLE dans l’Assistant application.

#### <a name="to-define-a-server-document-class"></a>Pour définir une classe de document serveur

1. Dérivez votre classe de document à partir de `COleServerDoc` au lieu de `CDocument`.

1. Créer une classe d’élément serveur dérivée `COleServerItem`.

1. Implémentez le `OnGetEmbeddedItem` fonction membre de votre classe de document serveur.

   `OnGetEmbeddedItem` est appelée lorsque l’utilisateur d’une application conteneur crée ou modifie un élément incorporé. Elle doit retourner un élément qui représente la totalité du document. Cela doit être un objet de votre `COleServerItem`-classe dérivée.

1. Remplacer le `Serialize` fonction membre à sérialiser le contenu du document. Vous n’avez pas besoin de sérialiser la liste des éléments de serveur, sauf si vous les utilisez pour représenter les données natives dans votre document. Pour plus d’informations, consultez *implémentation des éléments serveur* dans l’article [serveurs : éléments de serveur](../mfc/servers-server-items.md).

Lorsqu’un document serveur est créé, le framework enregistre automatiquement le document avec les DLL système OLE. Ainsi, les DLL identifier les documents de serveur.

Pour plus d’informations, consultez [COleServerItem](../mfc/reference/coleserveritem-class.md) et [COleServerDoc](../mfc/reference/coleserverdoc-class.md) dans le *Class Library Reference*.

## <a name="see-also"></a>Voir aussi

[Serveurs](../mfc/servers.md)<br/>
[Serveurs : éléments du serveur](../mfc/servers-server-items.md)<br/>
[Serveurs : implémentation d’un serveur](../mfc/servers-implementing-a-server.md)<br/>
[Serveurs : implémentations de fenêtres frame sur place](../mfc/servers-implementing-in-place-frame-windows.md)


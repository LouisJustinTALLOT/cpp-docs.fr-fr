---
title: 'Serveurs : Implémentation de Frame en Place Windows | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame windows [MFC], implementing
- OLE server applications [MFC], frame windows
- servers, in-place frame windows
- frame windows [MFC], in-place
- in-place frame windows
ms.assetid: 09bde4d8-15e2-4fba-8d14-9b954d926b92
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 24c63c10feff624abe399952b682303a6e262d35
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425013"
---
# <a name="servers-implementing-in-place-frame-windows"></a>Serveurs : implémentations de fenêtres frame sur place

Cet article explique ce que vous devez effectuer pour implémenter des fenêtres frame au sein de votre application serveur d'édition visuelle si vous n'utilisez pas l'Assistant d'application pour créer votre application serveur. Au lieu de suivre la procédure décrite dans cet article, vous pouvez utiliser une classe de fenêtre frame sur place existante à partir d’une application générée par l’Assistant application ou un exemple fourni avec Visual C++.

#### <a name="to-declare-an-in-place-frame-window-class"></a>Pour déclarer une classe de fenêtre frame en place

1. Dérivez une classe de fenêtre frame en place depuis `COleIPFrameWnd`.

   - Utilisez la macro DECLARE_DYNCREATE dans votre fichier d’en-tête de classe.

   - Utilisez la macro IMPLEMENT_DYNCREATE dans votre fichier d’implémentation (.cpp). Cela permet aux objets de cette classe d'être créés par le .NET Framework.

1. Déclarez un membre `COleResizeBar` dans la classe de fenêtre frame. Cela est nécessaire si vous voulez prendre en charge le redimensionnement en place dans les applications serveur.

     Déclarez un `OnCreate` Gestionnaire de messages (à l’aide de la **propriétés** fenêtre) et appelez `Create` pour votre `COleResizeBar` membre, si vous l’avez défini.

1. Si vous avez une barre d'outils, déclarez un membre `CToolBar` dans la classe de fenêtre frame.

     Remplacez la fonction membre `OnCreateControlBars` pour créer une barre d'outils lorsque le serveur en place est actif. Exemple :

     [!code-cpp[NVC_MFCOleServer#1](../mfc/codesnippet/cpp/servers-implementing-in-place-frame-windows_1.cpp)]

     Consultez la discussion sur ce code en suivant l'étape 5.

1. Incluez le fichier d'en-tête pour cette classe de fenêtre frame en place dans le fichier .cpp principal.

1. Dans `InitInstance` pour votre classe d'application, appelez la fonction `SetServerInfo` de l'objet modèle de document afin de spécifier les ressources et la fenêtre frame en place à utiliser pour l'ouverture et la modification en place.

La série de la fonction appelle le **si** instruction crée la barre d’outils à partir des ressources du serveur fourni. À ce stade, la barre d'outils fait partie de la hiérarchie dans la fenêtre du conteneur. Cette barre d'outils est dérivée de `CToolBar`, elle transmet les messages à son propriétaire, la fenêtre frame de l'application conteneur, sauf si vous modifiez le propriétaire. C'est pourquoi l'appel à `SetOwner` est nécessaire. Cet appel modifie la fenêtre lorsque les commandes sont envoyées à la fenêtre frame en place du serveur, ce qui fait que des messages sont transmis au serveur. Ainsi, le serveur peut réagir aux opérations dans la barre d'outils disponible.

L'ID de la bitmap de la barre d'outils doit être le même que les autres ressources en place définies dans votre application serveur. Consultez [Menus et ressources : ajouts de serveurs](../mfc/menus-and-resources-server-additions.md) pour plus d’informations.

Pour plus d’informations, consultez [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md), [COleResizeBar](../mfc/reference/coleresizebar-class.md), et [CDocTemplate::SetServerInfo](../mfc/reference/cdoctemplate-class.md#setserverinfo) dans le *Class Library Reference*.

## <a name="see-also"></a>Voir aussi

[Serveurs](../mfc/servers.md)<br/>
[Serveurs : implémentation d’un serveur](../mfc/servers-implementing-a-server.md)<br/>
[Serveurs : implémentation de documents de serveur](../mfc/servers-implementing-server-documents.md)<br/>
[Serveurs : éléments du serveur](../mfc/servers-server-items.md)


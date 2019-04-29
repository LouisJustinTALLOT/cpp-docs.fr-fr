---
title: 'serveurs : Implémentation d’un serveur'
ms.date: 11/04/2016
helpviewer_keywords:
- servers, implementing
- OLE server applications [MFC], implementing OLE servers
ms.assetid: 5bd57e8e-3b23-4f23-9597-496fac2d24b5
ms.openlocfilehash: 953d157f4bbad0b460947740a2622074dfc90f4f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308015"
---
# <a name="servers-implementing-a-server"></a>serveurs : Implémentation d’un serveur

Cet article explique le code de que l’Assistant Application MFC crée pour une application serveur d’édition visuelle. Si vous n’utilisez pas l’Assistant application, cet article répertorie les domaines où vous devez écrire du code pour implémenter une application serveur.

Si vous utilisez l’Assistant application pour créer une nouvelle application serveur, il vous fournit une quantité importante de code spécifique au serveur. Si vous ajoutez des fonctionnalités de serveur d’édition visual à une application existante, vous devez dupliquer le code de l’Assistant application aurait fourni avant d’ajouter le reste du code serveur nécessaires.

Le code du serveur qui fournit l’Assistant application se divise en plusieurs catégories :

- Définition des ressources serveur :

  - La ressource de menu utilisée quand le serveur modifie un élément incorporé dans sa propre fenêtre.

  - Les ressources de menu et barre d’outils utilisés lorsque le serveur est actif en place.

  Pour plus d’informations sur ces ressources, consultez [Menus et ressources : Ajouts de serveurs](../mfc/menus-and-resources-server-additions.md).

- Définition d’une classe d’élément dérivé `COleServerItem`. Pour plus d’informations sur les éléments de serveur, consultez [serveurs : Éléments de serveur](../mfc/servers-server-items.md).

- Modification de la classe de base de la classe de document à `COleServerDoc`. Pour plus d’informations, consultez [serveurs : Implémentation des Documents serveur](../mfc/servers-implementing-server-documents.md).

- Définition d’une classe de fenêtre frame dérivé `COleIPFrameWnd`. Pour plus d’informations, consultez [serveurs : Implémentation Windows du Frame en Place](../mfc/servers-implementing-in-place-frame-windows.md).

- Création d’une entrée pour l’application serveur dans la base de données d’inscription Windows et l’inscription de la nouvelle instance du serveur avec le système OLE. Pour plus d’informations sur ce sujet, consultez [inscription](../mfc/registration.md).

- Initialisation et lancement de l’application serveur. Pour plus d’informations sur ce sujet, consultez [inscription](../mfc/registration.md).

Pour plus d’informations, consultez [COleServerItem](../mfc/reference/coleserveritem-class.md), [COleServerDoc](../mfc/reference/coleserverdoc-class.md), et [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md) dans le *Class Library Reference*.

## <a name="see-also"></a>Voir aussi

[Serveurs](../mfc/servers.md)<br/>
[Conteneurs](../mfc/containers.md)<br/>
[Menus et ressources (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Inscription](../mfc/registration.md)

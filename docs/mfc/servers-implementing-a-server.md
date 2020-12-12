---
description: 'En savoir plus sur : serveurs : implémentation d’un serveur'
title: "Serveurs : implémentation d'un serveur"
ms.date: 11/04/2016
helpviewer_keywords:
- servers, implementing
- OLE server applications [MFC], implementing OLE servers
ms.assetid: 5bd57e8e-3b23-4f23-9597-496fac2d24b5
ms.openlocfilehash: 3ced10f88ce062ab571841610ba4b000571835b0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217378"
---
# <a name="servers-implementing-a-server"></a>Serveurs : implémentation d'un serveur

Cet article explique le code créé par l’Assistant Application MFC pour une application serveur d’édition visuelle. Si vous n’utilisez pas l’Assistant Application, cet article répertorie les domaines dans lesquels vous devez écrire du code pour implémenter une application serveur.

Si vous utilisez l’Assistant application pour créer une nouvelle application serveur, il fournit une quantité significative de code spécifique au serveur pour vous. Si vous ajoutez des fonctionnalités de serveur d’édition visuelle à une application existante, vous devez dupliquer le code que l’Assistant Application aurait fourni avant d’ajouter le reste du code serveur nécessaire.

Le code serveur que l’Assistant application fournit se divise en plusieurs catégories :

- Définition des ressources du serveur :

  - Ressource de menu utilisée lorsque le serveur modifie un élément incorporé dans sa propre fenêtre.

  - Ressources de menu et de barre d’outils utilisées lorsque le serveur est actif sur place.

  Pour plus d’informations sur ces ressources, consultez [menus et ressources : ajouts de serveurs](../mfc/menus-and-resources-server-additions.md).

- Définition d’une classe d’élément dérivée de `COleServerItem` . Pour plus d’informations sur les éléments de serveur, consultez [serveurs : éléments de serveur](../mfc/servers-server-items.md).

- Modification de la classe de base de la classe de document en `COleServerDoc` . Pour plus d’informations, consultez [serveurs : implémentation de documents serveur](../mfc/servers-implementing-server-documents.md).

- Définition d’une classe de fenêtre frame dérivée de `COleIPFrameWnd` . Pour plus d’informations, consultez [Servers : implementing In-Place Frame Windows](../mfc/servers-implementing-in-place-frame-windows.md).

- Création d’une entrée pour l’application serveur dans la base de données d’inscription Windows et enregistrement de la nouvelle instance du serveur avec le système OLE. Pour plus d’informations sur cette rubrique, consultez [inscription](../mfc/registration.md).

- Initialisation et lancement de l’application serveur. Pour plus d’informations sur cette rubrique, consultez [inscription](../mfc/registration.md).

Pour plus d’informations, consultez [COleServerItem](../mfc/reference/coleserveritem-class.md), [COleServerDoc](../mfc/reference/coleserverdoc-class.md)et [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md) dans la *référence* de la bibliothèque de classes.

## <a name="see-also"></a>Voir aussi

[Serveurs](../mfc/servers.md)<br/>
[Containers](../mfc/containers.md)<br/>
[Menus et ressources (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Inscription](../mfc/registration.md)

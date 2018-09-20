---
title: 'Activation : Verbes | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- verbs [MFC]
- OLE [MFC], activation
- edit verb [MFC]
- activation [MFC], verbs
- OLE [MFC], editing
- Primary verb [MFC]
- OLE activation {MFC]
ms.assetid: eb56ff23-1de8-43ad-abeb-dc7346ba7b70
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 63b21e4d7f40d87b35d2ea5650f86801294affaa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425715"
---
# <a name="activation-verbs"></a>Activation : verbes

Cet article explique le jeu de verbes principal et secondaire de rôle dans OLE [activation](../mfc/activation-cpp.md).

En règle générale, double-cliquez sur un élément incorporé permet à l’utilisateur pour le modifier. Toutefois, certains éléments ne comportent pas de cette façon. Par exemple, double-cliquez sur un élément créé avec l’application Magnétophone n’ouvre pas le serveur dans une fenêtre distincte ; au lieu de cela, il lit le son.

La raison de cette différence de comportement est que les éléments de Magnétophone possèdent un autre « primary (verbe). » Le verbe principal est l’action effectuée lorsque l’utilisateur double-clique sur un élément OLE. Pour la plupart des types d’éléments OLE, le verbe principal est Edit, ce qui lance le serveur qui a créé l’élément. Pour certains types d’éléments, tels que des éléments Magnétophone, le verbe principal est Play.

Prend en charge de nombreux types d’éléments OLE qu’un seul verbe et Edit est la plus courante. Toutefois, certains types d’éléments prennent en charge plusieurs verbes. Par exemple, le Magnétophone éléments prennent en charge Modifier sous forme verbale secondaire.

Un autre verbe fréquemment utilisé est ouverte. Le verbe Open est identique à modifier, sauf l’application serveur est lancée dans une fenêtre distincte. Ce verbe doit être utilisé lors de l’application conteneur ou l’application serveur ne prend pas en charge l’activation sur place.

Tous les verbes autres que le verbe principal doivent être appelés via une commande de sous-menu lorsque l’élément est sélectionné. Ce sous-menu contient tous les verbes pris en charge par l’élément et est généralement atteint par le *typename* **objet** commande sur le **modifier** menu. Pour plus d’informations sur la *typename* **objet** de commande, consultez l’article [Menus et ressources : ajouts de conteneurs](../mfc/menus-and-resources-container-additions.md).

Les verbes de qu'une application serveur prend en charge sont répertoriées dans la base de données d’inscription Windows. Si votre application serveur est écrite avec la bibliothèque Microsoft Foundation Class, elle inscrit automatiquement tous les verbes lorsque le serveur est démarré. Si ce n’est pas le cas, vous devez les inscrire pendant la phase d’initialisation de l’application serveur. Pour plus d’informations, consultez l’article [inscription](../mfc/registration.md).

## <a name="see-also"></a>Voir aussi

[Activation](../mfc/activation-cpp.md)<br/>
[Conteneurs](../mfc/containers.md)<br/>
[Serveurs](../mfc/servers.md)


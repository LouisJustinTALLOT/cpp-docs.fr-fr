---
description: 'En savoir plus sur : activation : verbes'
title: 'Activation : Verbes'
ms.date: 11/04/2016
helpviewer_keywords:
- verbs [MFC]
- OLE [MFC], activation
- edit verb [MFC]
- activation [MFC], verbs
- OLE [MFC], editing
- Primary verb [MFC]
- OLE activation {MFC]
ms.assetid: eb56ff23-1de8-43ad-abeb-dc7346ba7b70
ms.openlocfilehash: 2c680452d87f1fcfd1ee2a0b8362dbaab8c0affd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325930"
---
# <a name="activation-verbs"></a>Activation : Verbes

Cet article explique les verbes principal et secondaire du rôle joués dans l' [activation](activation-cpp.md)OLE.

En règle générale, le fait de double-cliquer sur un élément incorporé permet à l’utilisateur de le modifier. Toutefois, certains éléments ne se comportent pas de cette façon. Par exemple, le fait de double-cliquer sur un élément créé avec l’application magnétophone n’ouvre pas le serveur dans une fenêtre distincte ; au lieu de cela, il lit le son.

Cette différence de comportement est due au fait que les éléments de l’enregistreur de sons ont un « verbe principal » différent. Le verbe principal est l’action effectuée lorsque l’utilisateur double-clique sur un élément OLE. Pour la plupart des types d’éléments OLE, le verbe principal est Edit, ce qui lance le serveur qui a créé l’élément. Pour certains types d’éléments, tels que les éléments d’enregistreur de sons, le verbe principal est Play.

De nombreux types d’éléments OLE ne prennent en charge qu’un seul verbe, et la modification est la plus courante. Toutefois, certains types d’éléments prennent en charge plusieurs verbes. Par exemple, les éléments d’enregistreur de sons prennent en charge la modification en tant que verbe secondaire.

Un autre verbe utilisé fréquemment est ouvert. Le verbe Open est identique à Edit, sauf que l’application serveur est lancée dans une fenêtre distincte. Ce verbe doit être utilisé lorsque l’application conteneur ou l’application serveur ne prend pas en charge l’activation sur place.

Les verbes autres que le verbe principal doivent être appelés à l’aide d’une commande de sous-menu lorsque l’élément est sélectionné. Ce sous-menu contient tous les verbes pris en charge par l’élément et est généralement atteint par la commande d' **objet** *TypeName* du menu **Edition** . Pour plus d’informations sur la commande d' **objet** *TypeName* , consultez l’article [menus et ressources : ajouts de conteneurs](menus-and-resources-container-additions.md).

Les verbes pris en charge par une application serveur sont répertoriés dans la base de données d’inscription Windows. Si votre application serveur est écrite avec le bibliothèque MFC (Microsoft Foundation Class), elle inscrira automatiquement tous les verbes lorsque le serveur sera démarré. Si ce n’est pas le cas, vous devez les inscrire pendant la phase d’initialisation de l’application serveur. Pour plus d’informations, consultez l’article [inscription](registration.md).

## <a name="see-also"></a>Voir aussi

[Activation](activation-cpp.md)<br/>
[Containers](containers.md)<br/>
[Serveurs](servers.md)

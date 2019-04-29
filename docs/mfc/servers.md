---
title: Serveurs
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC]
- OLE server applications [MFC], activation
- full-server
- servers
- mini-server
- OLE server applications [MFC], server types
- server applications [MFC]
ms.assetid: e45172e8-eae3-400a-8139-0fa009a42fdc
ms.openlocfilehash: 7b1eb0df439bcfde3aa295f23a90291e865df3a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307833"
---
# <a name="servers"></a>Serveurs

Une application serveur (ou application composant) crée OLE éléments (ou composants) pour une utilisation par les applications de conteneur. Une application serveur d’édition visuelle prend également en charge la modification visuelle ou l’activation sur place. Une autre forme de serveur OLE est un [serveur automation](../mfc/automation-servers.md). Certaines applications serveur prennent en charge uniquement la création d’éléments incorporés ; d’autres prennent en charge la création d’éléments liés et incorporés. Certains prennent en charge de liaison uniquement, bien que cela soit rare. Toutes les applications serveur doivent prendre en charge l’activation par les applications de conteneur lorsque l’utilisateur souhaite modifier un élément. Une application peut être un conteneur et un serveur. En d’autres termes, il peut à la fois incorporer des données dans ses documents et créer des données qui peuvent être incorporées en tant qu’éléments dans les documents d’autres applications.

Un mini-serveur est un type spécial d’application serveur qui peut être lancé uniquement par un conteneur. Microsoft Draw et Microsoft Graph sont des exemples de mini-serveurs. Un mini-serveur ne stocke pas les documents sous forme de fichiers sur le disque. Au lieu de cela, il lit ses documents à partir d’et les écrit dans les éléments dans les documents appartenant à des conteneurs. Par conséquent, un mini-serveur prend en charge uniquement l’incorporation, ne pas de liaison.

Un serveur complet peut être soit exécuté comme une application autonome ou lancé par une application de conteneur. Un serveur complet peut stocker des documents en tant que fichiers sur le disque. Il peut prendre en charge uniquement l’incorporation, à la fois l’incorporation et la liaison ou la liaison uniquement. L’utilisateur d’une application conteneur peut créer un élément incorporé en choisissant la commande Couper ou copier dans le serveur et la commande Coller dans le conteneur. Un élément lié est créé en choisissant la commande de copie sur le serveur et la commande Coller un lien dans le conteneur. Vous pouvez également, l’utilisateur peut créer un élément incorporé ou lié à l’aide de la boîte de dialogue Insérer un objet.

Le tableau suivant résume les caractéristiques de différents types de serveurs :

### <a name="server-characteristics"></a>Caractéristiques du serveur

|Type de serveur|Prend en charge plusieurs instances|Éléments par document|Documents par instance|
|--------------------|---------------------------------|------------------------|----------------------------|
|Mini-serveur|Oui|1|1|
|Serveur complet SDI|Oui|1 (si la liaison est prise en charge, 1 ou plus)|1|
|Serveur complet MDI|Aucun (non requis)|1 (si la liaison est prise en charge, 1 ou plus)|0 ou plus|

Une application serveur doit prendre en charge plusieurs conteneurs simultanément, dans le cas où plusieurs conteneurs permet de modifier un élément incorporé ou lié. Si le serveur est une application SDI (ou un mini-serveur avec une interface de boîte de dialogue), plusieurs instances du serveur doivent être en mesure d’exécuter simultanément. Cela permet à une instance distincte de l’application pour traiter chaque demande de conteneur.

Si le serveur est une application MDI, il peut créer une fenêtre enfant MDI chaque fois qu’un conteneur doit modifier un élément. De cette façon, une seule instance de l’application peut prendre en charge plusieurs conteneurs.

Votre application serveur doit indiquer les DLL système OLE que faire si une instance du serveur est déjà en cours d’exécution lorsqu’un autre conteneur demande ses services : si elle doit lancer une nouvelle instance du serveur ou diriger les demandes de tous les conteneurs vers une instance de la serveur.

Pour plus d’informations sur les serveurs, consultez :

- [Serveurs : Implémentation d’un serveur](../mfc/servers-implementing-a-server.md)

- [Serveurs : Implémentation de documents de serveur](../mfc/servers-implementing-server-documents.md)

- [Serveurs : Implémentations de fenêtres frame sur place](../mfc/servers-implementing-in-place-frame-windows.md)

- [Serveurs : Éléments du serveur](../mfc/servers-server-items.md)

- [Serveurs : Problèmes d’interface utilisateur](../mfc/servers-user-interface-issues.md)

## <a name="see-also"></a>Voir aussi

[OLE](../mfc/ole-in-mfc.md)<br/>
[Conteneurs](../mfc/containers.md)<br/>
[Conteneurs : Fonctionnalités avancées](../mfc/containers-advanced-features.md)<br/>
[Menus et ressources (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Inscription](../mfc/registration.md)<br/>
[Serveurs Automation](../mfc/automation-servers.md)

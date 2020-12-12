---
description: 'En savoir plus sur : serveurs'
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
ms.openlocfilehash: 5e9a9dd7cbb1ab237712b5ad0c84e3114a119ee3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217300"
---
# <a name="servers"></a>Serveurs

Une application serveur (ou application de composant) crée des éléments (ou composants) OLE pour une utilisation par les applications de conteneur. Une application serveur d’édition visuelle prend également en charge la modification visuelle ou l’activation sur place. Une autre forme de serveur OLE est un [serveur Automation](../mfc/automation-servers.md). Certaines applications serveur prennent uniquement en charge la création d’éléments incorporés ; d’autres prennent en charge la création d’éléments incorporés et liés. Certains prennent uniquement en charge la liaison, bien que cela soit rare. Toutes les applications serveur doivent prendre en charge l’activation par les applications conteneur lorsque l’utilisateur souhaite modifier un élément. Une application peut être à la fois un conteneur et un serveur. En d’autres termes, elle peut incorporer des données dans ses documents et créer des données qui peuvent être incorporées en tant qu’éléments dans d’autres documents d’applications.

Un mini-serveur est un type spécial d’application serveur qui peut être lancé uniquement par un conteneur. Microsoft Draw et Microsoft Graph sont des exemples de miniservers. Un mini-minine stocke pas les documents en tant que fichiers sur le disque. Au lieu de cela, il lit ses documents à partir de et les écrit dans les éléments des documents appartenant aux conteneurs. Par conséquent, un mini-mini prend en charge uniquement l’incorporation, pas la liaison.

Un serveur complet peut être exécuté en tant qu’application autonome ou lancé par une application de conteneur. Un serveur complet peut stocker des documents en tant que fichiers sur le disque. Il peut uniquement prendre en charge l’incorporation, l’incorporation et la liaison, ou la liaison uniquement. L’utilisateur d’une application conteneur peut créer un élément incorporé en choisissant la commande couper ou copier dans le serveur et la commande coller dans le conteneur. Pour créer un élément lié, choisissez la commande copier dans le serveur et la commande Coller le lien dans le conteneur. L’utilisateur peut également créer un élément incorporé ou lié à l’aide de la boîte de dialogue Insérer un objet.

Le tableau suivant récapitule les caractéristiques de différents types de serveurs :

### <a name="server-characteristics"></a>Caractéristiques du serveur

|Type de serveur|Prend en charge plusieurs instances|Éléments par document|Documents par instance|
|--------------------|---------------------------------|------------------------|----------------------------|
|Mini|Oui|1|1|
|Serveur complet SDI|Oui|1 (si la liaison est prise en charge, 1 ou plus)|1|
|Serveur MDI complet|Non (non requis)|1 (si la liaison est prise en charge, 1 ou plus)|0 ou plus|

Une application serveur doit prendre en charge plusieurs conteneurs simultanément, dans le cas où plusieurs conteneurs seront utilisés pour modifier un élément incorporé ou lié. Si le serveur est une application SDI (ou un mini-serveur avec une interface de boîte de dialogue), plusieurs instances du serveur doivent être en mesure d’être exécutées simultanément. Cela permet à une instance distincte de l’application de gérer chaque demande de conteneur.

Si le serveur est une application MDI, il peut créer une nouvelle fenêtre enfant MDI chaque fois qu’un conteneur a besoin de modifier un élément. De cette façon, une seule instance de l’application peut prendre en charge plusieurs conteneurs.

Votre application serveur doit indiquer aux DLL système OLE ce qu’il faut faire si une instance du serveur est déjà en cours d’exécution lorsqu’un autre conteneur demande ses services : s’il doit lancer une nouvelle instance du serveur ou diriger toutes les demandes de conteneurs vers une instance du serveur.

Pour plus d’informations sur les serveurs, consultez :

- [Serveurs : implémentation d’un serveur](../mfc/servers-implementing-a-server.md)

- [Serveurs : implémentation de documents de serveur](../mfc/servers-implementing-server-documents.md)

- [Serveurs : implémentation de fenêtres Frame In-Place](../mfc/servers-implementing-in-place-frame-windows.md)

- [Serveurs : éléments du serveur](../mfc/servers-server-items.md)

- [Serveurs : problèmes de User-Interface](../mfc/servers-user-interface-issues.md)

## <a name="see-also"></a>Voir aussi

[OLE](../mfc/ole-in-mfc.md)<br/>
[Containers](../mfc/containers.md)<br/>
[Conteneurs : fonctionnalités avancées](../mfc/containers-advanced-features.md)<br/>
[Menus et ressources (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Inscription](../mfc/registration.md)<br/>
[Serveurs Automation](../mfc/automation-servers.md)

---
title: Tables des messages (MFC)
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.messages
helpviewer_keywords:
- message maps [MFC], MFC
- Windows messages [MFC], message maps
- messages [MFC], Windows
- MFC, messages
ms.assetid: 3f9855e4-9d7d-4b64-8f3f-a19ea3cf79ba
ms.openlocfilehash: dda989318d6c6915ef8bc4e668fd238e8167de08
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599184"
---
# <a name="message-maps-mfc"></a>Tables des messages (MFC)

Cette section de la référence répertorie tous les [message les macros de mappage](../../mfc/reference/message-map-macros-mfc.md) et tous les [CWnd](../../mfc/reference/cwnd-class.md) prototypes de fonction des entrées de table des messages, ainsi que le membre correspondant :

|Category|Description|
|--------------|-----------------|
|ON\_Gestionnaire de messages de commande|Gère `WM_COMMAND` messages générés par les sélections de menu utilisateur ou les touches d’accès rapide.|
|[Gestionnaires pour les messages de notification de fenêtre enfant](../../mfc/reference/child-window-notification-message-handlers.md)|Gérer les messages de notification à partir des fenêtres enfants.|
|[Gestionnaires de messages WM_](../../mfc/reference/handlers-for-wm-messages.md)|Gérer `WM_` des messages, tel que `WM_PAINT`.|
|[Gestionnaires de messages définis par l’utilisateur](../../mfc/reference/user-defined-handlers.md)|Gérer les messages définis par l’utilisateur.|

(Pour obtenir une explication de la terminologie et les conventions utilisées dans cette référence, consultez [comment utiliser le renvoi de mappage de Message](../../mfc/reference/how-to-use-the-message-map-cross-reference.md).)

Dans la mesure où Windows est un système d’exploitation orientés message, une grande partie de la programmation pour l’environnement Windows implique la gestion des messages. Se produit chaque fois, cliquez sur un événement tel qu’une séquence de touches ou de la souris, un message est envoyé à l’application, qui doit ensuite gérer l’événement.

La bibliothèque Microsoft Foundation Class offre un modèle de programmation optimisé pour la programmation basée sur message. Dans ce modèle, « tables des messages » sont utilisées pour désigner les fonctions gérera différents messages pour une classe particulière. Tables des messages contiennent une ou plusieurs macros qui spécifient quels messages seront traités par les fonctions. Par exemple, une carte message contenant un `ON_COMMAND` macro peut ressembler à ceci :

[!code-cpp[NVC_MFCMessageMaps#16](../../mfc/reference/codesnippet/cpp/message-maps-mfc_1.cpp)]

Le `ON_COMMAND` macro est utilisée pour gérer les messages de commande générés par les menus, des boutons et des touches accélérateur. [Macros](../../mfc/reference/message-map-macros-mfc.md) sont disponibles pour mapper les éléments suivants :

## <a name="windows-messages"></a>Messages Windows

- Notifications de contrôle

- Messages définis par l’utilisateur

## <a name="command-messages"></a>Messages de commande

- Inscrit les messages définis par l’utilisateur

- Messages de mise à jour d’interface utilisateur

## <a name="ranges-of-messages"></a>Plages de Messages

- Commandes

- Messages de gestionnaire de mise à jour

- Notifications de contrôle

Bien que les macros de table des messages sont importants, en règle générale ne sont pas avoir à les utiliser directement. Il s’agit, car la fenêtre Propriétés crée automatiquement des entrées de table des messages dans vos fichiers sources lorsque vous l’utilisez pour associer des fonctions de gestion des messages avec des messages. Chaque fois que vous souhaitez modifier ou ajouter une entrée de la table des messages, vous pouvez utiliser la fenêtre Propriétés.

> [!NOTE]
>  La fenêtre Propriétés ne prend pas en charge les plages de la table des messages. Vous devez écrire vous-même ces entrées de table des messages.

Toutefois, les tables des messages sont une partie importante de la bibliothèque Microsoft Foundation Class. Vous devez comprendre ce qu’ils font et documentation est fournie pour eux.

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)


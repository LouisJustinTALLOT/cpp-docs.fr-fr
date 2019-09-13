---
title: Tables des messages (MFC)
ms.date: 09/07/2019
helpviewer_keywords:
- message maps [MFC], MFC
- Windows messages [MFC], message maps
- messages [MFC], Windows
- MFC, messages
ms.assetid: 3f9855e4-9d7d-4b64-8f3f-a19ea3cf79ba
ms.openlocfilehash: 4305d9b1db297eebcb189d2fad98b8c634ed1133
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908042"
---
# <a name="message-maps-mfc"></a>Tables des messages (MFC)

Cette section de la référence répertorie toutes les [macros de mappage des messages](../../mfc/reference/message-map-macros-mfc.md) et toutes les entrées de table des messages [CWnd](../../mfc/reference/cwnd-class.md) , ainsi que les prototypes de fonction membre correspondants :

|Catégorie|Description|
|--------------|-----------------|
|Gestionnaire\_de messages de commande sur|Gère `WM_COMMAND` les messages générés par les sélections de menu utilisateur ou les touches d’accès de menu.|
|[Gestionnaires pour les messages de notification de fenêtre enfant](../../mfc/reference/child-window-notification-message-handlers.md)|Gérer les messages de notification des fenêtres enfants.|
|[Gestionnaires de messages WM_](../../mfc/reference/handlers-for-wm-messages.md)|Gérer `WM_` les messages, tels `WM_PAINT`que.|
|[Gestionnaires de messages définis par l’utilisateur](../../mfc/reference/user-defined-handlers.md)|Gérer les messages définis par l’utilisateur.|

(Pour obtenir une explication de la terminologie et des conventions utilisées dans cette référence, consultez [comment utiliser la référence croisée de la table des messages](../../mfc/reference/how-to-use-the-message-map-cross-reference.md).)

Étant donné que Windows est un système d’exploitation orienté message, une grande partie de la programmation de l’environnement Windows implique la gestion des messages. Chaque fois qu’un événement tel qu’une séquence d’événements ou un clic de souris se produit, un message est envoyé à l’application, qui doit ensuite gérer l’événement.

Le bibliothèque MFC (Microsoft Foundation Class) offre un modèle de programmation optimisé pour la programmation basée sur les messages. Dans ce modèle, les « tables des messages » sont utilisées pour désigner les fonctions qui géreront différents messages pour une classe particulière. Les tables des messages contiennent une ou plusieurs macros qui spécifient les messages qui seront gérés par les fonctions. Par exemple, une table des messages contenant `ON_COMMAND` une macro peut se présenter comme suit :

[!code-cpp[NVC_MFCMessageMaps#16](../../mfc/reference/codesnippet/cpp/message-maps-mfc_1.cpp)]

La `ON_COMMAND` macro est utilisée pour gérer les messages de commande générés par les menus, les boutons et les touches d’accès rapide. Les [macros](../../mfc/reference/message-map-macros-mfc.md) sont disponibles pour mapper les éléments suivants :

## <a name="windows-messages"></a>Messages Windows

- Notifications de contrôle

- Messages définis par l’utilisateur

## <a name="command-messages"></a>Messages de commande

- Messages définis par l’utilisateur inscrits

- Messages de mise à jour de l’interface utilisateur

## <a name="ranges-of-messages"></a>Plages de messages

- Commandes

- Mettre à jour les messages du gestionnaire

- Notifications de contrôle

Bien que les macros de table des messages soient importantes, il n’est généralement pas nécessaire de les utiliser directement. Cela est dû au fait que l' [Assistant classe](mfc-class-wizard.md) crée automatiquement des entrées de table des messages dans vos fichiers sources lorsque vous l’utilisez pour associer des fonctions de gestion de message à des messages. Chaque fois que vous souhaitez modifier ou ajouter une entrée de table des messages, vous pouvez utiliser l’Assistant classe.

> [!NOTE]
>  L’Assistant classe ne prend pas en charge les plages de table des messages. Vous devez écrire ces entrées de table des messages vous-même.

Toutefois, les tables des messages constituent une partie importante du bibliothèque MFC (Microsoft Foundation Class). Vous devez comprendre ce qu’ils font et la documentation qui leur est fournie.

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

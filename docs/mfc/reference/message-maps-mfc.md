---
title: Tables des messages (MFC)
ms.date: 09/07/2019
helpviewer_keywords:
- message maps [MFC], MFC
- Windows messages [MFC], message maps
- messages [MFC], Windows
- MFC, messages
ms.assetid: 3f9855e4-9d7d-4b64-8f3f-a19ea3cf79ba
ms.openlocfilehash: 8080becf1a1a153322bfd03cbd7006eaf2ce4e13
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356573"
---
# <a name="message-maps-mfc"></a>Tables des messages (MFC)

Cette section de la référence répertorie toutes les [macros de cartographie des messages](../../mfc/reference/message-map-macros-mfc.md) et toutes les entrées de carte de message [CWnd](../../mfc/reference/cwnd-class.md) ainsi que les prototypes correspondants de fonction des membres :

|Category|Description|
|--------------|-----------------|
|Sur\_COMMAND Message Handler|Gère `WM_COMMAND` les messages générés par les sélections de menus des utilisateurs ou les clés d’accès au menu.|
|[Gestionnaires pour les messages de notification de fenêtre enfant](../../mfc/reference/child-window-notification-message-handlers.md)|Gérer les messages de notification à partir des fenêtres des enfants.|
|[WM_ Messages Handlers](../../mfc/reference/handlers-for-wm-messages.md)|Gérer `WM_` les messages, tels que `WM_PAINT`.|
|[Gestionnaires de messages définis par l’utilisateur](../../mfc/reference/user-defined-handlers.md)|Gérer les messages définis par l’utilisateur.|

(Pour une explication de la terminologie et des conventions utilisées dans cette référence, voir [Comment utiliser la carte du message Cross-Reference](../../mfc/reference/how-to-use-the-message-map-cross-reference.md).)

Étant donné que Windows est un système d’exploitation axé sur les messages, une grande partie de la programmation de l’environnement Windows implique la manipulation des messages. Chaque fois qu’un événement tel qu’une frappe ou un clic de souris se produit, un message est envoyé à l’application, qui doit ensuite gérer l’événement.

La Microsoft Foundation Class Library offre un modèle de programmation optimisé pour la programmation basée sur les messages. Dans ce modèle, les « cartes de message » sont utilisées pour désigner quelles fonctions traiteront divers messages pour une classe particulière. Les cartes de message contiennent une ou plusieurs macros qui spécifient quels messages seront traités par quelles fonctions. Par exemple, une carte `ON_COMMAND` de message contenant une macro peut ressembler à ceci :

[!code-cpp[NVC_MFCMessageMaps#16](../../mfc/reference/codesnippet/cpp/message-maps-mfc_1.cpp)]

La `ON_COMMAND` macro est utilisée pour gérer les messages de commande générés par les menus, les boutons et les touches d’accélérateur. [Macros](../../mfc/reference/message-map-macros-mfc.md) sont disponibles pour cartographier ce qui suit:

## <a name="windows-messages"></a>Windows Messages

- Notifications de contrôle

- Messages définis par l’utilisateur

## <a name="command-messages"></a>Messages de commande

- Messages enregistrés définis par l’utilisateur

- Messages de mise à jour de l’interface utilisateur

## <a name="ranges-of-messages"></a>Gammes de messages

- Commandes

- Mettre à jour les messages des gestionnaires

- Notifications de contrôle

Bien que les macros de carte de message soient importantes, vous n’aurez généralement pas à les utiliser directement. C’est parce que [l’assistant de classe](mfc-class-wizard.md) crée automatiquement des entrées de carte de message dans vos fichiers sources lorsque vous l’utilisez pour associer les fonctions de traitement des messages avec les messages. Chaque fois que vous souhaitez modifier ou ajouter une entrée de carte de message, vous pouvez utiliser l’assistant de classe.

> [!NOTE]
> L’assistant de classe ne prend pas en charge les plages de carte de message. Vous devez écrire ces entrées de carte de message vous-même.

Cependant, les cartes de messages sont une partie importante de la Bibliothèque de classe de la Fondation Microsoft. Vous devez comprendre ce qu’ils font, et la documentation leur est fournie.

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

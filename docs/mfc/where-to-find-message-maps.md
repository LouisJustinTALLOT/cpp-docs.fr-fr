---
title: Où trouver des tables de messages
ms.date: 11/04/2016
helpviewer_keywords:
- macros, message map
- locating message maps
- message classes [MFC], finding
- message-map macros
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
ms.openlocfilehash: ab21369cecfa977a8397e7e2a7e68394e86e6927
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533469"
---
# <a name="where-to-find-message-maps"></a>Où trouver des tables de messages

Lorsque vous créez une nouvelle application squelette avec l’Assistant Application, l’Assistant Application écrit une table des messages pour chaque classe de cible de commande qu’il crée pour vous. Cela inclut votre application dérivée, document, vue et les classes de fenêtre frame. Certaines de ces tables des messages ont déjà entrées fournies par l’Assistant Application pour certains messages et les commandes prédéfinies, et certaines sont seulement des espaces réservés pour les gestionnaires que vous allez ajouter.

Table des messages d’une classe se trouve dans le. Fichier CPP pour la classe. Utilisez les mappages de messages de base qui crée l’Assistant Application, vous utiliser la fenêtre Propriétés pour ajouter des entrées pour les messages et les commandes qui gère chaque classe. Un mappage de message classique peut se présenter comme suit après avoir ajouté des entrées :

[!code-cpp[NVC_MFCMessageHandling#1](../mfc/codesnippet/cpp/where-to-find-message-maps_1.cpp)]

La table des messages se compose d’une collection de macros. Deux macros, [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) et [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map), mettre entre parenthèses de la table des messages. Autres macros, telles que `ON_COMMAND`, renseignez le contenu de la carte de message.

> [!NOTE]
>  Les macros de table des messages ne sont pas suivies par des points-virgules.

Lorsque vous utilisez l’Assistant Ajouter une classe pour créer une nouvelle classe, il fournit une table des messages pour la classe. Vous pouvez également créer une table des messages manuellement à l’aide de l’éditeur de code source.

## <a name="see-also"></a>Voir aussi

[Comment le Framework effectue des recherches dans les tables des messages](../mfc/how-the-framework-searches-message-maps.md)


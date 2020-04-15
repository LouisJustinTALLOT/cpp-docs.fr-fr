---
title: Où trouver des tables de messages
ms.date: 11/04/2016
helpviewer_keywords:
- macros, message map
- locating message maps
- message classes [MFC], finding
- message-map macros
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
ms.openlocfilehash: eec0ae43546e3cc0c08e3178c4808e21fa48686a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360162"
---
# <a name="where-to-find-message-maps"></a>Où trouver des tables de messages

Lorsque vous créez une nouvelle application squelette avec l’Assistant d’Application, l’Assistant d’Application écrit une carte de message pour chaque classe de commande-cible qu’elle crée pour vous. Cela comprend vos classes dérivées d’application, de document, de vue et de fenêtre de cadre. Certaines de ces cartes de messages ont déjà les entrées fournies par l’assistant d’application pour certains messages et commandes prédéfinises, et certains ne sont que des espaces réservés pour les gestionnaires que vous ajouterez.

La carte de message d’une classe est située dans le . Dossier du RPC pour la classe. En travaillant avec les cartes de message de base que l’Assistant d’Application crée, vous utilisez le [Class Wizard](reference/mfc-class-wizard.md) pour ajouter des entrées pour les messages et les commandes que chaque classe gérera. Une carte de message typique peut ressembler à ce qui suit après que vous ajoutez quelques entrées:

[!code-cpp[NVC_MFCMessageHandling#1](../mfc/codesnippet/cpp/where-to-find-message-maps_1.cpp)]

La carte des messages se compose d’une collection de macros. Deux macros, [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) et [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map), entre parenthèse de la carte de message. D’autres macros, telles que `ON_COMMAND`, remplir le contenu de la carte de message.

> [!NOTE]
> Les macros de carte de message ne sont pas suivies de semi-colons.

Lorsque vous utilisez l’assistant De classe Add pour créer une nouvelle classe, il fournit une carte de message pour la classe. Alternativement, vous pouvez créer une carte de message manuellement à l’aide de l’éditeur de code source.

## <a name="see-also"></a>Voir aussi

[Comment le Framework effectue des recherches dans les tables des messages](../mfc/how-the-framework-searches-message-maps.md)

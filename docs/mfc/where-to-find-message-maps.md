---
description: 'En savoir plus sur : où trouver les tables des messages'
title: Où trouver des tables de messages
ms.date: 11/04/2016
helpviewer_keywords:
- macros, message map
- locating message maps
- message classes [MFC], finding
- message-map macros
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
ms.openlocfilehash: 4796d358dd3be5455b22e348fbcc9236d1404ce8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97284965"
---
# <a name="where-to-find-message-maps"></a>Où trouver des tables de messages

Lorsque vous créez une nouvelle application squelette à l’aide de l’Assistant Application, l’Assistant application écrit une table des messages pour chaque classe cible de commande créée pour vous. Cela comprend vos classes d’application, de document, de vue et de fenêtre frame dérivées. Certaines de ces tables contiennent déjà les entrées fournies par l’Assistant application pour certains messages et commandes prédéfinies, tandis que d’autres sont simplement des espaces réservés pour les gestionnaires que vous allez ajouter.

La table des messages d’une classe se trouve dans le. Fichier CPP pour la classe. En utilisant les tables des messages de base créées par l’Assistant Application, vous utilisez l' [Assistant classe](reference/mfc-class-wizard.md) pour ajouter des entrées pour les messages et les commandes que chaque classe gérera. Une carte de message classique peut ressembler à ce qui suit après que vous avez ajouté des entrées :

[!code-cpp[NVC_MFCMessageHandling#1](../mfc/codesnippet/cpp/where-to-find-message-maps_1.cpp)]

La table des messages se compose d’une collection de macros. Deux macros, [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) et [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map), mettent en fourchette la table des messages. D’autres macros, telles que `ON_COMMAND` , remplissent le contenu de la table des messages.

> [!NOTE]
> Les macros de la table des messages ne sont pas suivies de points-virgules.

Lorsque vous utilisez l’Assistant Ajout d’une classe pour créer une classe, il fournit une table des messages pour la classe. Vous pouvez également créer une table des messages manuellement à l’aide de l’éditeur de code source.

## <a name="see-also"></a>Voir aussi

[Comment le Framework recherche les tables des messages](../mfc/how-the-framework-searches-message-maps.md)

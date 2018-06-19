---
title: Où trouver des tables des messages | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, message map
- locating message maps
- message classes [MFC], finding
- message-map macros
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 19dfaec7d97bed560665fce25c2ddf2cc816a483
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33383391"
---
# <a name="where-to-find-message-maps"></a>Où trouver des tables de messages
Lorsque vous créez une nouvelle application squelette avec l’Assistant Application, l’Assistant Application écrit une table des messages pour chaque classe cible de commande qu’il crée pour vous. Cela inclut votre application dérivée document, vue et classes de fenêtre frame. Certaines de ces tables des messages possèdent déjà des entrées fournies par l’Assistant Application pour certains messages et les commandes prédéfinies, et certaines sont seulement des espaces réservés pour les gestionnaires que vous ajouterez.  
  
 Table des messages d’une classe se trouve dans le. Fichier CPP pour la classe. Vous travaillez avec les tables des messages de base créé par l’Assistant Application, vous utilisez la fenêtre Propriétés pour ajouter des entrées pour les messages et les commandes qui gère chaque classe. Un mappage de message classique peut ressembler à ce qui suit après avoir ajouté des entrées :  
  
 [!code-cpp[NVC_MFCMessageHandling#1](../mfc/codesnippet/cpp/where-to-find-message-maps_1.cpp)]  
  
 La table des messages se compose d’une collection de macros. Deux macros, [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) et [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map), crochet de la table des messages. Autres macros, telles que `ON_COMMAND`, renseignez le contenu de la carte de message.  
  
> [!NOTE]
>  Les macros de table des messages ne sont pas suivies par des points-virgules.  
  
 Lorsque vous utilisez l’Assistant Ajouter une classe pour créer une nouvelle classe, il fournit une table des messages pour la classe. Vous pouvez également créer une table des messages manuellement à l’aide de l’éditeur de code source.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment le Framework effectue des recherches dans les tables des messages](../mfc/how-the-framework-searches-message-maps.md)


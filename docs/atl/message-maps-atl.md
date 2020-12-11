---
description: 'En savoir plus sur : tables des messages (ATL)'
title: Tables des messages (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message maps, ATL
- ATL, message handlers
ms.assetid: 9e100400-65c7-4a85-8857-4e6cb6dd7340
ms.openlocfilehash: c5b3340abbfbc66ac710ab716e3daa38dd7cd6df
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159516"
---
# <a name="message-maps-atl"></a>Tables des messages (ATL)

Une table des messages associe une fonction de gestionnaire à un message, une commande ou une notification particulier. À l’aide des [macros](../atl/reference/message-map-macros-atl.md)de la table des messages d’ATL, vous pouvez spécifier une table des messages pour une fenêtre. Les procédures de fenêtre dans `CWindowImpl` , `CDialogImpl` et `CContainedWindowT` dirigent les messages d’une fenêtre vers la table des messages.

Les [fonctions de gestionnaire de messages](../atl/message-handler-functions.md) acceptent un argument supplémentaire de type `BOOL&` . Cet argument indique si un message a été traité et s’il a la valeur TRUE par défaut. Une fonction gestionnaire peut ensuite affecter la valeur FALSe à l’argument pour indiquer qu’elle n’a pas géré de message. Dans ce cas, ATL continuera à rechercher une fonction de gestionnaire plus loin dans la table des messages. En affectant la valeur FALSe à cet argument, vous pouvez d’abord effectuer une action en réponse à un message, puis autoriser le traitement par défaut ou une autre fonction de gestionnaire à terminer la gestion du message.

## <a name="chained-message-maps"></a>Tables des messages chaînés

ATL vous permet également de chaîner des tables de messages, ce qui dirige la gestion des messages vers une table des messages définie dans une autre classe. Par exemple, vous pouvez implémenter la gestion des messages commune dans une classe distincte pour fournir un comportement uniforme pour l’ensemble du Chaînage Windows à cette classe. Vous pouvez chaîner à une classe de base ou à un membre de données de votre classe.

ATL prend également en charge le chaînage dynamique, ce qui vous permet de chaîner dans la table des messages d’un autre objet au moment de l’exécution. Pour implémenter le chaînage dynamique, vous devez dériver votre classe de [CDynamicChain](../atl/reference/cdynamicchain-class.md). Déclarez ensuite la macro [CHAIN_MSG_MAP_DYNAMIC](reference/message-map-macros-atl.md#chain_msg_map_dynamic) dans votre table des messages. CHAIN_MSG_MAP_DYNAMIC nécessite un numéro unique qui identifie l’objet et la table des messages dans laquelle vous effectuez le chaînage. Vous devez définir cette valeur unique à l’aide d’un appel à `CDynamicChain::SetChainEntry` .

Vous pouvez effectuer une chaîne vers n’importe quelle classe qui déclare une table des messages, à condition que la classe dérive de [CMessageMap](../atl/reference/cmessagemap-class.md). `CMessageMap` permet à un objet d’exposer ses tables de messages à d’autres objets. Notez que `CWindowImpl` dérive déjà de `CMessageMap` .

## <a name="alternate-message-maps"></a>Autres tables des messages

Enfin, ATL prend en charge les autres tables des messages, déclarées avec la macro [ALT_MSG_MAP](reference/message-map-macros-atl.md#alt_msg_map) . Chaque table des messages de remplacement est identifiée par un numéro unique, que vous transmettez à ALT_MSG_MAP. À l’aide de tables de messages secondaires, vous pouvez gérer les messages de plusieurs fenêtres dans une seule carte. Notez que, par défaut, `CWindowImpl` n’utilise pas de tables de messages de remplacement. Pour ajouter cette prise en charge, substituez la `WindowProc` méthode dans votre `CWindowImpl` classe dérivée de et appelez `ProcessWindowMessage` avec l’identificateur de la table des messages.

## <a name="see-also"></a>Voir aussi

[Implémentation d’une fenêtre](../atl/implementing-a-window.md)

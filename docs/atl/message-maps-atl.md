---
title: Tables (ATL) des messages | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- message maps, ATL
- ATL, message handlers
ms.assetid: 9e100400-65c7-4a85-8857-4e6cb6dd7340
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eaef52363ebdd79a1efb1e2e26bce016500cb722
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357256"
---
# <a name="message-maps-atl"></a>Tables des messages (ATL)
Une table des messages associe une fonction de gestionnaire d’un message particulier, une commande ou une notification. À l’aide d’ATL [macros de table de messages](../atl/reference/message-map-macros-atl.md), vous pouvez spécifier une table des messages pour une fenêtre. Les procédures de fenêtre de `CWindowImpl`, `CDialogImpl`, et `CContainedWindowT` diriger les messages d’une fenêtre à sa table des messages.  
  
 Le [fonctions gestionnaires de messages](../atl/message-handler-functions.md) accepte un argument supplémentaire de type `BOOL&`. Cet argument indique si un message a été traité, et elle est définie sur `TRUE` par défaut. Une fonction gestionnaire pouvez ensuite affecter l’argument `FALSE` pour indiquer qu’elle n’est pas gérée un message. Dans ce cas, ATL continuera à rechercher une fonction gestionnaire dans la table des messages. En affectant à cet argument `FALSE`, vous pouvez tout d’abord effectuer une action en réponse à un message et ensuite autoriser le traitement par défaut ou une autre fonction de gestionnaire à la fin du traitement du message.  
  
## <a name="chained-message-maps"></a>Tables des messages chaînées  
 ATL vous permet également à des tables des messages de chaîne qui indique à la gestion des messages vers une table des messages définie dans une autre classe. Par exemple, vous pouvez implémenter courantes de gestion des messages dans une classe distincte pour fournir un comportement uniforme pour toutes les fenêtres chaînées à cette classe. Vous pouvez chaîner à une classe de base ou à un membre de données de votre classe.  
  
 ATL prend également en charge le chaînage dynamique, ce qui vous permet de chaîne de la table des messages d’un autre objet en cours d’exécution. Pour implémenter le chaînage dynamique, vous devez dériver votre classe de [CDynamicChain](../atl/reference/cdynamicchain-class.md). Déclare le [macro CHAIN_MSG_MAP_DYNAMIC](reference/message-map-macros-atl.md#chain_msg_map_dynamic) macro dans votre table des messages. `CHAIN_MSG_MAP_DYNAMIC` nécessite un nombre unique qui identifie l’objet et la table à laquelle vous enchaînez des messages. Vous devez définir cette valeur unique par un appel à `CDynamicChain::SetChainEntry`.  
  
 Vous pouvez chaîner à toute classe qui déclare une table des messages, condition dérive de la classe [CMessageMap](../atl/reference/cmessagemap-class.md). `CMessageMap` permet à un objet d’exposer ses tables des messages à d’autres objets. Notez que `CWindowImpl` dérive déjà de `CMessageMap`.  
  
## <a name="alternate-message-maps"></a>Tables des messages de remplacement  
 Enfin, ATL prend en charge les tables des messages de remplacement, déclarés avec le [ALT_MSG_MAP](reference/message-map-macros-atl.md#alt_msg_map) (macro). Chaque table des messages secondaire est identifié par un numéro unique, que vous passez à `ALT_MSG_MAP`. À l’aide de messages de remplacement est mappé, vous pouvez gérer les messages de plusieurs fenêtres dans un mappage. Notez que, par défaut, `CWindowImpl` n’utilise pas les tables des messages de remplacement. Pour ajouter cette prise en charge, substituez le `WindowProc` méthode dans votre `CWindowImpl`-dérivée de classe et appelez `ProcessWindowMessage` avec l’identificateur de carte.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’une fenêtre](../atl/implementing-a-window.md)


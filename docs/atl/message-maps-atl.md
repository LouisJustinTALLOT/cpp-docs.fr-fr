---
title: Tables (ATL) des messages | Microsoft Docs
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
ms.openlocfilehash: 6c59cda065a84b7b664dcfccd7c876e19ef2f1aa
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848413"
---
# <a name="message-maps-atl"></a>Tables des messages (ATL)
Une table des messages associe une fonction de gestionnaire à un message particulier, une commande ou une notification. À l’aide d’ATL [message les macros de mappage](../atl/reference/message-map-macros-atl.md), vous pouvez spécifier une table des messages pour une fenêtre. Les procédures de fenêtre dans `CWindowImpl`, `CDialogImpl`, et `CContainedWindowT` diriger les messages d’une fenêtre à sa table des messages.  
  
 Le [fonctions gestionnaires de messages](../atl/message-handler-functions.md) accepte un argument supplémentaire de type `BOOL&`. Cet argument indique si un message a été traité, et il est défini sur TRUE par défaut. Une fonction de gestionnaire pouvez ensuite définir l’argument False pour indiquer qu’il n’a pas traité un message. Dans ce cas, ATL continuera à rechercher une fonction gestionnaire dans la table des messages. En définissant cet argument sur FALSE, vous pouvez tout d’abord effectuer une action en réponse à un message et ensuite autoriser le traitement par défaut ou une autre fonction de gestionnaire à la fin du traitement du message.  
  
## <a name="chained-message-maps"></a>Tables des messages chaînées  
 ATL vous permet également aux mappages de message de chaîne, qui dirige la gestion des messages vers une table des messages définie dans une autre classe. Par exemple, vous pouvez implémenter courantes de gestion des messages dans une classe distincte pour fournir un comportement uniforme pour toutes les fenêtres chaînées à cette classe. Vous pouvez chaîner à une classe de base ou à un membre de données de votre classe.  
  
 ATL prend également en charge le chaînage dynamique, ce qui vous permet de chaîne de la table des messages d’un autre objet en cours d’exécution. Pour implémenter le chaînage dynamique, vous devez dériver votre classe de [CDynamicChain](../atl/reference/cdynamicchain-class.md). Ensuite déclarer le [macro CHAIN_MSG_MAP_DYNAMIC](reference/message-map-macros-atl.md#chain_msg_map_dynamic) macro dans votre table des messages. Macro CHAIN_MSG_MAP_DYNAMIC requiert un nombre unique qui identifie l’objet et la table des messages auquel vous connectez en chaîne. Vous devez définir cette valeur unique via un appel à `CDynamicChain::SetChainEntry`.  
  
 Vous pouvez chaîner à toute classe qui déclare une table des messages, fournie par la classe dérive [CMessageMap](../atl/reference/cmessagemap-class.md). `CMessageMap` permet à un objet d’exposer ses tables des messages à d’autres objets. Notez que `CWindowImpl` dérive déjà de `CMessageMap`.  
  
## <a name="alternate-message-maps"></a>Tables des messages de remplacement  
 Enfin, ATL prend en charge les mappages de message alternatifs, déclarés avec le [ALT_MSG_MAP](reference/message-map-macros-atl.md#alt_msg_map) macro. Chaque table des messages secondaire est identifié par un numéro unique, vous passez à ALT_MSG_MAP. À l’aide de messages de remplacement est mappé, vous pouvez gérer les messages de plusieurs fenêtres dans une seule carte. Notez que par défaut, `CWindowImpl` n’utilise pas les tables des messages de remplacement. Pour ajouter cette prise en charge, substituez le `WindowProc` méthode dans votre `CWindowImpl`-dérivée de classe et appelez `ProcessWindowMessage` avec l’identificateur de carte.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’une fenêtre](../atl/implementing-a-window.md)


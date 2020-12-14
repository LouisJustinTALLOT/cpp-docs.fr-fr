---
description: 'En savoir plus sur : gestionnaire OnCmdMsg'
title: OnCmdMsg, gestionnaire
ms.date: 11/04/2016
f1_keywords:
- OnCmdMsg
helpviewer_keywords:
- messages, routing
- handlers [MFC]
- command routing [MFC], OnCmdMsg handler
- handlers, OnCmdMessage [MFC]
- OnCmdMessage method [MFC]
ms.assetid: 8df07024-506f-47e7-bba9-1c3bc5ad8ab6
ms.openlocfilehash: 69dfbd7ccc52a6d90b57ef9cedf0f896d65057b2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243963"
---
# <a name="oncmdmsg-handler"></a>OnCmdMsg, gestionnaire

Pour accomplir le routage des commandes, chaque cible de commande appelle la `OnCmdMsg` fonction membre de la cible de commande suivante dans la séquence. Les cibles de commande utilisent `OnCmdMsg` pour déterminer si elles peuvent gérer une commande et la router vers une autre cible de commande si elles ne peuvent pas la gérer.

Chaque classe de cible de commande peut remplacer la `OnCmdMsg` fonction membre. Les remplacements permettent à chaque classe d’acheminer des commandes vers une cible suivante particulière. Par exemple, une fenêtre frame achemine toujours les commandes vers sa fenêtre ou vue enfant actuelle, comme indiqué dans le tableau [itinéraire de commande standard](command-routing.md).

L’implémentation par défaut `CCmdTarget` de `OnCmdMsg` utilise la table des messages de la classe de cible de commande pour rechercher une fonction de gestionnaire pour chaque message de commande reçu, de la même façon que les messages standard sont recherchés. S’il trouve une correspondance, il appelle le gestionnaire. La recherche dans la table des messages est expliquée dans [la manière dont le Framework recherche les tables des messages](how-the-framework-searches-message-maps.md).

## <a name="see-also"></a>Voir aussi

[Comment le Framework appelle un gestionnaire](how-the-framework-calls-a-handler.md)

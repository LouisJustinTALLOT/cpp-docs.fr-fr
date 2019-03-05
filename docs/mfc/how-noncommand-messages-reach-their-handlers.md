---
title: Comment les messages noncommand parviennent à leurs gestionnaires
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], routing
- noncommand messages
- Windows messages [MFC], routing
- message handling [MFC], noncommand messages
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
ms.openlocfilehash: 4b9fb0a72b330380f0207db9968199a7e4c3d9b3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295056"
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>Comment les messages noncommand parviennent à leurs gestionnaires

Contrairement aux commandes, les messages Windows standard ne sont pas acheminés via une chaîne de cibles de commandes, mais sont généralement gérées par la fenêtre à laquelle Windows envoie le message. La fenêtre peut être une fenêtre frame principale, une fenêtre enfant MDI, un contrôle standard, une boîte de dialogue, une vue ou un autre type de fenêtre enfant.

Au moment de l’exécution, chaque fenêtre Windows est attaché à un objet de fenêtre (dérivé directement ou indirectement de `CWnd`) qui a ses propres fonctions de mappage et le Gestionnaire de message associé. L’infrastructure utilise la table des messages, comme pour une commande — pour mapper les messages entrants aux gestionnaires.

## <a name="see-also"></a>Voir aussi

[Méthode d’appel d’un gestionnaire par le Framework](../mfc/how-the-framework-calls-a-handler.md)

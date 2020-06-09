---
title: Comment les messages noncommand parviennent à leurs gestionnaires
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], routing
- noncommand messages
- Windows messages [MFC], routing
- message handling [MFC], noncommand messages
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
ms.openlocfilehash: c7b2bf819c5305da4039fae172578298d3b4e609
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618506"
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>Comment les messages noncommand parviennent à leurs gestionnaires

Contrairement aux commandes, les messages Windows standard ne sont pas acheminés via une chaîne de cibles de commande, mais sont généralement gérés par la fenêtre à laquelle Windows envoie le message. Il peut s’agir d’une fenêtre frame principale, d’une fenêtre enfant MDI, d’un contrôle standard, d’une boîte de dialogue, d’une vue ou d’un autre type de fenêtre enfant.

Au moment de l’exécution, chaque fenêtre Windows est attachée à un objet de fenêtre (dérivé directement ou indirectement de `CWnd` ) qui possède ses propres fonctions de gestionnaire et de table des messages associées. L’infrastructure utilise la table des messages, comme pour une commande, pour mapper les messages entrants aux gestionnaires.

## <a name="see-also"></a>Voir aussi

[Méthode d’appel d’un gestionnaire par le Framework](how-the-framework-calls-a-handler.md)

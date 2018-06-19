---
title: Comment les Messages noncommand parviennent à leurs gestionnaires | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- messages [MFC], routing
- noncommand messages
- Windows messages [MFC], routing
- message handling [MFC], noncommand messages
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3999c74bf7a612acb998e7a044c12948d7679d9b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343880"
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>Comment les messages noncommand parviennent à leurs gestionnaires
Contrairement aux commandes, les messages Windows standard ne sont pas acheminés via une chaîne de cibles de commandes, mais sont généralement gérées par la fenêtre à laquelle Windows envoie le message. La fenêtre peut être une fenêtre frame principale, une fenêtre enfant MDI, un contrôle standard, une boîte de dialogue, une vue ou un autre type de fenêtre enfant.  
  
 Au moment de l’exécution, chaque fenêtre Windows est attaché à un objet fenêtre (dérivé directement ou indirectement de `CWnd`) qui a ses propres fonctions de mappage et le Gestionnaire de message associé. L’infrastructure utilise la table des messages, comme pour une commande — pour mapper les messages entrants aux gestionnaires.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode d’appel d’un gestionnaire par le Framework](../mfc/how-the-framework-calls-a-handler.md)


---
title: Substitution du routage des commandes standard
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], overriding
- command handling [MFC], routing commands
- overriding, standard command routing
ms.assetid: 872b698a-7432-40c4-9008-68721e8effa5
ms.openlocfilehash: 5383c1053894d44e23baf51b19ac3df4e60158e5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57277948"
---
# <a name="overriding-the-standard-command-routing"></a>Substitution du routage des commandes standard

Dans de rares cas où vous devez implémenter une variation de la gamme de framework standard, vous pouvez la remplacer. L’idée est de modifier le routage dans une ou plusieurs classes en substituant `OnCmdMsg` dans ces classes. Procédez comme suit :

- Dans la classe qui interrompt la commande à passer à un objet non défini par défaut.

- Dans le nouvel objet non défini par défaut ou dans les cibles de la commande qu’il peut à son tour transmettre les commandes.

Si vous insérez un nouvel objet dans le routage, sa classe doit être une classe de cible de commande. Dans vos versions de remplacement de `OnCmdMsg`, veillez à appeler la version que vous remplacez. Consultez le [OnCmdMsg](../mfc/reference/ccmdtarget-class.md#oncmdmsg) fonction membre de classe `CCmdTarget` dans le *référence MFC* et les versions de classes telles que `CView` et `CDocument` dans le code source fourni pour obtenir des exemples.

## <a name="see-also"></a>Voir aussi

[Méthode d’appel d’un gestionnaire par le Framework](../mfc/how-the-framework-calls-a-handler.md)

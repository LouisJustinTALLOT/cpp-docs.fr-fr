---
description: 'En savoir plus sur : remplacement du routage des commandes standard'
title: Substitution du routage des commandes standard
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], overriding
- command handling [MFC], routing commands
- overriding, standard command routing
ms.assetid: 872b698a-7432-40c4-9008-68721e8effa5
ms.openlocfilehash: 5241e767beee85f92875128cc5ebccd1a23477f5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205991"
---
# <a name="overriding-the-standard-command-routing"></a>Substitution du routage des commandes standard

Dans de rares cas, lorsque vous devez implémenter une variation du routage de Framework standard, vous pouvez la remplacer. L’idée est de modifier le routage dans une ou plusieurs classes en remplaçant `OnCmdMsg` ces classes. Procédez comme suit :

- Dans la classe qui arrête l’ordre à passer à un objet non défini par défaut.

- Dans le nouvel objet ou la cible de la commande, il est possible qu’elle passe à son tour les commandes à.

Si vous insérez un nouvel objet dans le routage, sa classe doit être une classe de cible de commande. Dans vos versions de substitution de `OnCmdMsg` , veillez à appeler la version que vous substituez. Consultez la fonction membre [OnCmdMsg](reference/ccmdtarget-class.md#oncmdmsg) de `CCmdTarget` la classe dans la *référence MFC* et les versions de ces classes en tant que `CView` et `CDocument` dans le code source fourni pour obtenir des exemples.

## <a name="see-also"></a>Voir aussi

[Comment le Framework appelle un gestionnaire](how-the-framework-calls-a-handler.md)

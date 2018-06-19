---
title: Substitution du routage des commandes Standard | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], overriding
- command handling [MFC], routing commands
- overriding, standard command routing
ms.assetid: 872b698a-7432-40c4-9008-68721e8effa5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 13f6c8f262061477da95a4863965c04e9d75c49a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352810"
---
# <a name="overriding-the-standard-command-routing"></a>Substitution du routage des commandes standard
Dans de rares cas où vous devez implémenter une variation de la gamme de framework standard, vous pouvez la remplacer. Il est possible de modifier le routage dans une ou plusieurs classes en remplaçant `OnCmdMsg` dans ces classes. Pour ce faire :  
  
-   Dans la classe qui interrompt la commande à passer à un objet par défaut.  
  
-   Dans le nouvel objet par défaut ou dans les cibles de la commande qu’il peut à son tour transmettre les commandes.  
  
 Si vous insérez un nouvel objet dans le routage, sa classe doit être une classe cible de la commande. Dans les versions de substitution de `OnCmdMsg`, veillez à appeler la version que vous remplacez. Consultez le [OnCmdMsg](../mfc/reference/ccmdtarget-class.md#oncmdmsg) fonction membre de classe `CCmdTarget` dans les *référence MFC* et les versions de classes telles que `CView` et **CDocument** dans le code source fourni pour obtenir des exemples.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode d’appel d’un gestionnaire par le Framework](../mfc/how-the-framework-calls-a-handler.md)


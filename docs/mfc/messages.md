---
title: Messages | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- messages, MFC
- messages [MFC]
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: abd49410f9982788e9403f0cb83ca8656473417d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="messages"></a>Messages
La boucle de messages dans la **exécuter** fonction membre de classe `CWinApp` récupère les messages générés par divers événements en file d’attente. Par exemple, lorsque l’utilisateur clique sur la souris, Windows envoie plusieurs messages liés à la souris, tels que `WM_LBUTTONDOWN` lorsque le bouton gauche de la souris est enfoncé et `WM_LBUTTONUP` lorsque le bouton gauche de la souris est relâché. Implémentation de l’infrastructure de la boucle de messages d’application distribue le message à la fenêtre appropriée.  
  
 Les principales catégories de messages sont décrits dans [catégories de messages](../mfc/message-categories.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et commandes dans le Framework](../mfc/messages-and-commands-in-the-framework.md)


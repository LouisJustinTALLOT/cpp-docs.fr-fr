---
title: OnIdle, fonction membre | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- OnIdle
dev_langs:
- C++
helpviewer_keywords:
- processing messages [MFC]
- OnIdle method [MFC]
- idle loop processing [MFC]
- CWinApp class [MFC], OnIdle method [MFC]
- message handling [MFC], OnIdle method [MFC]
ms.assetid: 51adc874-0075-4f76-be1c-79283f46c10b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bbe912db448e424f18b6d72f6e148312c5940687
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350365"
---
# <a name="onidle-member-function"></a>OnIdle, fonction membre
Lorsque les messages Windows sont en cours de traitement, le framework appelle la [CWinApp](../mfc/reference/cwinapp-class.md) fonction membre [OnIdle](../mfc/reference/cwinapp-class.md#onidle) (décrite dans la référence de bibliothèque MFC).  
  
 Substituer `OnIdle` pour effectuer des tâches en arrière-plan. La version par défaut met à jour l’état des objets d’interface utilisateur tels que les boutons de barre d’outils et effectue un nettoyage des objets temporaires créés par le framework au cours de ses opérations. L’exemple suivant illustre comment la boucle de messages appelle `OnIdle` lorsqu’il y a aucun message dans la file d’attente.  
  
 ![Processus en boucle de message](../mfc/media/vc387c1.gif "vc387c1")  
La boucle de messages  
  
 Pour plus d’informations sur ce que vous pouvez faire dans la boucle inactive, consultez [traitement de la boucle inactive](../mfc/idle-loop-processing.md).  
  
## <a name="see-also"></a>Voir aussi  
 [CWinApp : classe d’application](../mfc/cwinapp-the-application-class.md)

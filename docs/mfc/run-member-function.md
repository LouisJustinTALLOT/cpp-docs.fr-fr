---
title: Exécuter une fonction membre | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- WinMain method [MFC]
ms.assetid: 24ab7597-2354-495b-9a20-2c8ccc7385b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a658af47723a9c19218b205a17cb46919d7abd59
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932284"
---
# <a name="run-member-function"></a>Exécuter une fonction membre
Une application framework passe la majorité de son temps dans le [exécuter](../mfc/reference/cwinapp-class.md#run) fonction membre de classe [CWinApp](../mfc/reference/cwinapp-class.md). Après l’initialisation, `WinMain` appelle `Run` pour traiter la boucle de messages.  
  
 `Run` permet de parcourir une boucle de message, la vérification de la file d’attente de message pour les messages disponibles. Si un message est disponible, `Run` distribue pour l’action. Si aucun message n’est disponible, ce qui est souvent le cas, `Run` appelle `OnIdle` d’effectuer tout traitement de temps d’inactivité que vous ou le framework peut-être nécessiter terminé. S’il y a aucun message et aucun traitement inactif, l’application attend jusqu'à ce que quelque chose se produit. Lorsque l’application se termine, `Run` appelle `ExitInstance`. La figure dans [fonction membre OnIdle](../mfc/onidle-member-function.md) montre la séquence d’actions dans la boucle de messages.  
  
 La distribution des messages dépend du type de message. Pour plus d’informations, consultez [Messages et commandes de l’infrastructure](../mfc/messages-and-commands-in-the-framework.md).  
  
## <a name="see-also"></a>Voir aussi  
 [CWinApp : classe d’application](../mfc/cwinapp-the-application-class.md)

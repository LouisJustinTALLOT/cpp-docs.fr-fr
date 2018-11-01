---
title: Exécuter une fonction membre
ms.date: 11/04/2016
helpviewer_keywords:
- WinMain method [MFC]
ms.assetid: 24ab7597-2354-495b-9a20-2c8ccc7385b3
ms.openlocfilehash: 8e6e74b8f0fd62f96d6d846bbba867f9189550ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666854"
---
# <a name="run-member-function"></a>Exécuter une fonction membre

Une application framework passe la plupart de son temps dans le [exécuter](../mfc/reference/cwinapp-class.md#run) fonction membre de classe [CWinApp](../mfc/reference/cwinapp-class.md). Après l’initialisation, `WinMain` appels `Run` pour traiter la boucle de message.

`Run` parcourt une boucle de messages, la vérification de la file d’attente de message pour les messages disponibles. Si un message est disponible, `Run` le distribue pour l’action. Si aucun message n’est disponible, ce qui est souvent le cas, `Run` appels `OnIdle` d’effectuer tout traitement de durée d’inactivité qui vous ou l’infrastructure peut-être terminé. S’il y a pas de messages et aucun traitement inactif pour cela, l’application attend jusqu'à ce que quelque chose se produit. Lorsque l’application se termine, `Run` appels `ExitInstance`. La figure dans [fonction membre OnIdle](../mfc/onidle-member-function.md) montre la séquence d’actions dans la boucle de message.

La distribution des messages varie selon le type de message. Pour plus d’informations, consultez [Messages et commandes dans le Framework](../mfc/messages-and-commands-in-the-framework.md).

## <a name="see-also"></a>Voir aussi

[CWinApp : classe d’application](../mfc/cwinapp-the-application-class.md)

---
title: Exécuter une fonction membre
ms.date: 11/04/2016
helpviewer_keywords:
- WinMain method [MFC]
ms.assetid: 24ab7597-2354-495b-9a20-2c8ccc7385b3
ms.openlocfilehash: 8271a10ad7439d2795dcc45d667b23b0932a0486
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308548"
---
# <a name="run-member-function"></a>Exécuter une fonction membre

Une application framework passe la plupart de son temps dans le [exécuter](../mfc/reference/cwinapp-class.md#run) fonction membre de classe [CWinApp](../mfc/reference/cwinapp-class.md). Après l’initialisation, `WinMain` appels `Run` pour traiter la boucle de message.

`Run` parcourt une boucle de messages, la vérification de la file d’attente de message pour les messages disponibles. Si un message est disponible, `Run` le distribue pour l’action. Si aucun message n’est disponible, ce qui est souvent le cas, `Run` appels `OnIdle` d’effectuer tout traitement de durée d’inactivité qui vous ou l’infrastructure peut-être terminé. S’il y a pas de messages et aucun traitement inactif pour cela, l’application attend jusqu'à ce que quelque chose se produit. Lorsque l’application se termine, `Run` appels `ExitInstance`. La figure dans [fonction membre OnIdle](../mfc/onidle-member-function.md) montre la séquence d’actions dans la boucle de message.

La distribution des messages varie selon le type de message. Pour plus d’informations, consultez [Messages et commandes dans le Framework](../mfc/messages-and-commands-in-the-framework.md).

## <a name="see-also"></a>Voir aussi

[CWinApp : Classe d’application](../mfc/cwinapp-the-application-class.md)

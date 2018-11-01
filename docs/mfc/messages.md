---
title: Messages
ms.date: 11/04/2016
helpviewer_keywords:
- messages, MFC
- messages [MFC]
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
ms.openlocfilehash: 033edfd289ea075b89e9d44111da94b987177470
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434539"
---
# <a name="messages"></a>Messages

La boucle de message dans le `Run` fonction membre de classe `CWinApp` récupère les messages générés par divers événements en file d’attente. Par exemple, lorsque l’utilisateur clique sur la souris, Windows envoie plusieurs messages liés à la souris, tels que WM_LBUTTONDOWN lorsque le bouton gauche de la souris est enfoncé et WM_LBUTTONUP lorsque le bouton gauche de la souris est relâché. Implémentation de l’infrastructure de la boucle de message d’application distribue le message à la fenêtre appropriée.

Les principales catégories de messages sont décrits dans [catégories de messages](../mfc/message-categories.md).

## <a name="see-also"></a>Voir aussi

[Messages et commandes dans le Framework](../mfc/messages-and-commands-in-the-framework.md)


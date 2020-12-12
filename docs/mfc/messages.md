---
description: 'En savoir plus sur : messages'
title: Messages
ms.date: 11/04/2016
helpviewer_keywords:
- messages, MFC
- messages [MFC]
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
ms.openlocfilehash: dbfec2794cc0dae5a7358b3c2ba39553643fb7c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203092"
---
# <a name="messages"></a>Messages

La boucle de message dans la `Run` fonction membre de la classe `CWinApp` récupère les messages mis en file d’attente générés par divers événements. Par exemple, quand l’utilisateur clique sur la souris, Windows envoie plusieurs messages liés à la souris, par exemple WM_LBUTTONDOWN lorsque le bouton gauche de la souris est enfoncé et WM_LBUTTONUP lorsque le bouton gauche de la souris est relâché. L’implémentation du Framework de la boucle de message d’application distribue le message à la fenêtre appropriée.

Les catégories de messages importantes sont décrites dans [catégories de message](message-categories.md).

## <a name="see-also"></a>Voir aussi

[Messages et commandes dans le Framework](messages-and-commands-in-the-framework.md)

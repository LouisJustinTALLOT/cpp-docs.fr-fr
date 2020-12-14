---
description: 'En savoir plus sur : exécuter la fonction membre'
title: Exécuter une fonction membre
ms.date: 11/04/2016
helpviewer_keywords:
- WinMain method [MFC]
ms.assetid: 24ab7597-2354-495b-9a20-2c8ccc7385b3
ms.openlocfilehash: ae67c6b02344a65735ce06775b1d1788d1dabf2c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217820"
---
# <a name="run-member-function"></a>Exécuter une fonction membre

Une application d’infrastructure consacre la plus grande partie de son temps à la fonction membre [Run](../mfc/reference/cwinapp-class.md#run) de la classe [CWinApp](../mfc/reference/cwinapp-class.md). Après l’initialisation, `WinMain` appelle `Run` pour traiter la boucle de message.

`Run` parcourt une boucle de messages pour rechercher les messages disponibles dans la file d’attente de messages. Si un message est disponible, `Run` le distribue pour action. Si aucun message n’est disponible, ce qui est souvent le cas, les `Run` appels `OnIdle` à effectuent tout traitement du temps d’inactivité que vous ou l’infrastructure devrez peut-être faire. S’il n’y a aucun message et aucun traitement inactif à faire, l’application attend jusqu’à ce qu’un événement se produise. Lorsque l’application se termine, `Run` appelle `ExitInstance` . La figure dans la [fonction membre OnIdle](../mfc/onidle-member-function.md) affiche la séquence d’actions dans la boucle de message.

La distribution des messages dépend du type de message. Pour plus d’informations, consultez [messages et commandes dans le Framework](../mfc/messages-and-commands-in-the-framework.md).

## <a name="see-also"></a>Voir aussi

[CWinApp : classe d’application](../mfc/cwinapp-the-application-class.md)

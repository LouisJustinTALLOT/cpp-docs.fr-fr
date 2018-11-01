---
title: OnIdle, fonction membre
ms.date: 11/04/2016
f1_keywords:
- OnIdle
helpviewer_keywords:
- processing messages [MFC]
- OnIdle method [MFC]
- idle loop processing [MFC]
- CWinApp class [MFC], OnIdle method [MFC]
- message handling [MFC], OnIdle method [MFC]
ms.assetid: 51adc874-0075-4f76-be1c-79283f46c10b
ms.openlocfilehash: 3d457c1675d5f5f3f88c67b1aac2d03509c21564
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662148"
---
# <a name="onidle-member-function"></a>OnIdle, fonction membre

Lorsqu’aucun message de Windows n’est en cours de traitement, l’infrastructure appelle la [CWinApp](../mfc/reference/cwinapp-class.md) fonction membre [OnIdle](../mfc/reference/cwinapp-class.md#onidle) (décrite dans la référence de bibliothèque MFC).

Substituer `OnIdle` pour effectuer des tâches en arrière-plan. La version par défaut met à jour l’état des objets d’interface utilisateur tels que des boutons de barre d’outils et effectue le nettoyage des objets temporaires créés par l’infrastructure au cours de ses opérations. L’exemple suivant illustre comment la boucle de messages appelle `OnIdle` lorsqu’il n’y a aucun message dans la file d’attente.

![Processus de boucle de message](../mfc/media/vc387c1.gif "vc387c1") la boucle de Message

Pour plus d’informations sur ce que vous pouvez faire dans la boucle inactive, consultez [traitement inactif de la boucle](../mfc/idle-loop-processing.md).

## <a name="see-also"></a>Voir aussi

[CWinApp : classe d’application](../mfc/cwinapp-the-application-class.md)

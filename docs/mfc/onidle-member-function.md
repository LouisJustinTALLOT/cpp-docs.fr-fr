---
title: OnIdle, fonction membre
ms.date: 11/19/2018
f1_keywords:
- OnIdle
helpviewer_keywords:
- processing messages [MFC]
- OnIdle method [MFC]
- idle loop processing [MFC]
- CWinApp class [MFC], OnIdle method [MFC]
- message handling [MFC], OnIdle method [MFC]
ms.assetid: 51adc874-0075-4f76-be1c-79283f46c10b
ms.openlocfilehash: c7cdd5cd2327be1b90e7fdb3694353acf8adcafe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394552"
---
# <a name="onidle-member-function"></a>OnIdle, fonction membre

Lorsqu’aucun message de Windows n’est en cours de traitement, l’infrastructure appelle la [CWinApp](../mfc/reference/cwinapp-class.md) fonction membre [OnIdle](../mfc/reference/cwinapp-class.md#onidle) (décrite dans la référence de bibliothèque MFC).

Substituer `OnIdle` pour effectuer des tâches en arrière-plan. La version par défaut met à jour l’état des objets d’interface utilisateur tels que des boutons de barre d’outils et effectue le nettoyage des objets temporaires créés par l’infrastructure au cours de ses opérations. L’exemple suivant illustre comment la boucle de messages appelle `OnIdle` lorsqu’il n’y a aucun message dans la file d’attente.

![Processus de boucle de message](../mfc/media/vc387c1.gif "processus de boucle de Message") <br/>
La boucle de Message

Pour plus d’informations sur ce que vous pouvez faire dans la boucle inactive, consultez [traitement inactif de la boucle](../mfc/idle-loop-processing.md).

## <a name="see-also"></a>Voir aussi

[CWinApp : Classe d’application](../mfc/cwinapp-the-application-class.md)

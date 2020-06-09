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
ms.openlocfilehash: 17595713f942c7fe7784fa2a12adbcc583cad418
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619845"
---
# <a name="onidle-member-function"></a>OnIdle, fonction membre

Quand aucun message Windows n’est traité, le Framework appelle la [CWinApp](reference/cwinapp-class.md) fonction membre CWinApp [OnIdle](reference/cwinapp-class.md#onidle) (décrite dans la référence de la bibliothèque MFC).

Remplacez `OnIdle` pour effectuer des tâches en arrière-plan. La version par défaut met à jour l’état des objets d’interface utilisateur tels que les boutons de la barre d’outils et effectue le nettoyage des objets temporaires créés par l’infrastructure au cours de ses opérations. L’illustration suivante montre comment la boucle de message appelle `OnIdle` lorsqu’il n’y a aucun message dans la file d’attente.

![Processus de boucle de message](../mfc/media/vc387c1.gif "Processus de boucle de message") <br/>
Boucle de messages

Pour plus d’informations sur ce que vous pouvez faire dans la boucle inactive, consultez [traitement des boucles inactives](idle-loop-processing.md).

## <a name="see-also"></a>Voir aussi

[CWinApp : classe d’application](cwinapp-the-application-class.md)

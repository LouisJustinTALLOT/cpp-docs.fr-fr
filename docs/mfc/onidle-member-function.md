---
title: OnIdle, fonction membre | Microsoft Docs
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
ms.openlocfilehash: 9b334a4561af40b69bc367ab5b1129afa8fb29ae
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377293"
---
# <a name="onidle-member-function"></a>OnIdle, fonction membre

Lorsqu’aucun message de Windows n’est en cours de traitement, l’infrastructure appelle la [CWinApp](../mfc/reference/cwinapp-class.md) fonction membre [OnIdle](../mfc/reference/cwinapp-class.md#onidle) (décrite dans la référence de bibliothèque MFC).

Substituer `OnIdle` pour effectuer des tâches en arrière-plan. La version par défaut met à jour l’état des objets d’interface utilisateur tels que des boutons de barre d’outils et effectue le nettoyage des objets temporaires créés par l’infrastructure au cours de ses opérations. L’exemple suivant illustre comment la boucle de messages appelle `OnIdle` lorsqu’il n’y a aucun message dans la file d’attente.

![Processus de boucle de message](../mfc/media/vc387c1.gif "vc387c1") la boucle de Message

Pour plus d’informations sur ce que vous pouvez faire dans la boucle inactive, consultez [traitement inactif de la boucle](../mfc/idle-loop-processing.md).

## <a name="see-also"></a>Voir aussi

[CWinApp : classe d’application](../mfc/cwinapp-the-application-class.md)

---
title: Traitement des notifications de contrôle Header
ms.date: 11/04/2016
helpviewer_keywords:
- CHeaderCtrl class [MFC], processing notifications
- controls [MFC], header
- notifications [MFC], processing for CHeaderCtrl
- header controls [MFC], processing notifications
- header control notifications
ms.assetid: e6c6af7c-d458-4d33-85aa-48014ccde5f6
ms.openlocfilehash: 4513bafedd531c7f0bcb103728c19c0940a2efc9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626770"
---
# <a name="processing-header-control-notifications"></a>Traitement des notifications de contrôle Header

Dans votre classe d’affichage ou de la boîte de dialogue, utilisez la fenêtre Propriétés pour créer un [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) fonction gestionnaire avec une instruction switch pour n’importe quel contrôle header ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) des messages de notification que vous souhaitez gérer (voir [mappage des Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md)). Notifications sont envoyées vers la fenêtre parente lorsque l’utilisateur clique ou double-clique sur un élément d’en-tête, fait glisser un séparateur entre les éléments et ainsi de suite.

Les messages de notification associés à un contrôle header sont répertoriés dans [référence de contrôle d’en-tête](https://msdn.microsoft.com/library/windows/desktop/bb775239) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Utilisation de CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)


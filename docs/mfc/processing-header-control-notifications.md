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
ms.openlocfilehash: 3c5d147741123f97a53b18a854db9204738d0a2f
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64339621"
---
# <a name="processing-header-control-notifications"></a>Traitement des notifications de contrôle Header

Dans votre classe d’affichage ou de la boîte de dialogue, utilisez la fenêtre Propriétés pour créer un [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) fonction gestionnaire avec une instruction switch pour n’importe quel contrôle header ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) des messages de notification que vous souhaitez gérer (voir [mappage des Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md)). Notifications sont envoyées vers la fenêtre parente lorsque l’utilisateur clique ou double-clique sur un élément d’en-tête, fait glisser un séparateur entre les éléments et ainsi de suite.

Les messages de notification associés à un contrôle header sont répertoriés dans [référence de contrôle d’en-tête](/windows/desktop/controls/header-control-reference) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Utilisation de CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

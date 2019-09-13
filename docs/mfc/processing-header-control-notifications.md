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
ms.openlocfilehash: bc811763fe3f4717b8baaeb4a23df1ae59bb1979
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908133"
---
# <a name="processing-header-control-notifications"></a>Traitement des notifications de contrôle Header

Dans votre classe d’affichage ou de boîte de dialogue, utilisez l' [Assistant classe](reference/mfc-class-wizard.md) pour créer une fonction de gestionnaire [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) avec une instruction switch pour tous les messages de notification de contrôle d’en-tête ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) que vous souhaitez gérer (consultez [mappage des messages à Functions](../mfc/reference/mapping-messages-to-functions.md)). Les notifications sont envoyées à la fenêtre parente lorsque l’utilisateur clique ou double-clique sur un élément d’en-tête, fait glisser un séparateur entre les éléments, et ainsi de suite.

Les messages de notification associés à un contrôle d’en-tête sont répertoriés dans [référence de contrôle d’en-tête](/windows/win32/controls/header-control-reference) dans la SDK Windows.

## <a name="see-also"></a>Voir aussi

[Utilisation de CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

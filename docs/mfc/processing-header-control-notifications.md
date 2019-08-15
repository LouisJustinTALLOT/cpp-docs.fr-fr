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
ms.openlocfilehash: f60a0c918476702881984f976b220130727cf4b0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507946"
---
# <a name="processing-header-control-notifications"></a>Traitement des notifications de contrôle Header

Dans votre classe d’affichage ou de boîte de dialogue, utilisez la Fenêtre Propriétés pour créer une fonction de gestionnaire [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) avec une instruction switch pour tous les messages de notification de contrôle d’en-tête ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) que vous souhaitez gérer (consultez [mappage de messages à des fonctions). ](../mfc/reference/mapping-messages-to-functions.md)). Les notifications sont envoyées à la fenêtre parente lorsque l’utilisateur clique ou double-clique sur un élément d’en-tête, fait glisser un séparateur entre les éléments, et ainsi de suite.

Les messages de notification associés à un contrôle d’en-tête sont répertoriés dans [référence de contrôle d’en-tête](/windows/win32/controls/header-control-reference) dans la SDK Windows.

## <a name="see-also"></a>Voir aussi

[Utilisation de CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

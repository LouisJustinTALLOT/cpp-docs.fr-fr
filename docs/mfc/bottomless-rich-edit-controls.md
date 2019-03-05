---
title: Contrôles RichEdit sans marge inférieure
ms.date: 11/04/2016
helpviewer_keywords:
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
ms.openlocfilehash: 6f078680777dcf80a4349ea34e4520cb56031f44
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270642"
---
# <a name="bottomless-rich-edit-controls"></a>Contrôles RichEdit sans marge inférieure

Votre application peut redimensionner un contrôle RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) en fonction des besoins afin qu’elle soit toujours la même taille que son contenu. Un contrôle RichEdit prend en charge cette fonctionnalité dite de « infinie » en envoyant sa fenêtre parente un [EN_REQUESTRESIZE](/windows/desktop/Controls/en-requestresize) message de notification chaque fois que la taille de son contenu change.

Lors du traitement de la **EN_REQUESTRESIZE** message de notification, une application doit être redimensionné le contrôle sur les dimensions de spécifié [REQRESIZE](/windows/desktop/api/richedit/ns-richedit-_reqresize) structure. Une application peut également déplacer toutes les informations près du contrôle pour prendre en charge la modification du contrôle de la hauteur. Pour redimensionner le contrôle, vous pouvez utiliser la `CWnd` fonction [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos).

Vous pouvez forcer un contrôle RichEdit pour envoyer un **EN_REQUESTRESIZE** message de notification à l’aide de la [fonction membre RequestResize](../mfc/reference/cricheditctrl-class.md#requestresize) fonction membre. Ce message peut être utile dans les [OnSize](../mfc/reference/cwnd-class.md#onsize) gestionnaire.

Pour recevoir des **EN_REQUESTRESIZE** des messages de notification, vous devez activer la notification à l’aide de la `SetEventMask` fonction membre.

## <a name="see-also"></a>Voir aussi

[Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

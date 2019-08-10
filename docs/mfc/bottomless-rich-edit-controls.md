---
title: Contrôles RichEdit sans marge inférieure
ms.date: 11/04/2016
helpviewer_keywords:
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
ms.openlocfilehash: d5650d34ffc350444061aa6147c38af016458811
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915267"
---
# <a name="bottomless-rich-edit-controls"></a>Contrôles RichEdit sans marge inférieure

Votre application peut redimensionner un contrôle Rich Edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) en fonction des besoins afin qu’elle ait toujours la même taille que son contenu. Un contrôle RichEdit prend en charge cette fonctionnalité dite «sans fin» en envoyant sa fenêtre parente un message de notification [EN_REQUESTRESIZE](/windows/desktop/Controls/en-requestresize) chaque fois que la taille de son contenu change.

Lors du traitement du message de notification **EN_REQUESTRESIZE** , une application doit redimensionner le contrôle avec les dimensions de la structure [REQRESIZE](/windows/desktop/api/richedit/ns-richedit-reqresize) spécifiée. Une application peut également déplacer toutes les informations près du contrôle pour s’adapter au changement de hauteur du contrôle. Pour redimensionner le contrôle, vous pouvez utiliser `CWnd` la fonction [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos).

Vous pouvez forcer un contrôle RichEdit sans fin pour envoyer un message de notification **EN_REQUESTRESIZE** à l’aide de la fonction membre [REQUESTRESIZE](../mfc/reference/cricheditctrl-class.md#requestresize) . Ce message peut être utile dans le gestionnaire [OnSize](../mfc/reference/cwnd-class.md#onsize) .

Pour recevoir des messages de notification **EN_REQUESTRESIZE** , vous devez activer la notification à `SetEventMask` l’aide de la fonction membre.

## <a name="see-also"></a>Voir aussi

[Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

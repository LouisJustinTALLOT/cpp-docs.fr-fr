---
description: En savoir plus sur les contrôles RichEdit sans fin
title: Contrôles RichEdit sans marge inférieure
ms.date: 11/04/2016
helpviewer_keywords:
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
ms.openlocfilehash: ad3f78fb4a5e172c16faf3421b6a9da91d422888
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339811"
---
# <a name="bottomless-rich-edit-controls"></a>Contrôles RichEdit sans marge inférieure

Votre application peut redimensionner un contrôle Rich Edit ([CRichEditCtrl](reference/cricheditctrl-class.md)) en fonction des besoins afin qu’elle ait toujours la même taille que son contenu. Un contrôle RichEdit prend en charge cette fonctionnalité dite « sans fin » en envoyant à sa fenêtre parente un message de notification [EN_REQUESTRESIZE](/windows/win32/Controls/en-requestresize) à chaque fois que la taille de son contenu change.

Lors du traitement du message de notification **EN_REQUESTRESIZE** , une application doit redimensionner le contrôle avec les dimensions de la structure [REQRESIZE](/windows/win32/api/richedit/ns-richedit-reqresize) spécifiée. Une application peut également déplacer toutes les informations près du contrôle pour s’adapter au changement de hauteur du contrôle. Pour redimensionner le contrôle, vous pouvez utiliser la `CWnd` fonction [SetWindowPos](reference/cwnd-class.md#setwindowpos).

Vous pouvez forcer un contrôle RichEdit sans fin pour envoyer un **EN_REQUESTRESIZE** message de notification à l’aide de la fonction membre [REQUESTRESIZE](reference/cricheditctrl-class.md#requestresize) . Ce message peut être utile dans le gestionnaire [OnSize](reference/cwnd-class.md#onsize) .

Pour recevoir des messages de notification **EN_REQUESTRESIZE** , vous devez activer la notification à l’aide de la `SetEventMask` fonction membre.

## <a name="see-also"></a>Voir aussi

[Utilisation de CRichEditCtrl](using-cricheditctrl.md)<br/>
[Contrôles](controls-mfc.md)

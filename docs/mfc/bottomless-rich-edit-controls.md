---
title: Contrôles RichEdit | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6f2b08f6c04d345b4ae3ab32c6d0f17a1d8a4647
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343309"
---
# <a name="bottomless-rich-edit-controls"></a>Contrôles RichEdit sans marge inférieure
Votre application peut redimensionner un contrôle RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) en fonction des besoins afin qu’il soit toujours la même taille que son contenu. Un contrôle RichEdit prend en charge cette fonctionnalité dite de « sans fin » en envoyant à sa fenêtre parente un [EN_REQUESTRESIZE](http://msdn.microsoft.com/library/windows/desktop/bb787983) message de notification chaque fois que la taille de son contenu change.  
  
 Lors du traitement de la **EN_REQUESTRESIZE** message de notification, une application doit redimensionner le contrôle aux dimensions spécifié [REQRESIZE](http://msdn.microsoft.com/library/windows/desktop/bb787950) structure. Une application peut également déplacer une information à proximité du contrôle pour prendre en charge la modification du contrôle de la hauteur. Pour redimensionner le contrôle, vous pouvez utiliser la `CWnd` fonction [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos).  
  
 Vous pouvez forcer un contrôle RichEdit pour envoyer un **EN_REQUESTRESIZE** message de notification à l’aide de la [fonction membre RequestResize](../mfc/reference/cricheditctrl-class.md#requestresize) fonction membre. Ce message peut être utile dans les [OnSize](../mfc/reference/cwnd-class.md#onsize) gestionnaire.  
  
 Pour recevoir des **EN_REQUESTRESIZE** messages de notification, vous devez activer la notification à l’aide de la `SetEventMask` fonction membre.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)


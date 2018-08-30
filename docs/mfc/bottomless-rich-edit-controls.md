---
title: Contrôles RichEdit | Microsoft Docs
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
ms.openlocfilehash: c9e3115000b7b45d9b48a1ac0d274eb32c11f4d0
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218877"
---
# <a name="bottomless-rich-edit-controls"></a>Contrôles RichEdit sans marge inférieure
Votre application peut redimensionner un contrôle RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) en fonction des besoins afin qu’elle soit toujours la même taille que son contenu. Un contrôle RichEdit prend en charge cette fonctionnalité dite de « infinie » en envoyant sa fenêtre parente un [EN_REQUESTRESIZE](/windows/desktop/Controls/en-requestresize) message de notification chaque fois que la taille de son contenu change.  
  
 Lors du traitement de la **EN_REQUESTRESIZE** message de notification, une application doit être redimensionné le contrôle sur les dimensions de spécifié [REQRESIZE](/windows/desktop/api/richedit/ns-richedit-_reqresize) structure. Une application peut également déplacer toutes les informations près du contrôle pour prendre en charge la modification du contrôle de la hauteur. Pour redimensionner le contrôle, vous pouvez utiliser la `CWnd` fonction [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos).  
  
 Vous pouvez forcer un contrôle RichEdit pour envoyer un **EN_REQUESTRESIZE** message de notification à l’aide de la [fonction membre RequestResize](../mfc/reference/cricheditctrl-class.md#requestresize) fonction membre. Ce message peut être utile dans les [OnSize](../mfc/reference/cwnd-class.md#onsize) gestionnaire.  
  
 Pour recevoir des **EN_REQUESTRESIZE** des messages de notification, vous devez activer la notification à l’aide de la `SetEventMask` fonction membre.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)


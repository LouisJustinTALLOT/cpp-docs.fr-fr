---
title: Notifications envoyées par les contrôles d’Animation | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1696389ce3dc40c5d02ec660ebaeb6bf3e6c3ec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33345239"
---
# <a name="notifications-sent-by-animation-controls"></a>Notifications envoyées par les contrôles d'animation
Un contrôle animation ([CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) envoie les deux types de messages de notification. Les notifications sont envoyées sous la forme de [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) messages.  
  
 Le [message ACN_START](http://msdn.microsoft.com/library/windows/desktop/bb761891) message est envoyé lorsque le contrôle animation a commencé la lecture d’un élément. Le [message ACN_STOP](http://msdn.microsoft.com/library/windows/desktop/bb761893) message est envoyé lorsque le contrôle animation a fini ou arrêté la lecture d’un élément.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CAnimateCtrl](../mfc/using-canimatectrl.md)   
 [Contrôles](../mfc/controls-mfc.md)


---
title: Messages de Notification du Slider | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CSliderCtrl class [MFC], notifications
- slider controls [MFC], notification messages
- messages, notification
- notifications [MFC], CSliderCtrl
ms.assetid: b9121104-3889-4a10-92bf-f3723f1af9d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c383458905d16dda935254e56a5aa9f56a153e83
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956159"
---
# <a name="slider-notification-messages"></a>Messages de notification du Slider
Un contrôle slider notifie sa fenêtre parente des actions de l’utilisateur en envoyant le parent des messages WM_HSCROLL ou WM_VSCROLL, en fonction de l’orientation du contrôle slider. Pour gérer ces messages, ajoutez des gestionnaires pour les messages WM_HSCROLL et WM_VSCROLL à la fenêtre parente. Le [OnHScroll](../mfc/reference/cwnd-class.md#onhscroll) et [OnVScroll](../mfc/reference/cwnd-class.md#onvscroll) fonctions membres recevront un code de notification, la position du curseur et un pointeur vers le [CSliderCtrl](../mfc/reference/csliderctrl-class.md) objet. Notez que le pointeur est de type `CScrollBar *` bien qu’il pointe vers un `CSliderCtrl` objet. Vous devrez peut-être convertir ce pointeur si vous avez besoin manipuler le contrôle slider.  
  
 Au lieu d’utiliser la barre des codes de notification de défilement, les contrôles slider envoient un ensemble différent de codes de notification. Un contrôle slider envoie les codes de notification TB_BOTTOM, quel, TB_LINEUP et TB_TOP uniquement lorsque l’utilisateur interagit avec un contrôle de curseur à l’aide du clavier. Les messages de notification TB_THUMBPOSITION et TB_THUMBTRACK sont uniquement envoyés lorsque l’utilisateur est à l’aide de la souris. Les codes de notification TB_ENDTRACK, TB_PAGEDOWN et TB_PAGEUP sont envoyés dans les deux cas.  
  
 Le tableau suivant répertorie les messages de notification de contrôle slider et des événements (codes de touches virtuelles ou les événements de souris) qui provoquent l’envoi de notifications. (Pour une liste des codes de touches virtuelles, consultez Winuser.h.)  
  
|Message de notification|Événement ayant déclenché la notification à envoyer|  
|--------------------------|-------------------------------------------|  
|TB_BOTTOM|VK_END|  
|TB_ENDTRACK|WM_KEYUP (l’utilisateur a une clé qui a envoyé un code de touche virtuelle pertinentes)|  
|QUEL|VK_RIGHT ou VK_DOWN|  
|TB_LINEUP|VK_LEFT ou VK_UP|  
|TB_PAGEDOWN|VK_NEXT (l’utilisateur a cliqué sur le canal en dessous ou à droite du curseur)|  
|TB_PAGEUP|VK_PRIOR (l’utilisateur a cliqué sur le canal au-dessus ou à gauche du curseur)|  
|TB_THUMBPOSITION|WM_LBUTTONUP suivant un message de notification TB_THUMBTRACK|  
|TB_THUMBTRACK|Déplacement du curseur (l’utilisateur fait glisser le curseur)|  
|TB_TOP|VK_HOME|  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CSliderCtrl](../mfc/using-csliderctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)


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
ms.openlocfilehash: b003e23a1fef2b44600b9fd15dfe4ca541df5369
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381977"
---
# <a name="slider-notification-messages"></a>Messages de notification du Slider
Un contrôle slider notifie sa fenêtre parente des actions de l’utilisateur en envoyant au parent `WM_HSCROLL` ou `WM_VSCROLL` messages, en fonction de l’orientation du contrôle slider. Pour gérer ces messages, ajouter des gestionnaires pour les `WM_HSCROLL` et `WM_VSCROLL` messages à la fenêtre parente. Le [OnHScroll](../mfc/reference/cwnd-class.md#onhscroll) et [OnVScroll](../mfc/reference/cwnd-class.md#onvscroll) fonctions membres recevront un code de notification, la position du curseur et un pointeur vers le [CSliderCtrl](../mfc/reference/csliderctrl-class.md) objet. Notez que le pointeur est de type **CScrollBar \***  bien qu’il pointe vers un `CSliderCtrl` objet. Vous devrez peut-être convertir ce pointeur si vous avez besoin manipuler le contrôle slider.  
  
 Au lieu d’utiliser la barre des codes de notification de défilement, les contrôles slider envoient un ensemble différent de codes de notification. Un contrôle slider envoie le **TB_BOTTOM**, **quel**, **TB_LINEUP**, et **TB_TOP** uniquement lorsque l’utilisateur interagit les codes de notification avec un contrôle de curseur à l’aide du clavier. Le **TB_THUMBPOSITION** et **TB_THUMBTRACK** messages de notification sont envoyés uniquement lorsque l’utilisateur est à l’aide de la souris. Le **TB_ENDTRACK**, **TB_PAGEDOWN**, et **TB_PAGEUP** codes de notification sont envoyés dans les deux cas.  
  
 Le tableau suivant répertorie les messages de notification de contrôle slider et des événements (codes de touches virtuelles ou les événements de souris) qui provoquent l’envoi de notifications. (Pour une liste des codes de touches virtuelles, consultez Winuser.h.)  
  
|Message de notification|Événement ayant déclenché la notification à envoyer|  
|--------------------------|-------------------------------------------|  
|**TB_BOTTOM**|**VK_END**|  
|**TB_ENDTRACK**|`WM_KEYUP` (l’utilisateur a une clé qui a envoyé un code de touche virtuelle pertinentes)|  
|**QUEL**|**VK_RIGHT** ou **VK_DOWN**|  
|**TB_LINEUP**|**VK_LEFT** ou **VK_UP**|  
|**TB_PAGEDOWN**|**VK_NEXT** (l’utilisateur a cliqué sur le canal en dessous ou à droite du curseur)|  
|**TB_PAGEUP**|**VK_PRIOR** (l’utilisateur a cliqué sur le canal au-dessus ou à gauche du curseur)|  
|**TB_THUMBPOSITION**|`WM_LBUTTONUP` suivant une **TB_THUMBTRACK** message de notification|  
|**TB_THUMBTRACK**|Déplacement du curseur (l’utilisateur fait glisser le curseur)|  
|**TB_TOP**|**VK_HOME**|  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CSliderCtrl](../mfc/using-csliderctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)


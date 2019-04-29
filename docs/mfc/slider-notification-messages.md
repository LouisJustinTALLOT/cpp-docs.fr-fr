---
title: Messages de notification du Slider
ms.date: 11/04/2016
helpviewer_keywords:
- CSliderCtrl class [MFC], notifications
- slider controls [MFC], notification messages
- messages, notification
- notifications [MFC], CSliderCtrl
ms.assetid: b9121104-3889-4a10-92bf-f3723f1af9d0
ms.openlocfilehash: bee2d602512ea1a6af39b0bb218ee7333b399c80
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307326"
---
# <a name="slider-notification-messages"></a>Messages de notification du Slider

Un contrôle slider notifie sa fenêtre parente des actions de l’utilisateur en envoyant le parent des messages WM_HSCROLL ou WM_VSCROLL, selon l’orientation du contrôle slider. Pour gérer ces messages, ajoutez des gestionnaires pour les messages WM_HSCROLL et WM_VSCROLL messages vers la fenêtre parente. Le [OnHScroll](../mfc/reference/cwnd-class.md#onhscroll) et [OnVScroll](../mfc/reference/cwnd-class.md#onvscroll) fonctions membres recevront un code de notification, la position du curseur et un pointeur vers le [CSliderCtrl](../mfc/reference/csliderctrl-class.md) objet. Notez que le pointeur est de type `CScrollBar *` même si elle pointe vers un `CSliderCtrl` objet. Vous devrez peut-être convertir ce pointeur si vous avez besoin de manipuler le contrôle slider.

Au lieu d’utiliser la barre des codes de notification de défilement, contrôles slider envoient un ensemble différent de codes de notification. Un contrôle slider envoie les codes de notification TB_BOTTOM, quel, TB_LINEUP et TB_TOP uniquement lorsque l’utilisateur interagit avec un contrôle slider à l’aide du clavier. Les messages de notification TB_THUMBPOSITION et TB_THUMBTRACK sont envoyés uniquement lorsque l’utilisateur est à l’aide de la souris. Les codes de notification TB_ENDTRACK, TB_PAGEDOWN et TB_PAGEUP sont envoyés dans les deux cas.

Le tableau suivant répertorie les messages de notification de contrôle de curseur et les événements (codes de touches virtuelles ou les événements de souris) qui provoquent l’envoi de notifications. (Pour une liste des codes de touches virtuelles, consultez Winuser.h.)

|Message de notification|Événement à l’origine de la notification à envoyer|
|--------------------------|-------------------------------------------|
|TB_BOTTOM|VK_END|
|TB_ENDTRACK|WM_KEYUP (l’utilisateur a relâché une clé qui a envoyé un code de touche virtuelle pertinents)|
|TB_LINEDOWN|VK_RIGHT ou VK_DOWN|
|TB_LINEUP|VK_LEFT ou VK_UP|
|TB_PAGEDOWN|VK_NEXT (l’utilisateur a cliqué sur le canal ci-dessous ou à droite du curseur)|
|TB_PAGEUP|VK_PRIOR (l’utilisateur a cliqué sur le canal au-dessus ou à gauche du curseur)|
|TB_THUMBPOSITION|WM_LBUTTONUP suivant un message de notification TB_THUMBTRACK|
|TB_THUMBTRACK|Déplacement du curseur (l’utilisateur fait glisser le curseur)|
|TB_TOP|VK_HOME|

## <a name="see-also"></a>Voir aussi

[Utilisation de CSliderCtrl](../mfc/using-csliderctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

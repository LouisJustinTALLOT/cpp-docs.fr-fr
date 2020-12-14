---
description: 'En savoir plus sur : les messages de notification Slider'
title: Messages de notification du Slider
ms.date: 11/04/2016
helpviewer_keywords:
- CSliderCtrl class [MFC], notifications
- slider controls [MFC], notification messages
- messages, notification
- notifications [MFC], CSliderCtrl
ms.assetid: b9121104-3889-4a10-92bf-f3723f1af9d0
ms.openlocfilehash: fab8d515e71fd2ca8fd390a41b6d1bf68442c24c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216884"
---
# <a name="slider-notification-messages"></a>Messages de notification du Slider

Un contrôle Slider avertit la fenêtre parente des actions de l’utilisateur en envoyant le WM_HSCROLL parent ou les messages WM_VSCROLL, en fonction de l’orientation du contrôle Slider. Pour gérer ces messages, ajoutez des gestionnaires pour les messages WM_HSCROLL et WM_VSCROLL à la fenêtre parente. Un code de notification, la position du curseur et un pointeur vers l’objet [CSliderCtrl](../mfc/reference/csliderctrl-class.md) sont passés aux fonctions membres [OnHScroll](../mfc/reference/cwnd-class.md#onhscroll) et [OnVScroll](../mfc/reference/cwnd-class.md#onvscroll) . Notez que le pointeur est de type, `CScrollBar *` même s’il pointe vers un `CSliderCtrl` objet. Vous devrez peut-être convertir ce pointeur si vous devez manipuler le contrôle Slider.

Au lieu d’utiliser les codes de notification de la barre de défilement, les contrôles Slider envoient un ensemble différent de codes de notification. Un contrôle Slider envoie les codes de notification TB_BOTTOM, TB_LINEDOWN, TB_LINEUP et TB_TOP uniquement lorsque l’utilisateur interagit avec un contrôle Slider à l’aide du clavier. Les messages de notification TB_THUMBPOSITION et TB_THUMBTRACK sont envoyés uniquement lorsque l’utilisateur utilise la souris. Les codes de notification TB_ENDTRACK, TB_PAGEDOWN et TB_PAGEUP sont envoyés dans les deux cas.

Le tableau suivant répertorie les messages de notification du contrôle Slider et les événements (codes de touches virtuelles ou événements de souris) qui entraînent l’envoi des notifications. (Pour obtenir la liste des codes de touches virtuelles standard, consultez Winuser. h.)

|Message de notification|Événement provoquant l’envoi de notifications|
|--------------------------|-------------------------------------------|
|TB_BOTTOM|VK_END|
|TB_ENDTRACK|WM_KEYUP (l’utilisateur a publié une clé qui a envoyé un code de clé virtuelle approprié)|
|TB_LINEDOWN|VK_RIGHT ou VK_DOWN|
|TB_LINEUP|VK_LEFT ou VK_UP|
|TB_PAGEDOWN|VK_NEXT (l’utilisateur a cliqué sur le canal en dessous ou à droite du curseur)|
|TB_PAGEUP|VK_PRIOR (l’utilisateur a cliqué sur le canal au-dessus ou à gauche du curseur)|
|TB_THUMBPOSITION|WM_LBUTTONUP après un message de notification TB_THUMBTRACK|
|TB_THUMBTRACK|Déplacement du curseur (l’utilisateur a fait glisser le curseur)|
|TB_TOP|VK_HOME|

## <a name="see-also"></a>Voir aussi

[Utilisation de CSliderCtrl](../mfc/using-csliderctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

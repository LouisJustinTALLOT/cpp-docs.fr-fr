---
title: Notifications envoyées par les contrôles d'animation
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
ms.openlocfilehash: 68ede3bc55669a29eef192d38b29b8c1ab433e4b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508019"
---
# <a name="notifications-sent-by-animation-controls"></a>Notifications envoyées par les contrôles d'animation

Un contrôle d’animation ([CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) envoie deux types différents de messages de notification. Les notifications sont envoyées sous la forme de messages [WM_COMMAND](/windows/win32/menurc/wm-command) .

Le message [ACN_START](/windows/win32/Controls/acn-start) est envoyé lorsque le contrôle d’animation a commencé à écouter un clip. Le message [ACN_STOP](/windows/win32/Controls/acn-stop) est envoyé lorsque le contrôle d’animation est terminé ou arrêté en lisant un clip.

## <a name="see-also"></a>Voir aussi

[Utilisation de CAnimateCtrl](../mfc/using-canimatectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

---
title: Notifications envoyées par les contrôles d'animation
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
ms.openlocfilehash: 2a736e4315091b1b26daceb4fe0ce9672ab33ff6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281263"
---
# <a name="notifications-sent-by-animation-controls"></a>Notifications envoyées par les contrôles d'animation

Un contrôle animation ([CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) envoie deux types de messages de notification. Les notifications sont envoyées sous la forme de [WM_COMMAND](/windows/desktop/menurc/wm-command) messages.

Le [message ACN_START](/windows/desktop/Controls/acn-start) message est envoyé lorsque le contrôle d’animation a commencé la lecture d’un élément. Le [message ACN_STOP](/windows/desktop/Controls/acn-stop) message est envoyé lorsque le contrôle de l’animation est terminée ou a cessé de lire un clip.

## <a name="see-also"></a>Voir aussi

[Utilisation de CAnimateCtrl](../mfc/using-canimatectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

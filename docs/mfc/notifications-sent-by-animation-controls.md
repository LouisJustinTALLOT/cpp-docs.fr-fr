---
description: 'En savoir plus sur : notifications envoyées par les contrôles d’animation'
title: Notifications envoyées par les contrôles d'animation
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
ms.openlocfilehash: 17dbd041e1c22b8d6542e64fd8b99d86389ea2d4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280558"
---
# <a name="notifications-sent-by-animation-controls"></a>Notifications envoyées par les contrôles d'animation

Un contrôle d’animation ([CAnimateCtrl](reference/canimatectrl-class.md)) envoie deux types différents de messages de notification. Les notifications sont envoyées sous la forme de messages [WM_COMMAND](/windows/win32/menurc/wm-command) .

Le message [ACN_START](/windows/win32/Controls/acn-start) est envoyé lorsque le contrôle d’animation a commencé à exécuter un clip. Le message [ACN_STOP](/windows/win32/Controls/acn-stop) est envoyé lorsque le contrôle d’animation est terminé ou qu’il a cessé de lancer un clip.

## <a name="see-also"></a>Voir aussi

[Utilisation de CAnimateCtrl](using-canimatectrl.md)<br/>
[Contrôles](controls-mfc.md)

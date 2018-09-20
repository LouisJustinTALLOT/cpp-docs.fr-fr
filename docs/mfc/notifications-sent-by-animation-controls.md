---
title: Notifications envoyées par les contrôles d’Animation | Microsoft Docs
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
ms.openlocfilehash: eb83fe6195c01c1e9dbcc2c00e43738af9ebc8e2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386390"
---
# <a name="notifications-sent-by-animation-controls"></a>Notifications envoyées par les contrôles d'animation

Un contrôle animation ([CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) envoie deux types de messages de notification. Les notifications sont envoyées sous la forme de [WM_COMMAND](/windows/desktop/menurc/wm-command) messages.

Le [message ACN_START](/windows/desktop/Controls/acn-start) message est envoyé lorsque le contrôle d’animation a commencé la lecture d’un élément. Le [message ACN_STOP](/windows/desktop/Controls/acn-stop) message est envoyé lorsque le contrôle de l’animation est terminée ou a cessé de lire un clip.

## <a name="see-also"></a>Voir aussi

[Utilisation de CAnimateCtrl](../mfc/using-canimatectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)


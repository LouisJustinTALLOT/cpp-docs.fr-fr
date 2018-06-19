---
title: Paramètres de l’outil de contrôle ToolTip | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tool tips [MFC], activating
- CToolTipCtrl class [MFC], settings
ms.assetid: ff8c5c46-2047-403a-bd98-ffec3d21ee3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b61fb9450e6206c8f96102b5feeec6fbf3bead3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379949"
---
# <a name="settings-for-the-tool-tip-control"></a>Paramètres du contrôle d’info-bulle
Vous pouvez définir le contrôle d’info-bulle ([CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)) de sorte qu’il soit actif ou inactif. Quand vous le définissez comme étant actif, le contrôle d’info-bulle s’affiche quand le curseur se trouve sur un outil. Quand vous le définissez comme étant inactif, le contrôle d’info-bulle ne s’affiche pas, même si le curseur se trouve sur un outil. Appelez [Activate](../mfc/reference/ctooltipctrl-class.md#activate) pour activer ou désactiver un contrôle d’info-bulle.  
  
 Vous pouvez définir une info-bulle active pour qu’elle s’affiche quand le curseur se trouve sur un outil, que la fenêtre propriétaire du contrôle d’info-bulle soit active ou inactive, en utilisant le style **TTS_ALWAYSTIP** . Si vous n’utilisez pas ce style, le contrôle d’info-bulle s’affiche quand la fenêtre de propriétaire de l’outil est active, mais pas quand elle est inactive.  
  
 La plupart des applications contiennent des barres d’outils qui correspondent à des commandes de menu. Pour ces outils, il est pratique que le contrôle d’info-bulle affiche le même texte que l’élément de menu correspondant. Le système supprime automatiquement les caractères « et commercial » (&) accélérateur à partir de toutes les chaînes passées à un contrôle info-bulle, sauf si le contrôle a le **TTS_NOPREFIX** style.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)


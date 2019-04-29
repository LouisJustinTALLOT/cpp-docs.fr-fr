---
title: Paramètres du contrôle d’info-bulle
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], activating
- CToolTipCtrl class [MFC], settings
ms.assetid: ff8c5c46-2047-403a-bd98-ffec3d21ee3a
ms.openlocfilehash: 5cc72401da95e63520b544865ea509a8ad219bda
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307612"
---
# <a name="settings-for-the-tool-tip-control"></a>Paramètres du contrôle d’info-bulle

Vous pouvez définir le contrôle d’info-bulle ([CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)) de sorte qu’il soit actif ou inactif. Quand vous le définissez comme étant actif, le contrôle d’info-bulle s’affiche quand le curseur se trouve sur un outil. Quand vous le définissez comme étant inactif, le contrôle d’info-bulle ne s’affiche pas, même si le curseur se trouve sur un outil. Appelez [Activate](../mfc/reference/ctooltipctrl-class.md#activate) pour activer ou désactiver un contrôle d’info-bulle.

Vous pouvez définir une info-bulle active pour afficher l’info-bulle lorsque le curseur se trouve sur un outil, fenêtre de propriétaire du contrôle info-bulle est active ou inactive, en utilisant le style TTS_ALWAYSTIP ou non. Si vous n’utilisez pas ce style, le contrôle d’info-bulle s’affiche quand la fenêtre de propriétaire de l’outil est active, mais pas quand elle est inactive.

La plupart des applications contiennent des barres d’outils qui correspondent à des commandes de menu. Pour ces outils, il est pratique que le contrôle d’info-bulle affiche le même texte que l’élément de menu correspondant. Le système supprime automatiquement l’esperluette (&) caractères accélérateur de toutes les chaînes passées à un contrôle info-bulle, sauf si le contrôle a le style TTS_NOPREFIX.

## <a name="see-also"></a>Voir aussi

[Utilisation de CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

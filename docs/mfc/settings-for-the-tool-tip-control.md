---
description: En savoir plus sur les paramètres du contrôle d’info-bulle
title: Paramètres du contrôle d’info-bulle
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], activating
- CToolTipCtrl class [MFC], settings
ms.assetid: ff8c5c46-2047-403a-bd98-ffec3d21ee3a
ms.openlocfilehash: 789f33a7e8e960f52589588bcda49a12889fa0d7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217027"
---
# <a name="settings-for-the-tool-tip-control"></a>Paramètres du contrôle d’info-bulle

Vous pouvez définir le contrôle d’info-bulle ([CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)) de sorte qu’il soit actif ou inactif. Quand vous le définissez comme étant actif, le contrôle d’info-bulle s’affiche quand le curseur se trouve sur un outil. Quand vous le définissez comme étant inactif, le contrôle d’info-bulle ne s’affiche pas, même si le curseur se trouve sur un outil. Appelez [Activate](../mfc/reference/ctooltipctrl-class.md#activate) pour activer ou désactiver un contrôle d’info-bulle.

Vous pouvez définir une info-bulle active pour qu’elle s’affiche quand le curseur se trouve sur un outil, que la fenêtre propriétaire du contrôle d’info-bulle soit active ou inactive, en utilisant le style TTS_ALWAYSTIP. Si vous n’utilisez pas ce style, le contrôle d’info-bulle s’affiche quand la fenêtre de propriétaire de l’outil est active, mais pas quand elle est inactive.

La plupart des applications contiennent des barres d’outils qui correspondent à des commandes de menu. Pour ces outils, il est pratique que le contrôle d’info-bulle affiche le même texte que l’élément de menu correspondant. Le système supprime automatiquement les caractères de raccourci « & » (esperluette) de toutes les chaînes passées à un contrôle d’info-bulle, sauf si le contrôle a le style TTS_NOPREFIX.

## <a name="see-also"></a>Voir aussi

[Utilisation de CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

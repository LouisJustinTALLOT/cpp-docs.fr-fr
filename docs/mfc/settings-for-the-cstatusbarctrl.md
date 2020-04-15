---
title: Paramètres de l'objet CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- status bar controls [MFC], settings
- CStatusBarCtrl class [MFC], settings
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
ms.openlocfilehash: dd7c68d6721c48f751c04437e43c8770f6ec5736
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365377"
---
# <a name="settings-for-the-cstatusbarctrl"></a>Paramètres de l'objet CStatusBarCtrl

La position par défaut d’une fenêtre d’état [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) se trouve le long du bas de la fenêtre parente, mais vous pouvez spécifier le style CCS_TOP pour qu’il apparaisse en haut de la zone client de la fenêtre mère.

Vous pouvez spécifier le style SBARS_SIZEGRIP pour inclure une `CStatusBarCtrl` poignée de dimensionnement à l’extrémité droite de la fenêtre d’état. Une poignée de dimensionnement est semblable à une bordure de dimensionnement; il s’agit d’une zone rectangulaire que l’utilisateur peut cliquer et faire glisser pour resize la fenêtre parente.

> [!NOTE]
> Si vous combinez les styles CCS_TOP et SBARS_SIZEGRIP, l’adhérence de dimensionnement qui en résulte n’est pas fonctionnelle même si le système l’attire dans la fenêtre d’état.

La procédure de fenêtre de la fenêtre d’état fixe automatiquement la taille et la position initiales de la fenêtre de commande. La largeur est la même que celle de la zone cliente de la fenêtre mère. La hauteur est basée sur les mesures de la police qui est actuellement sélectionnée dans le contexte de l’appareil de la fenêtre d’état et sur la largeur des bordures de la fenêtre.

La procédure de fenêtre ajuste automatiquement la taille de la fenêtre d’état chaque fois qu’elle reçoit un message WM_SIZE. Typiquement, lorsque la taille de la fenêtre parente change, le parent envoie un message WM_SIZE à la fenêtre d’état.

Vous pouvez définir la hauteur minimale de la zone de dessin d’une fenêtre de statut en appelant [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight), en spécifiant la hauteur minimale en pixels. La zone de dessin n’inclut pas les bordures de la fenêtre.

Vous récupérez les largeurs des bordures d’une fenêtre de statut en appelant [GetBorders](../mfc/reference/cstatusbarctrl-class.md#getborders). Cette fonction de membre comprend le pointeur d’un tableau à trois éléments qui reçoit la largeur de la bordure horizontale, la bordure verticale et la bordure entre les rectangles.

## <a name="see-also"></a>Voir aussi

[Utilisation de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

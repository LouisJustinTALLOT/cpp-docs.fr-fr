---
title: Paramètres de l'objet CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- status bar controls [MFC], settings
- CStatusBarCtrl class [MFC], settings
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
ms.openlocfilehash: 18c4c780ecf7865d8d648bfa4c54961bbffe7b18
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446385"
---
# <a name="settings-for-the-cstatusbarctrl"></a>Paramètres de l'objet CStatusBarCtrl

La position par défaut d’une fenêtre d’état [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) se trouve dans la partie inférieure de la fenêtre parente, mais vous pouvez spécifier le style de CCS_TOP pour qu’il apparaisse en haut de la zone cliente de la fenêtre parente.

Vous pouvez spécifier le style de SBARS_SIZEGRIP pour inclure une poignée de dimensionnement à l’extrémité droite de la fenêtre d’État `CStatusBarCtrl`. Une poignée de dimensionnement est semblable à une bordure de redimensionnement ; Il s’agit d’une zone rectangulaire sur laquelle l’utilisateur peut cliquer et faire glisser pour redimensionner la fenêtre parente.

> [!NOTE]
>  Si vous combinez les styles CCS_TOP et SBARS_SIZEGRIP, la poignée de dimensionnement résultante n’est pas fonctionnelle même si le système la trace dans la fenêtre d’État.

La procédure de fenêtre pour la fenêtre d’État définit automatiquement la taille initiale et la position de la fenêtre de contrôle. La largeur est la même que celle de la zone cliente de la fenêtre parente. La hauteur est basée sur les métriques de la police actuellement sélectionnée dans le contexte de périphérique de la fenêtre d’État et sur la largeur des bordures de la fenêtre.

La procédure de fenêtre ajuste automatiquement la taille de la fenêtre d’état chaque fois qu’elle reçoit un message de WM_SIZE. En général, lorsque la taille de la fenêtre parente change, le parent envoie un message WM_SIZE à la fenêtre d’État.

Vous pouvez définir la hauteur minimale de la zone de dessin d’une fenêtre d’État en appelant [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight), en spécifiant la hauteur minimale en pixels. La zone de dessin n’inclut pas les bordures de la fenêtre.

Vous récupérez les largeurs des bordures d’une fenêtre d’État en appelant [GetBorders](../mfc/reference/cstatusbarctrl-class.md#getborders). Cette fonction membre comprend le pointeur vers un tableau à trois éléments qui reçoit la largeur de la bordure horizontale, la bordure verticale et la bordure entre les rectangles.

## <a name="see-also"></a>Voir aussi

[Utilisation de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

---
title: Paramètres de l'objet CStatusBarCtrl
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
helpviewer_keywords:
- status bar controls [MFC], settings
- CStatusBarCtrl class [MFC], settings
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
ms.openlocfilehash: b41997fb9342a651260bc2196d212016dc0deb7e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285176"
---
# <a name="settings-for-the-cstatusbarctrl"></a>Paramètres de l'objet CStatusBarCtrl

La position par défaut d’un [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) fenêtre d’état est dans la partie inférieure de la fenêtre parente, mais vous pouvez spécifier le style CCS_TOP pour qu’elle s’affiche en haut de la zone cliente de la fenêtre parente.

Vous pouvez spécifier le style SBARS_SIZEGRIP pour inclure une poignée de redimensionnement à l’extrémité droite de la `CStatusBarCtrl` fenêtre d’état. Une poignée de redimensionnement est similaire à une bordure de dimensionnement ; Il est une zone rectangulaire que l’utilisateur peut cliquer et faites-la glisser pour redimensionner la fenêtre parente.

> [!NOTE]
>  Si vous combinez les styles CCS_TOP et SBARS_SIZEGRIP, la poignée de redimensionnement qui en résulte ne fonctionne pas même si le système dessine dans la fenêtre d’état.

La procédure de fenêtre pour la fenêtre d’état définit automatiquement la taille initiale et la position de la fenêtre de contrôle. La largeur est la même que celle de la zone cliente de la fenêtre parent. La hauteur est basée sur les mesures de la police actuellement sélectionnée dans le contexte de périphérique de la fenêtre d’état et de la largeur des bordures de la fenêtre.

La procédure de fenêtre ajuste automatiquement la taille de la fenêtre d’état quand elle reçoit un message WM_SIZE. En règle générale, lorsque la taille de la fenêtre parente change, le parent envoie un message WM_SIZE à la fenêtre d’état.

Vous pouvez définir la hauteur minimale de la zone de dessin d’une fenêtre d’état en appelant [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight), en spécifiant la hauteur minimale en pixels. La zone de dessin n’inclut pas les bordures de la fenêtre.

Vous récupérez les largeurs des bordures d’une fenêtre d’état en appelant [GetBorders](../mfc/reference/cstatusbarctrl-class.md#getborders). Cette fonction membre inclut le pointeur vers un tableau de trois éléments qui reçoit la largeur de la bordure horizontale, la bordure verticale et la bordure entre les rectangles.

## <a name="see-also"></a>Voir aussi

[Utilisation de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

---
title: Styles de bouton toupie
ms.date: 11/04/2016
helpviewer_keywords:
- styles [MFC], CSpinButtonCtrl
- CSpinButtonCtrl class [MFC], styles
- styles [MFC], spin button control
- spin button control, styles
ms.assetid: fb4a7f6f-9182-47be-bccf-0728fdc5332f
ms.openlocfilehash: d955ba1d76ee4d5648613ddaf6c5f6a652f3d3af
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307170"
---
# <a name="spin-button-styles"></a>Styles de bouton toupie

Nombre des paramètres pour un bouton toupie (spin) ([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)) sont contrôlées par les styles. Vous pouvez définir les styles suivants à l’aide de la **propriétés** fenêtre dans l’éditeur de boîtes de dialogue.

- **Orientation** verticale ou horizontale. Contrôle l’orientation des boutons fléchés. Associé au style UDS_HORZ.

- **Alignement** non attachés, gauche ou droite. Contrôle l’emplacement du bouton toupie (spin). Left et Right positionnent le bouton de sélection numérique en regard de la fenêtre associée. La largeur de la fenêtre associée est diminuée en fonction du bouton spin. Associé avec les styles UDS_ALIGNLEFT et UDS_ALIGNRIGHT.

- **Auto Buddy** sélectionne automatiquement la fenêtre précédente dans l’ordre de plan comme fenêtre associée au bouton toupie (spin). Dans un modèle de boîte de dialogue, il s’agit du contrôle qui précède le bouton de sélection numérique dans l’ordre de tabulation. Associé au style UDS_AUTOBUDDY.

- **Définissez Buddy Integer** provoque l’incrémentation et décrémentation de la légende de la fenêtre associée lors du changement de position actuelle du contrôle spin. Associé au style UDS_SETBUDDYINT.

- **Aucun des milliers** n’insère pas les milliers séparateur dans la valeur dans la légende de la fenêtre associée. Associé au style UDS_NOTHOUSANDS.

    > [!NOTE]
    >  Définissez ce style si vous souhaitez utiliser l’échange de données de boîtes de dialogue (DDX) pour obtenir la valeur entière du contrôle associé. `DDX_Text` n’accepte pas les séparateurs de milliers incorporés.

- **Encapsuler** provoque la position pour « encapsuler » que la valeur est incrémenté ou décrémenté au-delà de la plage du contrôle. Associé au style UDS_WRAP.

- **Touches de direction** provoque le bouton de sélection numérique incrémenter ou décrémenter la position lorsque les touches de direction haut et bas sont utilisées. Associé au style UDS_ARROWKEYS.

## <a name="see-also"></a>Voir aussi

[Utilisation de CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

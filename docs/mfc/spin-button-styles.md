---
title: Styles de bouton toupie
ms.date: 09/09/2019
helpviewer_keywords:
- styles [MFC], CSpinButtonCtrl
- CSpinButtonCtrl class [MFC], styles
- styles [MFC], spin button control
- spin button control, styles
ms.assetid: fb4a7f6f-9182-47be-bccf-0728fdc5332f
ms.openlocfilehash: 1aae4b7e4c63929ebe03c97d50f05754bc13ec26
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907855"
---
# <a name="spin-button-styles"></a>Styles de bouton toupie

La plupart des paramètres d’un bouton toupie ([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)) sont contrôlés par des styles. Vous pouvez définir les styles suivants à l’aide de l' [Assistant classe](reference/mfc-class-wizard.md).

- **Orientation** Vertical ou horizontal. Contrôle l’orientation des boutons fléchés. Associé au style UDS_HORZ.

- **Alignement** Un de non attaché, gauche ou droit. Contrôle l’emplacement du bouton toupie. Placez le bouton toupie à côté de la fenêtre associée à gauche et à droite. La largeur de la fenêtre associée est réduite pour accueillir le bouton toupie. Associé aux styles UDS_ALIGNLEFT et UDS_ALIGNRIGHT.

- **Auto Buddy** Sélectionne automatiquement la fenêtre précédente dans l’ordre de plan en tant que fenêtre associée au bouton toupie. Dans un modèle de boîte de dialogue, il s’agit du contrôle qui précède le bouton toupie dans l’ordre de tabulation. Associé au style UDS_AUTOBUDDY.

- **Définir un entier associé** Fait en sorte que le contrôle spin incrémente et décrémente la légende de la fenêtre associée lorsque la position actuelle change. Associé au style UDS_SETBUDDYINT.

- **Aucune milliers** N’insère pas le séparateur des milliers dans la valeur de la légende de la fenêtre associée. Associé au style UDS_NOTHOUSANDS.

    > [!NOTE]
    >  Définissez ce style si vous souhaitez utiliser l’échange de données de boîtes de dialogue (DDX) pour obtenir la valeur entière du contrôle associé. `DDX_Text`n’accepte pas les séparateurs de milliers incorporés.

- **Retour à la ligne** Provoque le « retour à la ligne » de la position, car la valeur est incrémentée ou décrémentée au-delà de la plage du contrôle. Associé au style UDS_WRAP.

- **Touches de direction** Fait en sorte que la touche toupie incrémente ou décrémente la position lorsque vous appuyez sur les touches haut et bas. Associé au style UDS_ARROWKEYS.

## <a name="see-also"></a>Voir aussi

[Utilisation de CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

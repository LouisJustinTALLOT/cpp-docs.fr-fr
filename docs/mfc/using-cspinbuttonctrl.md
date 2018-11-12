---
title: Utilisation de CSpinButtonCtrl
ms.date: 11/04/2016
f1_keywords:
- CSpinButtonCtrl
helpviewer_keywords:
- up-down controls [MFC], spin button control
- up-down controls
- spin button control
- CSpinButtonCtrl class [MFC], using
ms.assetid: a91db36b-e11e-42ef-8e89-51915cc486d2
ms.openlocfilehash: d3fe77c4d6d6b7bbea6e2b5f28954df4eec454d0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545871"
---
# <a name="using-cspinbuttonctrl"></a>Utilisation de CSpinButtonCtrl

Le *toupie* contrôle (également appelé un *haut-bas* contrôle) fournit une paire de flèches sur lesquelles un utilisateur peut cliquer pour ajuster une valeur. Cette valeur est appelée le *position actuelle*. La position reste dans la plage du bouton Spin. Lorsque l'utilisateur clique sur la flèche vers le haut, la position se déplace vers le maximum ; et lorsque l'utilisateur clique sur la flèche vers le bas, la position se déplace vers le minimum.

Le contrôle de bouton toupie (spin) est représenté dans MFC par la [CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md) classe.

> [!NOTE]
>  Par défaut, la plage du bouton Spin a la valeur maximale définie sur zéro (0) et la valeur minimale définie sur 100. Étant donné que la valeur maximale est inférieure à la valeur minimale, cliquez sur la flèche vers le haut pour diminuer la position et cliquez sur la flèche vers le bas pour l'augmenter. Utilisez [CSpinButtonCtrl::SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) pour ajuster ces valeurs.

En général, la position actuelle est affichée dans un contrôle compagnon. Le contrôle Compagnon est appelé le *fenêtre associée*. Pour obtenir une illustration d’un contrôle de bouton toupie (spin), consultez [sur les contrôles Up-Down](/windows/desktop/Controls/up-down-controls) dans le SDK Windows.

Pour créer un contrôle Spin et une fenêtre associée du contrôle Edit, dans Visual Studio, faites glisser au préalable un contrôle Edit vers la boîte de dialogue ou la fenêtre, puis faites glisser à son tour un contrôle Spin. Sélectionnez le contrôle spin et définissez son **Auto Buddy** et **Set Buddy Integer** propriétés à **True**. Définissez également la **alignement** propriété ; **Aligner à droite** est plus courant. Avec ces paramètres, le contrôle Edit est défini comme fenêtre associée car elle précède directement le contrôle Edit dans l'ordre de tabulation. Le contrôle Edit affiche des entiers et le contrôle Spin est incorporé dans la partie droite du contrôle Edit. Si vous le souhaitez, vous pouvez définir la plage valide du contrôle spin à l’aide de la [CSpinButtonCtrl::SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) (méthode). Aucun gestionnaire d'événements n'est requis pour la communication entre le contrôle Spin et la fenêtre associée car ils échangent des données directement. Si vous utilisez un contrôle spin à d’autres fins, par exemple, pour parcourir une séquence de fenêtres ou boîtes de dialogue, puis ajoutez un gestionnaire pour le message UDN_DELTAPOS et exécutez votre action personnalisée il.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Bouton toupie, styles](../mfc/spin-button-styles.md)

- [Bouton toupie, fonctions membres](../mfc/spin-button-member-functions.md)

## <a name="see-also"></a>Voir aussi

[Contrôles](../mfc/controls-mfc.md)


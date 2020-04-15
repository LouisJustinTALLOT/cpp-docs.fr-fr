---
title: Utilisation de CSpinButtonCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- up-down controls [MFC], spin button control
- up-down controls
- spin button control
- CSpinButtonCtrl class [MFC], using
ms.assetid: a91db36b-e11e-42ef-8e89-51915cc486d2
ms.openlocfilehash: 6f72601d3813f36e4a99b9ab04f2e9383c58df94
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366483"
---
# <a name="using-cspinbuttonctrl"></a>Utilisation de CSpinButtonCtrl

Le contrôle *du bouton de rotation* (également connu sous le nom de contrôle vers le *bas)* fournit une paire de flèches qu’un utilisateur peut cliquer pour ajuster une valeur. Cette valeur est connue comme la *position actuelle*. La position reste dans la plage du bouton Spin. Lorsque l'utilisateur clique sur la flèche vers le haut, la position se déplace vers le maximum ; et lorsque l'utilisateur clique sur la flèche vers le bas, la position se déplace vers le minimum.

Le contrôle du bouton de rotation est représenté dans MFC par la classe [CSpinButtonCtrl.](../mfc/reference/cspinbuttonctrl-class.md)

> [!NOTE]
> Par défaut, la plage du bouton Spin a la valeur maximale définie sur zéro (0) et la valeur minimale définie sur 100. Étant donné que la valeur maximale est inférieure à la valeur minimale, cliquez sur la flèche vers le haut pour diminuer la position et cliquez sur la flèche vers le bas pour l'augmenter. Utilisez [CSpinButtonCtrl::SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) pour ajuster ces valeurs.

En général, la position actuelle est affichée dans un contrôle compagnon. Le contrôle compagnon est connu comme la *fenêtre de copain*. Pour une illustration d’un contrôle de bouton de spin, voir [About Up-Down Controls](/windows/win32/Controls/up-down-controls) in the Windows SDK.

Pour créer un contrôle Spin et une fenêtre associée du contrôle Edit, dans Visual Studio, faites glisser au préalable un contrôle Edit vers la boîte de dialogue ou la fenêtre, puis faites glisser à son tour un contrôle Spin. Sélectionnez le contrôle de spin et définissez ses propriétés **Auto Buddy** et **Set Buddy Integer** à **True**. Réglez également la propriété **d’alignement** ; **Align droit** est le plus typique. Avec ces paramètres, le contrôle Edit est défini comme fenêtre associée car elle précède directement le contrôle Edit dans l'ordre de tabulation. Le contrôle Edit affiche des entiers et le contrôle Spin est incorporé dans la partie droite du contrôle Edit. En option, vous pouvez définir la plage valide du contrôle de spin en utilisant la méthode [CSpinButtonCtrl::SetRange.](../mfc/reference/cspinbuttonctrl-class.md#setrange) Aucun gestionnaire d'événements n'est requis pour la communication entre le contrôle Spin et la fenêtre associée car ils échangent des données directement. Si vous utilisez un contrôle de spin pour un autre but, par exemple, pour feuillet à travers une séquence de fenêtres ou de boîtes de dialogue, puis ajouter un gestionnaire pour le message UDN_DELTAPOS et effectuer votre action personnalisée là-bas.

## <a name="what-do-you-want-to-know-more-about"></a>Qu’est-ce que vous voulez savoir plus sur

- [Bouton toupie, styles](../mfc/spin-button-styles.md)

- [Bouton toupie, fonctions membres](../mfc/spin-button-member-functions.md)

## <a name="see-also"></a>Voir aussi

[Contrôles](../mfc/controls-mfc.md)

---
description: 'En savoir plus sur les éléments suivants : à l’aide de CSpinButtonCtrl'
title: Utilisation de CSpinButtonCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- up-down controls [MFC], spin button control
- up-down controls
- spin button control
- CSpinButtonCtrl class [MFC], using
ms.assetid: a91db36b-e11e-42ef-8e89-51915cc486d2
ms.openlocfilehash: ef596c4f194eb60fc8548231293d4570456d2f54
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271588"
---
# <a name="using-cspinbuttonctrl"></a>Utilisation de CSpinButtonCtrl

Le contrôle *spin Button* (également appelé contrôle *Up-Down* ) fournit une paire de flèches sur lesquelles un utilisateur peut cliquer pour ajuster une valeur. Cette valeur est appelée *position actuelle*. La position reste dans la plage du bouton Spin. Lorsque l'utilisateur clique sur la flèche vers le haut, la position se déplace vers le maximum ; et lorsque l'utilisateur clique sur la flèche vers le bas, la position se déplace vers le minimum.

Le contrôle spin Button est représenté dans MFC par la classe [CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md) .

> [!NOTE]
> Par défaut, la plage du bouton Spin a la valeur maximale définie sur zéro (0) et la valeur minimale définie sur 100. Étant donné que la valeur maximale est inférieure à la valeur minimale, cliquez sur la flèche vers le haut pour diminuer la position et cliquez sur la flèche vers le bas pour l'augmenter. Utilisez [CSpinButtonCtrl :: SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) pour ajuster ces valeurs.

En général, la position actuelle est affichée dans un contrôle compagnon. Le contrôle compagnon est connu sous le nom de *fenêtre associée*. Pour obtenir une illustration d’un contrôle de bouton toupie, consultez [à propos des contrôles de Up-Down](/windows/win32/Controls/up-down-controls) dans le SDK Windows.

Pour créer un contrôle Spin et une fenêtre associée du contrôle Edit, dans Visual Studio, faites glisser au préalable un contrôle Edit vers la boîte de dialogue ou la fenêtre, puis faites glisser à son tour un contrôle Spin. Sélectionnez le contrôle spin et définissez ses propriétés **auto Buddy** et **Set Buddy Integer** sur **true**. Définissez également la propriété d' **alignement** . **Aligner à droite est le** plus courant. Avec ces paramètres, le contrôle Edit est défini comme fenêtre associée car elle précède directement le contrôle Edit dans l'ordre de tabulation. Le contrôle Edit affiche des entiers et le contrôle Spin est incorporé dans la partie droite du contrôle Edit. Si vous le souhaitez, vous pouvez définir la plage valide du contrôle spin à l’aide de la méthode [CSpinButtonCtrl :: SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) . Aucun gestionnaire d'événements n'est requis pour la communication entre le contrôle Spin et la fenêtre associée car ils échangent des données directement. Si vous utilisez un contrôle spin à d’autres fins, par exemple, pour parcourir une séquence de fenêtres ou de boîtes de dialogue, ajoutez un gestionnaire pour le UDN_DELTAPOS message et effectuez votre action personnalisée ici.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Styles de bouton toupie](../mfc/spin-button-styles.md)

- [Bouton toupie, fonctions membres](../mfc/spin-button-member-functions.md)

## <a name="see-also"></a>Voir aussi

[Contrôles](../mfc/controls-mfc.md)

---
title: Utilisation de CSpinButtonCtrl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CSpinButtonCtrl
dev_langs:
- C++
helpviewer_keywords:
- up-down controls [MFC], spin button control
- up-down controls
- spin button control
- CSpinButtonCtrl class [MFC], using
ms.assetid: a91db36b-e11e-42ef-8e89-51915cc486d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 03b1e83977c1d75070e8878dfdcc53c7afca7a86
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384398"
---
# <a name="using-cspinbuttonctrl"></a>Utilisation de CSpinButtonCtrl
Le *toupie* contrôle (également appelé un *déroulant* contrôle) fournit une paire de flèches sur lesquelles un utilisateur peut cliquer pour ajuster une valeur. Cette valeur est appelée la *position actuelle*. La position reste dans la plage du bouton Spin. Lorsque l'utilisateur clique sur la flèche vers le haut, la position se déplace vers le maximum ; et lorsque l'utilisateur clique sur la flèche vers le bas, la position se déplace vers le minimum.  
  
 Le contrôle spin est représenté dans MFC par la [CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md) classe.  
  
> [!NOTE]
>  Par défaut, la plage du bouton Spin a la valeur maximale définie sur zéro (0) et la valeur minimale définie sur 100. Étant donné que la valeur maximale est inférieure à la valeur minimale, cliquez sur la flèche vers le haut pour diminuer la position et cliquez sur la flèche vers le bas pour l'augmenter. Utilisez [CSpinButtonCtrl::SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) pour ajuster ces valeurs.  
  
 En général, la position actuelle est affichée dans un contrôle compagnon. Le contrôle Compagnon est appelé le *fenêtre associée*. Pour obtenir une illustration d’un contrôle de bouton toupie (spin), consultez [sur les contrôles Up-Down](http://msdn.microsoft.com/library/windows/desktop/bb759889) dans le Kit de développement logiciel Windows.  
  
 Pour créer un contrôle Spin et une fenêtre associée du contrôle Edit, dans Visual Studio, faites glisser au préalable un contrôle Edit vers la boîte de dialogue ou la fenêtre, puis faites glisser à son tour un contrôle Spin. Sélectionnez le contrôle spin et définissez son **Auto Buddy** et **Set Buddy Integer** propriétés **True**. Définissez également la **alignement** propriété ; **Aligner à droite** est plus courant. Avec ces paramètres, le contrôle Edit est défini comme fenêtre associée car elle précède directement le contrôle Edit dans l'ordre de tabulation. Le contrôle Edit affiche des entiers et le contrôle Spin est incorporé dans la partie droite du contrôle Edit. Si vous le souhaitez, vous pouvez définir la plage valide du contrôle spin à l’aide de la [CSpinButtonCtrl::SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) (méthode). Aucun gestionnaire d'événements n'est requis pour la communication entre le contrôle Spin et la fenêtre associée car ils échangent des données directement. Si vous utilisez un contrôle Spin à d'autres fins, par exemple, pour effectuer une pagination dans une séquence de fenêtres ou de boîtes de dialogue, ajoutez un gestionnaire pour le message `UDN_DELTAPOS` et exécutez votre action personnalisée à cet endroit.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Bouton toupie, styles](../mfc/spin-button-styles.md)  
  
-   [Bouton toupie, fonctions membres](../mfc/spin-button-member-functions.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles](../mfc/controls-mfc.md)


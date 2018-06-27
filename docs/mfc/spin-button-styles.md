---
title: Styles de bouton toupie | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- styles [MFC], CSpinButtonCtrl
- CSpinButtonCtrl class [MFC], styles
- styles [MFC], spin button control
- spin button control, styles
ms.assetid: fb4a7f6f-9182-47be-bccf-0728fdc5332f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 223b7e0875a5382edf5f4d350c9343d117768c41
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953776"
---
# <a name="spin-button-styles"></a>Styles de bouton toupie
Nombre des paramètres pour un bouton de sélection numérique ([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)) sont contrôlées par les styles. Vous pouvez définir les styles suivants à l’aide de la **propriétés** fenêtre dans l’éditeur de boîte de dialogue.  
  
-   **Orientation** verticale ou horizontale. Contrôle l’orientation des flèches. Associé au style UDS_HORZ.  
  
-   **Alignement** détachés, gauche ou droite. Contrôle l’emplacement du bouton de sélection numérique. Droite et gauche placent le bouton de sélection numérique en regard de la fenêtre associée. La largeur de la fenêtre associée est diminuée en fonction de la toupie. Associé avec les styles UDS_ALIGNLEFT et UDS_ALIGNRIGHT.  
  
-   **Auto Buddy** sélectionne automatiquement la fenêtre précédente dans l’ordre de plan comme fenêtre associée au bouton toupie (spin). Dans un modèle de boîte de dialogue, il s’agit du contrôle qui précède la toupie dans l’ordre de tabulation. Associé au style UDS_AUTOBUDDY.  
  
-   **Définir Buddy Integer** provoque le contrôle de sélection numérique incrémenter et décrémenter la légende de la fenêtre associée lors du changement de position actuelle. Associé au style UDS_SETBUDDYINT.  
  
-   **Aucun des milliers** n’insère pas de milliers séparateur dans la valeur de la légende de la fenêtre associée. Associé au style UDS_NOTHOUSANDS.  
  
    > [!NOTE]
    >  Définissez ce style si vous souhaitez utiliser l’échange de données de boîtes de dialogue (DDX) pour obtenir la valeur entière du contrôle associé. `DDX_Text` n’accepte pas les séparateurs de milliers incorporés.  
  
-   **Retour à la ligne** entraîne à la « ligne », car la valeur est incrémenté ou décrémenté au-delà de la plage du contrôle. Associé au style UDS_WRAP.  
  
-   **Touches de direction** le bouton de sélection numérique incrémenter ou décrémenter la position lorsque les touches de direction haut et bas sont utilisées. Associé au style UDS_ARROWKEYS.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)


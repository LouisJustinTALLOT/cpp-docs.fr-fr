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
ms.openlocfilehash: 96b559fcda4825aec71ba4b5c1dd8c3cd319b83d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33380095"
---
# <a name="spin-button-styles"></a>Styles de bouton toupie
Nombre des paramètres pour un bouton de sélection numérique ([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)) sont contrôlées par les styles. Vous pouvez définir les styles suivants à l’aide de la **propriétés** fenêtre dans l’éditeur de boîte de dialogue.  
  
-   **Orientation** verticale ou horizontale. Contrôle l’orientation des flèches. Associé à la `UDS_HORZ` style.  
  
-   **Alignement** détachés, gauche ou droite. Contrôle l’emplacement du bouton de sélection numérique. Droite et gauche placent le bouton de sélection numérique en regard de la fenêtre associée. La largeur de la fenêtre associée est diminuée en fonction de la toupie. Associé à la `UDS_ALIGNLEFT` et `UDS_ALIGNRIGHT` styles.  
  
-   **Auto Buddy** sélectionne automatiquement la fenêtre précédente dans l’ordre de plan comme fenêtre associée au bouton toupie (spin). Dans un modèle de boîte de dialogue, il s’agit du contrôle qui précède la toupie dans l’ordre de tabulation. Associé à la `UDS_AUTOBUDDY` style.  
  
-   **Définir Buddy Integer** provoque le contrôle de sélection numérique incrémenter et décrémenter la légende de la fenêtre associée lors du changement de position actuelle. Associé à la `UDS_SETBUDDYINT` style.  
  
-   **Aucun des milliers** n’insère pas de milliers séparateur dans la valeur de la légende de la fenêtre associée. Associé à la `UDS_NOTHOUSANDS` style.  
  
    > [!NOTE]
    >  Définissez ce style si vous souhaitez utiliser l’échange de données de boîtes de dialogue (DDX) pour obtenir la valeur entière du contrôle associé. `DDX_Text` n’accepte pas les séparateurs de milliers incorporés.  
  
-   **Retour à la ligne** entraîne à la « ligne », car la valeur est incrémenté ou décrémenté au-delà de la plage du contrôle. Associé à la `UDS_WRAP` style.  
  
-   **Touches de direction** le bouton de sélection numérique incrémenter ou décrémenter la position lorsque les touches de direction haut et bas sont utilisées. Associé à la `UDS_ARROWKEYS` style.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)


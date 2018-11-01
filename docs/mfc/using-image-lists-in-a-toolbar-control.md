---
title: Utilisation de listes d'images dans un contrôle ToolBar
ms.date: 11/04/2016
helpviewer_keywords:
- toolbar controls [MFC], image
- image lists [MFC], toolbar controls
- CToolBarCtrl class [MFC], image lists
ms.assetid: ccbe8df4-4ed9-4b54-bb93-9a1dcb3b97eb
ms.openlocfilehash: f8b19cd54a6fb2dca940c354ef23e7d06b35f0b3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584572"
---
# <a name="using-image-lists-in-a-toolbar-control"></a>Utilisation de listes d'images dans un contrôle ToolBar

Par défaut, les images utilisées par les boutons dans un contrôle de barre d’outils sont stockés en tant qu’une seule bitmap. Toutefois, vous pouvez également stocker des images de bouton dans un ensemble de listes d’images. L’objet de contrôle de barre d’outils peut utiliser jusqu'à trois listes d’images distincts :

- Activé image liste contient des images pour les boutons de barre d’outils qui sont actuellement activées.

- Désactivé image liste contient des images pour les boutons de barre d’outils qui sont actuellement désactivées.

- Mise en surbrillance image liste contient des images pour les boutons de barre d’outils qui sont actuellement mis en surbrillance. Cette liste d’images est utilisée uniquement lorsque la barre d’outils utilise le style TBSTYLE_FLAT.

Ces listes d’images sont utilisées par le contrôle de barre d’outils lorsque vous les associez avec le `CToolBarCtrl` objet. Cette association est obtenue en effectuant des appels à [CToolBarCtrl::SetImageList](../mfc/reference/ctoolbarctrl-class.md#setimagelist), [SetDisabledImageList](../mfc/reference/ctoolbarctrl-class.md#setdisabledimagelist), et [SetHotImageList](../mfc/reference/ctoolbarctrl-class.md#sethotimagelist).

Par défaut, MFC utilise le `CToolBar` classe pour implémenter des barres d’outils des applications MFC. Toutefois, le `GetToolBarCtrl` fonction membre peut être utilisée pour récupérer le texte incorporé `CToolBarCtrl` objet. Vous pouvez ensuite effectuer des appels à `CToolBarCtrl` les fonctions de membre à l’aide de l’objet retourné.

L’exemple suivant illustre cette technique en assignant une est activée (`m_ToolBarImages`) et il est désactivé (`m_ToolBarDisabledImages`) liste d’images à un `CToolBarCtrl` objet (`m_ToolBarCtrl`).

[!code-cpp[NVC_MFCControlLadenDialog#35](../mfc/codesnippet/cpp/using-image-lists-in-a-toolbar-control_1.cpp)]

> [!NOTE]
>  Listes d’images utilisées par l’objet de barre d’outils doivent être des objets permanents. Pour cette raison, ils sont généralement des membres de données d’une classe MFC ; Dans cet exemple, la classe de fenêtre frame principale.

Une fois que les listes d’images sont associées les `CToolBarCtrl` de l’objet, l’infrastructure affiche automatiquement l’image du bouton approprié.

## <a name="see-also"></a>Voir aussi

[Utilisation de CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)


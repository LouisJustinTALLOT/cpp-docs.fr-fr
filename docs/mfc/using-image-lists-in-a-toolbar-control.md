---
title: Utilisation de listes d'images dans un contrôle ToolBar
ms.date: 11/04/2016
helpviewer_keywords:
- toolbar controls [MFC], image
- image lists [MFC], toolbar controls
- CToolBarCtrl class [MFC], image lists
ms.assetid: ccbe8df4-4ed9-4b54-bb93-9a1dcb3b97eb
ms.openlocfilehash: 81468528c15300a7e9ace6b20fd9fb34818f1928
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366498"
---
# <a name="using-image-lists-in-a-toolbar-control"></a>Utilisation de listes d'images dans un contrôle ToolBar

Par défaut, les images utilisées par les boutons dans un contrôle de barre d’outils sont stockées sous forme d’une seule bitmap. Cependant, vous pouvez également stocker des images bouton dans un ensemble de listes d’images. L’objet de contrôle de la barre d’outils peut utiliser jusqu’à trois listes d’images distinctes :

- Liste d’images activée Contient des images pour les boutons de barre d’outils qui sont actuellement activés.

- Liste d’images désactivée Contient des images pour les boutons de barre d’outils qui sont actuellement désactivés.

- Liste d’images surlignée contient des images pour les boutons de barre d’outils qui sont actuellement mis en évidence. Cette liste d’images n’est utilisée que lorsque la barre d’outils utilise le style TBSTYLE_FLAT.

Ces listes d’images sont utilisées par le `CToolBarCtrl` contrôle de la barre d’outils lorsque vous les associez à l’objet. Cette association est accomplie en faisant des appels à [CToolBarCtrl::SetImageList](../mfc/reference/ctoolbarctrl-class.md#setimagelist), [SetDisabledImageList](../mfc/reference/ctoolbarctrl-class.md#setdisabledimagelist), et [SetHotImageList](../mfc/reference/ctoolbarctrl-class.md#sethotimagelist).

Par défaut, MFC `CToolBar` utilise la classe pour implémenter des barres d’outils d’application MFC. Cependant, `GetToolBarCtrl` la fonction membre peut être `CToolBarCtrl` utilisée pour récupérer l’objet intégré. Vous pouvez ensuite `CToolBarCtrl` passer des appels vers les fonctions des membres à l’aide de l’objet retourné.

L’exemple suivant démontre cette technique en`m_ToolBarImages`assignant`m_ToolBarDisabledImages`une liste d’images activée ( ) et désactivée ( ) à un `CToolBarCtrl` objet (`m_ToolBarCtrl`).

[!code-cpp[NVC_MFCControlLadenDialog#35](../mfc/codesnippet/cpp/using-image-lists-in-a-toolbar-control_1.cpp)]

> [!NOTE]
> Les listes d’images utilisées par l’objet de la barre d’outils doivent être des objets permanents. Pour cette raison, ils sont généralement des membres de données d’une classe MFC; dans cet exemple, la classe principale de fenêtre de cadre.

Une fois que les `CToolBarCtrl` listes d’images sont associées à l’objet, le cadre affiche automatiquement l’image bouton appropriée.

## <a name="see-also"></a>Voir aussi

[Utilisation de CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

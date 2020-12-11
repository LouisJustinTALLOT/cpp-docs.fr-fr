---
description: 'En savoir plus sur : utilisation des listes d’images dans un contrôle ToolBar'
title: Utilisation de listes d'images dans un contrôle ToolBar
ms.date: 11/04/2016
helpviewer_keywords:
- toolbar controls [MFC], image
- image lists [MFC], toolbar controls
- CToolBarCtrl class [MFC], image lists
ms.assetid: ccbe8df4-4ed9-4b54-bb93-9a1dcb3b97eb
ms.openlocfilehash: dbdac26f1d17997e14ed4ba16875ef3794e46a71
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154433"
---
# <a name="using-image-lists-in-a-toolbar-control"></a>Utilisation de listes d'images dans un contrôle ToolBar

Par défaut, les images utilisées par les boutons d’un contrôle ToolBar sont stockées sous la forme d’une image bitmap unique. Toutefois, vous pouvez également stocker des images de bouton dans un ensemble de listes d’images. L’objet de contrôle ToolBar peut utiliser jusqu’à trois listes d’images distinctes :

- La liste d’images activée contient des images pour les boutons de barre d’outils actuellement activés.

- Liste d’images désactivées contient des images pour les boutons de barre d’outils qui sont actuellement désactivés.

- La liste d’images en surbrillance contient des images pour les boutons de barre d’outils actuellement en surbrillance. Cette liste d’images est utilisée uniquement lorsque la barre d’outils utilise le style TBSTYLE_FLAT.

Ces listes d’images sont utilisées par le contrôle ToolBar lorsque vous les associez à l' `CToolBarCtrl` objet. Cette association s’effectue en effectuant des appels à [CToolBarCtrl :: SetImageList](../mfc/reference/ctoolbarctrl-class.md#setimagelist), [SetDisabledImageList](../mfc/reference/ctoolbarctrl-class.md#setdisabledimagelist)et [SetHotImageList](../mfc/reference/ctoolbarctrl-class.md#sethotimagelist).

Par défaut, MFC utilise la `CToolBar` classe pour implémenter des barres d’outils d’application MFC. Toutefois, la `GetToolBarCtrl` fonction membre peut être utilisée pour récupérer l’objet incorporé `CToolBarCtrl` . Vous pouvez ensuite effectuer des appels aux `CToolBarCtrl` fonctions membres à l’aide de l’objet retourné.

L’exemple suivant illustre cette technique en affectant une `m_ToolBarImages` liste d’images activée () et désactivée () `m_ToolBarDisabledImages` à un `CToolBarCtrl` objet ( `m_ToolBarCtrl` ).

[!code-cpp[NVC_MFCControlLadenDialog#35](../mfc/codesnippet/cpp/using-image-lists-in-a-toolbar-control_1.cpp)]

> [!NOTE]
> Les listes d’images utilisées par l’objet Toolbar doivent être des objets permanents. C’est pour cette raison qu’il s’agit généralement de données membres d’une classe MFC. dans cet exemple, la classe de fenêtre frame principale.

Une fois que les listes d’images sont associées à l' `CToolBarCtrl` objet, le Framework affiche automatiquement l’image de bouton appropriée.

## <a name="see-also"></a>Voir aussi

[Utilisation de CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

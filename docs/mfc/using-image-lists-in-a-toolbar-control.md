---
title: À l’aide de listes d’images dans un contrôle de barre d’outils | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- toolbar controls [MFC], image
- image lists [MFC], toolbar controls
- CToolBarCtrl class [MFC], image lists
ms.assetid: ccbe8df4-4ed9-4b54-bb93-9a1dcb3b97eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 76325d2b078f51860cad7fa3fab61ed7c518a41c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382848"
---
# <a name="using-image-lists-in-a-toolbar-control"></a>Utilisation de listes d'images dans un contrôle ToolBar
Par défaut, les images utilisées par les boutons dans un contrôle de barre d’outils sont stockés sous forme de bitmap unique. Toutefois, vous pouvez également stocker des images de boutons dans un ensemble de listes d’images. L’objet de contrôle de barre d’outils peut utiliser jusqu'à trois listes d’images séparées :  
  
-   Activé image liste contient des images pour les boutons de barre d’outils qui sont actuellement activées.  
  
-   Désactivé image liste contient des images pour les boutons de barre d’outils qui sont actuellement désactivées.  
  
-   Mise en surbrillance image liste contient des images pour les boutons de barre d’outils qui sont actuellement mis en surbrillance. Cette liste d’images est uniquement utilisée lors de la barre d’outils utilise le **TBSTYLE_FLAT** style.  
  
 Ces listes d’images sont utilisées par le contrôle de barre d’outils lorsque vous les associez avec le `CToolBarCtrl` objet. Cette association s’effectue via des appels à [CToolBarCtrl::SetImageList](../mfc/reference/ctoolbarctrl-class.md#setimagelist), [SetDisabledImageList](../mfc/reference/ctoolbarctrl-class.md#setdisabledimagelist), et [SetHotImageList](../mfc/reference/ctoolbarctrl-class.md#sethotimagelist).  
  
 Par défaut, MFC utilise le `CToolBar` classe pour implémenter des barres d’outils des applications MFC. Toutefois, le `GetToolBarCtrl` fonction membre peut être utilisée pour récupérer le texte incorporé `CToolBarCtrl` objet. Vous pouvez ensuite effectuer des appels à `CToolBarCtrl` des fonctions de membre à l’aide de l’objet retourné.  
  
 L’exemple suivant illustre cette technique en assignant un activé (`m_ToolBarImages`) et désactivé (`m_ToolBarDisabledImages`) liste d’images à un `CToolBarCtrl` objet (`m_ToolBarCtrl`).  
  
 [!code-cpp[NVC_MFCControlLadenDialog#35](../mfc/codesnippet/cpp/using-image-lists-in-a-toolbar-control_1.cpp)]  
  
> [!NOTE]
>  Listes d’images utilisées par l’objet de barre d’outils doivent être des objets permanents. Pour cette raison, ils sont généralement des membres de données d’une classe MFC ; Dans cet exemple, la classe de fenêtre frame principale.  
  
 Une fois que les listes d’images sont associées les `CToolBarCtrl` de l’objet, l’infrastructure affiche automatiquement l’image du bouton approprié.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)


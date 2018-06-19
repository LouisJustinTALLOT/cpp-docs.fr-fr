---
title: Redimensionnement d’une Image (Éditeur d’images pour les icônes) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.editing
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], resizing images
- graphics [C++], resizing
- images [C++], resizing
- resizing images
ms.assetid: d83a02c4-4dfe-4586-a0df-51a50c2ba71d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c6636e1f92907c301c6e66abd63f744375bffeb8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879046"
---
# <a name="resizing-an-image-image-editor-for-icons"></a>Redimensionnement d'une image (Éditeur d'images pour les icônes)
Le comportement de l’éditeur d’images lors du redimensionnement d’une image varie selon que vous avez [sélectionné](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) l’image entière ou une partie.  
  
 Lorsque la sélection contient uniquement une partie de l’image, l’éditeur d’images réduit la sélection en supprimant les lignes ou colonnes de pixels et en remplissant les régions libérées avec la couleur d’arrière-plan en cours, ou il s’étend la sélection en dupliquant des lignes ou des colonnes de pixels.  
  
 Lorsque la sélection comprend l’intégralité de l’image, l’éditeur d’images soit réduit et s’étend de l’image, ou les cultures et les étend.  
  
 Il existe deux mécanismes pour redimensionner une image : les poignées de redimensionnement et la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Vous pouvez faire glisser les poignées de redimensionnement pour modifier la taille de tous ou une partie d’une image. Les poignées de dimensionnement que vous pouvez faire glisser sont pleines. Vous ne peut pas faire glisser les poignées qui sont vides. Vous pouvez utiliser la fenêtre de propriétés pour redimensionner l’image entière uniquement, pas une partie sélectionnée.  
  
 ![Poignées d’une image bitmap](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")  
Poignées de redimensionnement  
  
> [!NOTE]
>  Si vous avez l’option de grille mosaïque sélectionnée dans le [boîte de dialogue Paramètres de la grille](../windows/grid-settings-dialog-box-image-editor-for-icons.md), redimensionnement s’aligne sur le quadrillage suivant. Si seule la grille de pixels est de l’option sélectionnée (paramètre par défaut), redimensionnement s’aligne sur le pixel suivant.  
  
-   [Redimensionner l’intégralité d’une Image](../windows/resizing-an-entire-image-image-editor-for-icons.md)  
  
-   [Rognage ou extension de l’intégralité d’une Image](cropping-or-extending-an-entire-image-image-editor-for-icons.md)  
  
-   [Réduction ou étirement de l’intégralité d’une Image](../windows/shrinking-or-stretching-an-entire-image-image-editor-for-icons.md)  
  
-   [Réduction ou étirement d’une partie d’une Image](../windows/shrinking-or-stretching-part-of-an-image-image-editor-for-icons.md)  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Spécifications  
 Aucun  
  
## <a name="see-also"></a>Voir aussi  
 [Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Modification de ressources graphiques](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)


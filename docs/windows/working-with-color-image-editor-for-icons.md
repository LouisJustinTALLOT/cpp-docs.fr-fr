---
title: Utilisation des couleurs (Éditeur d’images pour les icônes) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.color
dev_langs:
- C++
helpviewer_keywords:
- images [C++], background colors
- Image editor [C++], Colors Palette
- colors [C++], image
- Colors Palette, Image editor
- palettes, Image editor colors
- foreground colors, Image editor
- colors [C++]
ms.assetid: d34ff96f-241d-494f-abdd-13811ada8cd3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1f9016e36ce6b081446a00136445fd7ebdd5a341
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891657"
---
# <a name="working-with-color-image-editor-for-icons"></a>Utilisation des couleurs (Éditeur d'images pour les icônes)
L’éditeur d’images contient de nombreuses fonctionnalités qui permettent de gérer et de personnaliser les couleurs. Vous pouvez définir une couleur de premier plan ou d’arrière-plan, couleur de remplissage des zones limitées ou sélectionnez une couleur dans une image à utiliser comme couleur de premier plan ou d’arrière-plan actuelle. Vous pouvez utiliser les outils de la [barre d’outils Éditeur d’images](../windows/toolbar-image-editor-for-icons.md) , ainsi que de la palette de couleurs dans les [fenêtre couleurs](../windows/colors-window-image-editor-for-icons.md) pour créer des images.  
  
 Toutes les couleurs pour les images de 16 couleurs et monochrome sont affichés dans la palette de couleurs dans la fenêtre couleurs. En plus de 16 couleurs standards, vous pouvez créer vos propres couleurs personnalisées. La modification des couleurs dans la palette, change immédiatement la couleur correspondante dans l’image.  
  
 Lorsque les images de travail avec l’icône de 256 couleurs et de curseur, la propriété de couleurs dans les [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) est utilisé. Pour plus d’informations, consultez [création d’un curseur ou une icône de 256 couleurs](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md).  
  
> [!NOTE]
>  Grâce à l'Éditeur d'images, vous pouvez afficher des images 32 bits, mais vous ne pouvez pas les modifier.  
  
 Images en couleurs vraies peuvent également être créés. Toutefois, les échantillons de couleurs n’apparaissent pas dans la palette de la fenêtre couleurs ; ils apparaissent uniquement dans la zone d’indicateur de couleur de premier plan ou en arrière-plan. Les couleurs vraies sont créées à l’aide de la [boîte de dialogue Sélecteur de couleurs personnalisées](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md). Pour plus d’informations, consultez [personnalisation ou modification des couleurs](../windows/customizing-or-changing-colors-image-editor-for-icons.md).  
  
 Vous pouvez enregistrer des palettes de couleurs personnalisées sur disque et les recharger en fonction des besoins. La palette de couleurs que vous avez utilisé le plus récemment est enregistrée dans le Registre et chargée automatiquement la prochaine fois que vous démarrez Visual Studio.  
  
-   [Sélection de couleurs d’arrière-plan ou premier plan](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)  
  
-   [Remplissage d’une zone délimitée d’une Image avec une couleur](../windows/filling-a-bounded-area-of-an-image-with-a-color-image-editor-for-icons.md)  
  
-   [Sélection d’une couleur à partir d’une Image à utiliser ailleurs](../windows/picking-up-a-color-from-an-image-to-use-elsewhere-image-editor-for-icons.md)  
  
-   [Choix d’un arrière-plan Transparent ou Opaque](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)  
  
-   [Inversion des couleurs dans une sélection](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md)  
  
-   [Personnalisation ou modification des couleurs](../windows/customizing-or-changing-colors-image-editor-for-icons.md)  
  
-   [L’enregistrement et chargement de différentes Palettes de couleurs](../windows/saving-and-loading-different-color-palettes-image-editor-for-icons.md)  
  
-   [Fenêtre couleurs](../windows/colors-window-image-editor-for-icons.md)  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Spécifications  
 Aucun  
  
## <a name="see-also"></a>Voir aussi  
 [Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)   


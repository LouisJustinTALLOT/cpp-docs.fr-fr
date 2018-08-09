---
title: À l’aide de la Palette 256 couleurs (Éditeur d’images pour les icônes) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- 256-color palette
- colors, icons and cursors
- cursors, color
- color palettes, 256-color
- palettes, 256-color
- icons, color
ms.assetid: 1506ed00-669b-4a21-b1a4-39b6a84a78bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0287d27d975ce93e88a7a4b70a683188901ca958
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011814"
---
# <a name="using-the-256-color-palette-image-editor-for-icons"></a>Utilisation de la palette 256 couleurs (Éditeur d'images pour les icônes)
Pour dessiner avec une sélection à partir de la palette 256 couleurs, vous devez sélectionner les couleurs à partir de la **couleurs** palette dans la [fenêtre couleurs](../windows/colors-window-image-editor-for-icons.md).  
  
### <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>Pour choisir une couleur de la palette 256 couleurs pour les grandes icônes  
  
1.  Sélectionnez la grande icône ou curseur, ou créez une nouvelle grande icône ou curseur.  
  
2.  Choisir une couleur parmi les 256 couleurs affichées dans le **couleurs** palette dans la **couleurs** fenêtre.  
  
     La couleur sélectionnée devient la couleur actuelle dans le **couleurs** palette dans la **couleurs** fenêtre.  
  
    > [!NOTE]
    >  La palette d’origine utilisée pour les images de 256 couleurs correspond à la palette retournée par la `CreateHalftonePalette` API de Windows. Toutes les icônes pour le shell Windows doivent utiliser cette palette pour empêcher le scintillement pendant la réalisation de la palette.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Configuration requise  
 Aucun.  
  
## <a name="see-also"></a>Voir aussi  
 [Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Création d’un curseur ou une icône de 256 couleurs](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md)   
 [Icônes et curseurs : ressources Image pour les périphériques d’affichage](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)
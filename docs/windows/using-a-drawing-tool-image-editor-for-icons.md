---
title: À l’aide d’un outil de dessin (Éditeur d’images pour les icônes) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.drawing
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], selecting drawing tools
- Image editor [C++], toolbar
- drawing tools
ms.assetid: 1f8c6eef-7760-45a9-a5cb-9e15c6f91245
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8345829e5d561ead3be0052770e022f704eabc3b
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39646122"
---
# <a name="using-a-drawing-tool-image-editor-for-icons"></a>Utilisation d'un outil de dessin (Éditeur d'images pour les icônes)
L’éditeur d’images de dessin à main levée de dessin et effacement outils fonctionnent tous de la même façon : vous sélectionnez l’outil et, si nécessaire, [sélectionner des couleurs de premier plan et arrière-plan](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md) et options de taille et la forme. Vous placez le pointeur sur l’image et cliquez sur ou faites glisser pour dessiner et effacer.  
  
 Lorsque vous sélectionnez le **gomme** outil, **pinceau** outil, ou **aérographe** outil, le sélecteur d’options affiche les options de l’outil.  
  
> [!TIP]
>  Au lieu d’utiliser le **gomme** outil, vous pouvez s’avérer plus commode de dessiner dans la couleur d’arrière-plan avec l’un des outils de dessin.  
  
 Vous pouvez sélectionner les outils de dessin à partir du **Éditeur d’images** barre d’outils ou le **Image** menu.  
  
### <a name="to-select-and-use-a-drawing-tool-from-the-image-editor-toolbar"></a>Pour sélectionner et utiliser un outil de dessin à partir de la barre d’outils Éditeur d’images  
  
1.  Cliquez sur un bouton sur le **Éditeur d’images** barre d’outils.  
  
    -   Le **gomme** outil peint sur l’image avec la couleur d’arrière-plan actuelle lorsque vous appuyez sur le bouton gauche de la souris.  
  
    -   Le **crayon** outil dessine à main levée avec une largeur constante d’un pixel.  
  
    -   Le **sélecteur d’options détermine la forme et la taille de l’outil pinceau**.  
  
    -   Le **aérographe** outil distribue aléatoirement des pixels de couleur autour du centre du pinceau.  
  
        > [!TIP]
        >  Info-bulles s’affichent lorsque vous placez votre curseur sur les boutons sur le [barre d’outils Éditeur d’images](../windows/toolbar-image-editor-for-icons.md). Ces conseils vous aideront à identifier les différents boutons mentionnés ici.  
  
2.  Si nécessaire, sélectionnez les couleurs et un pinceau :  
  
    -   Dans le [palette de couleurs](../windows/colors-window-image-editor-for-icons.md), cliquez sur le bouton gauche de la souris pour sélectionner une couleur de premier plan ou le bouton droit de la souris pour sélectionner une couleur d’arrière-plan.  
  
    -   Dans le [sélecteur d’Options](../windows/toolbar-image-editor-for-icons.md), cliquez sur une forme qui représente le pinceau à utiliser.  
  
3.  Pointez vers l’emplacement sur l’image où vous souhaitez démarrer le dessin ou de la peinture. Le pointeur change de forme en fonction de l’outil que vous avez sélectionné.  
  
4.  Appuyez sur le bouton gauche de la souris (pour la couleur de premier plan) ou sur le bouton droit de la souris (pour la couleur d’arrière-plan) et maintenez-le enfoncé en tant que vous draw.  
  
### <a name="to-select-and-use-a-drawing-tool-from-the-image-menu"></a>Pour sélectionner et utiliser un outil de dessin dans le menu Image  
  
1.  Cliquez sur le **Image** menu et sélectionnez le **outils** commande.  
  
2.  Dans le sous-menu en cascade, choisissez l’outil que vous souhaitez utiliser.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Configuration requise  
 Aucun.  
  
## <a name="see-also"></a>Voir aussi  
 [Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Modification de ressources graphiques](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)   
 [Utilisation des couleurs](../windows/working-with-color-image-editor-for-icons.md)
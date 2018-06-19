---
title: Touches d’accès (Éditeur d’images pour les icônes) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
dev_langs:
- C++
helpviewer_keywords:
- accelerator keys
- Image editor [C++], accelerator keys
ms.assetid: add37861-3e17-4a6f-89e8-46df12e74a90
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f2b19fb16410f7d720d11e8b8560cde4cadf10b1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861530"
---
# <a name="accelerator-keys-image-editor-for-icons"></a>Touches accélérateur (Éditeur d'images pour les icônes)
Voici les touches accélérateur pour les commandes de l’éditeur d’Image qui sont liés aux clés par défaut. Pour modifier les touches d’accès, cliquez sur **Options** sur la **outils** menu, puis choisissez **clavier** sous le **environnement** dossier. Pour plus d’informations, consultez [Identification et personnalisation des raccourcis clavier](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).  
  
> [!NOTE]
>  Les options disponibles dans les boîtes de dialogue, ainsi que les noms et emplacements des commandes de menu que vous voyez, peuvent différer de ce qui est décrit dans l'aide selon vos paramètres actifs ou votre édition. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
|Commande|Touches|Description|  
|-------------|----------|-----------------|  
|Image.AirBrushTool|CTRL + A|Dessine à l’aide d’un aérographe avec la taille sélectionnée et la couleur.|  
|Image.BrushTool|CTRL + B|Dessine à l’aide d’un pinceau avec la forme sélectionnée, la taille et la couleur.|  
|Image.CopyAndOutlineSelection|CTRL + MAJ + U|Crée une copie de la sélection actuelle et met un contour. Si la couleur d’arrière-plan est contenue dans la sélection actuelle, il sera exclu si vous avez [transparent](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md) sélectionné.|  
|Image.DrawOpaque|CTRL + J|Rend la sélection actuelle soit [transparent ou opaque](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).|  
|Image.EllipseTool|CTRL + P|Dessine une ellipse avec la largeur de la ligne sélectionnée et la couleur.|  
|Image.EraserTool|CTRL + MAJ + I|Efface une partie de l’image (avec la couleur d’arrière-plan actuelle).|  
|Image.FilledEllipseTool|CTRL + MAJ + ALT + P|Dessine une ellipse remplie.|  
|Image.FilledRectangleTool|CTRL + MAJ + ALT + R|Dessine un rectangle rempli.|  
|Image.FilledRoundRectangleTool|CTRL + MAJ + ALT + W|Dessine un rectangle arrondi et rempli.|  
|Image.FillTool|CTRL + F|Remplit une zone.|  
|Image.FlipHorizontal|Ctrl+H|Retourne l'image ou la sélection horizontalement.|  
|Image.FlipVertical|MAJ + ALT + H|Retourne l'image ou la sélection verticalement.|  
|Image.LargerBrush|CTRL + =|Augmente la taille de la brosse d'un pixel dans chaque direction. Pour réduire la taille de la brosse, consultez Image.SmallerBrush dans ce tableau.|  
|Image.LineTool|Ctrl+L|Dessine une ligne droite de la forme, de la taille et de la couleur sélectionnées.|  
|Image.MagnificationTool|CTRL + M|Active le **loupe** outil qui vous permet d’agrandir des sections spécifiques de votre image.|  
|Image.Magnify|CTRL + MAJ + M|Bascule entre le facteur d'agrandissement actuel et le facteur 1:1.|  
|Image.NewImageType|INSERT|Lance le [nouveau \<appareil > boîte de dialogue Type d’Image](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md) avec lequel vous pouvez créer une image pour un type d’image différent.|  
|Image.NextColor|CTRL +]<br /><br /> ou<br /><br /> CTRL + FLÈCHE DROITE|Change la couleur de dessin de premier plan par la couleur suivante de la palette.|  
|Image.NextRightColor|CTRL + MAJ +]<br /><br /> ou<br /><br /> MAJ + CTRL + FLÈCHE DROITE|Change la couleur de dessin d'arrière-plan par la couleur suivante de la palette.|  
|Image.OutlinedEllipseTool|MAJ + ALT + P|Dessine une ellipse remplie avec un contour.|  
|Image.OutlinedRectangleTool|MAJ + ATL + R|Dessine un rectangle rempli avec un contour|  
|Image.OutlinedRoundRectangleTool|MAJ + ALT + W|Dessine un rectangle arrondi rempli avec un contour.|  
|Image.PencilTool|CTRL + I|Dessine à l'aide d'un pinceau d'un pixel.|  
|Image.PreviousColor|CTRL + [<br /><br /> ou<br /><br /> CTRL + FLÈCHE GAUCHE|Change la couleur de dessin de premier plan par la couleur précédente de la palette.|  
|Image.PreviousRightColor|CTRL + MAJ + [<br /><br /> ou<br /><br /> MAJ + CTRL + FLÈCHE GAUCHE|Change la couleur de dessin d'arrière-plan par la couleur précédente de la palette.|  
|Image.RectangleSelectionTool|MAJ + ALT + S|Sélectionne une partie rectangulaire de l’image à déplacer, copier ou modifier.|  
|Image.RectangleTool|ATL + R|Dessine un rectangle avec la largeur de la ligne sélectionnée et la couleur.|  
|Image.Rotate90Degrees|CTRL + MAJ + H|Fait pivoter l'image ou la sélection de 90 degrés.|  
|Image.RoundedRectangleTool|ALT + W|Dessine un rectangle arrondi de la largeur de la ligne sélectionnée et la couleur.|  
|Image.ShowGrid|CTRL + ALT + S|Active ou désactive la grille de pixels (Active ou désactive le **grille de pixels** option dans le [boîte de dialogue Paramètres de la grille](../windows/grid-settings-dialog-box-image-editor-for-icons.md)).|  
|Image.ShowTileGrid|CTRL + MAJ + ALT + S|Active ou désactive la grille (Active ou désactive le **grille** option dans le [boîte de dialogue Paramètres de la grille](../windows/grid-settings-dialog-box-image-editor-for-icons.md)).|  
|Image.SmallBrush|CTRL +. (point)|Réduit la **pinceau** taille à un pixel. (Consultez également Image.LargerBrush et Image.SmallerBrush dans ce tableau.)|  
|Image.SmallerBrush|CTRL + - (moins)|Réduit la taille du pinceau d'un pixel dans chaque direction. Pour augmenter de nouveau la taille du pinceau, consultez Image.LargerBrush dans ce tableau.|  
|Image.TextTool|CTRL + T|Ouvre le [boîte de dialogue Outil texte](../windows/text-tool-dialog-box-image-editor-for-icons.md).|  
|Image.UseSelectionAsBrush|CTRL + U|Dessine à l'aide de la sélection actuelle comme pinceau.|  
|Image.ZoomIn|CTRL + MAJ +. (point)<br /><br /> ou<br /><br /> CTRL + FLÈCHE HAUT|Augmente le facteur d'agrandissement de l'affichage actuel.|  
|Image.ZoomOut|CTRL +, (virgule)<br /><br /> ou<br /><br /> CTRL + FLÈCHE BAS|Réduit le facteur d'agrandissement de l'affichage actuel.|  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Spécifications  
 Aucun  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)


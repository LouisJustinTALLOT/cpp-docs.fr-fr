---
title: Touches accélérateur (Éditeur d’images C++ pour les icônes)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
helpviewer_keywords:
- accelerator keys
- Image editor [C++], accelerator keys
ms.assetid: add37861-3e17-4a6f-89e8-46df12e74a90
ms.openlocfilehash: 062b860849d968e18657afb66b568a1bf6f2b6d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505103"
---
# <a name="accelerator-keys-c-image-editor-for-icons"></a>Touches accélérateur (Éditeur d’images C++ pour les icônes)

Voici les touches accélérateur pour les commandes de l’éditeur d’Image qui sont liés aux clés par défaut. Pour modifier les touches d’accès rapide, cliquez sur **Options** sur le **outils** menu, puis choisissez **clavier** sous le **environnement** dossier. Pour plus d’informations, consultez [Identification et personnalisation des raccourcis clavier](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

> [!NOTE]
> Les options disponibles dans les boîtes de dialogue, ainsi que les noms et emplacements des commandes de menu que vous voyez, peuvent différer de ce qui est décrit dans l'aide selon vos paramètres actifs ou votre édition. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

|Commande|Touches|Description|
|-------------|----------|-----------------|
|Image.AirBrushTool|**Ctrl** + **A**|Dessine en utilisant un aérographe avec la taille sélectionnée et la couleur.|
|Image.BrushTool|**CTRL** + **B**|Dessine à l’aide d’un pinceau avec la forme sélectionnée, la taille et la couleur.|
|Image.CopyAndOutlineSelection|**CTRL** + **MAJ** + **U**|Crée une copie de la sélection actuelle et met un contour. Si la couleur d’arrière-plan est contenue dans la sélection actuelle, celle-ci sera exclue si vous avez [transparent](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md) sélectionné.|
|Image.DrawOpaque|**Ctrl** + **J**|Rend la sélection actuelle soit [opaque ou transparent](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).|
|Image.EllipseTool|**Ctrl** + **P**|Dessine une ellipse avec la largeur de ligne sélectionné et la couleur.|
|Image.EraserTool|**Ctrl** + **Maj** + **I**|Efface une partie de l’image (avec la couleur d’arrière-plan actuelle).|
|Image.FilledEllipseTool|**CTRL** + **MAJ** + **Alt** + **P**|Dessine une ellipse remplie.|
|Image.FilledRectangleTool|**CTRL** + **MAJ** + **Alt** + **R**|Dessine un rectangle rempli.|
|Image.FilledRoundRectangleTool|**CTRL** + **MAJ** + **Alt** + **W**|Dessine un rectangle arrondi et rempli.|
|Image.FillTool|**Ctrl** + **F**|Remplit une zone.|
|Image.FlipHorizontal|**Ctrl** + **H**|Retourne l'image ou la sélection horizontalement.|
|Image.FlipVertical|**MAJ**+ **Alt** + **H**|Retourne l'image ou la sélection verticalement.|
|Image.LargerBrush|**CTRL** + **=**|Augmente la taille de la brosse d'un pixel dans chaque direction. Pour réduire la taille de la brosse, consultez Image.SmallerBrush dans ce tableau.|
|Image.LineTool|**Ctrl** + **L**|Dessine une ligne droite de la forme, de la taille et de la couleur sélectionnées.|
|Image.MagnificationTool|**CTRL** + **M**|Active le **Magnify** outil qui vous permet d’agrandir des sections spécifiques de votre image.|
|Image.Magnify|**Ctrl** + **Maj** + **M**|Bascule entre le facteur d'agrandissement actuel et le facteur 1:1.|
|Image.NewImageType|**Insert**|Lance le [New \<appareil > boîte de dialogue Type d’Image](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md) avec lequel vous pouvez créer une image pour un type d’image différent.|
|Image.NextColor|**Ctrl** + **]**<br /><br /> ou<br /><br /> **CTRL** + **flèche droite**|Change la couleur de dessin de premier plan par la couleur suivante de la palette.|
|Image.NextRightColor|**Ctrl** + **Maj** + **]**<br /><br /> ou<br /><br /> **MAJ** + **Ctrl** + **flèche droite**|Change la couleur de dessin d'arrière-plan par la couleur suivante de la palette.|
|Image.OutlinedEllipseTool|**MAJ** + **Alt** + **P**|Dessine une ellipse remplie avec un contour.|
|Image.OutlinedRectangleTool|**MAJ** + **Alt** + **R**|Dessine un rectangle rempli avec un contour|
|Image.OutlinedRoundRectangleTool|**MAJ** + **Alt** + **W**|Dessine un rectangle arrondi rempli avec un contour.|
|Image.PencilTool|**Ctrl** + **I**|Dessine à l'aide d'un pinceau d'un pixel.|
|Image.PreviousColor|**Ctrl** + **[**<br /><br /> ou<br /><br /> **CTRL** + **flèche gauche**|Change la couleur de dessin de premier plan par la couleur précédente de la palette.|
|Image.PreviousRightColor|**Ctrl** + **Maj** + **[**<br /><br /> ou<br /><br /> **MAJ** + **Ctrl** + **flèche gauche**|Change la couleur de dessin d'arrière-plan par la couleur précédente de la palette.|
|Image.RectangleSelectionTool|**MAJ** + **Alt** + **S**|Sélectionne une partie rectangulaire de l’image à déplacer, copier ou modifier.|
|Image.RectangleTool|ATL + R|Dessine un rectangle avec la largeur de ligne sélectionné et la couleur.|
|Image.Rotate90Degrees|**Ctrl** + **Maj** + **H**|Fait pivoter l'image ou la sélection de 90 degrés.|
|Image.RoundedRectangleTool|**ALT** + **W**|Dessine un rectangle arrondi avec la largeur de ligne sélectionné et la couleur.|
|Image.ShowGrid|**CTRL** + **Alt** + **S**|Active ou désactive la grille de pixels (sélectionne ou efface la **grille de pixels** option dans le [boîte de dialogue Paramètres de la grille](../windows/grid-settings-dialog-box-image-editor-for-icons.md)).|
|Image.ShowTileGrid|**CTRL** + **MAJ** + **Alt** + **S**|Active ou désactive la grille mosaïque (sélectionne ou efface la **grille mosaïque** option dans le [boîte de dialogue Paramètres de la grille](../windows/grid-settings-dialog-box-image-editor-for-icons.md)).|
|Image.SmallBrush|**Ctrl** + **.** (période)|Réduit la **pinceau** taille à un pixel. (Consultez également Image.LargerBrush et Image.SmallerBrush dans ce tableau.)|
|Image.SmallerBrush|**CTRL**  +  **-** (moins)|Réduit la taille du pinceau d'un pixel dans chaque direction. Pour augmenter de nouveau la taille du pinceau, consultez Image.LargerBrush dans ce tableau.|
|Image.TextTool|**Ctrl** + **T**|Ouvre le [boîte de dialogue Outil texte](../windows/text-tool-dialog-box-image-editor-for-icons.md).|
|Image.UseSelectionAsBrush|**CTRL** + **U**|Dessine à l'aide de la sélection actuelle comme pinceau.|
|Image.ZoomIn|**CTRL** + **MAJ** + **.** (période)<br /><br /> ou<br /><br /> **CTRL** + **flèche vers le haut**|Augmente le facteur d'agrandissement de l'affichage actuel.|
|Image.ZoomOut|**CTRL** + **,** (virgule)<br /><br /> ou<br /><br /> **CTRL** + **flèche vers le bas**|Réduit le facteur d'agrandissement de l'affichage actuel.|

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Aucun.

## <a name="see-also"></a>Voir aussi

[Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)
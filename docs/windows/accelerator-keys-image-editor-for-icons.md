---
title: Touches accélérateur (Éditeur d’images C++ pour les icônes)
ms.date: 02/15/2019
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
helpviewer_keywords:
- accelerator keys
- Image editor [C++], accelerator keys
ms.assetid: add37861-3e17-4a6f-89e8-46df12e74a90
ms.openlocfilehash: 45afdf4b3b557b560d7597b1bb4330c36a1fc84d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59025083"
---
# <a name="accelerator-keys-c-image-editor-for-icons"></a>Touches accélérateur (Éditeur d’images C++ pour les icônes)

Voici les touches accélérateur pour les commandes de l’éditeur d’Image qui sont liés aux clés par défaut. Pour changer les touches accélérateur, accédez au menu **outils** > **Options** et choisissez **clavier** sous le **environnement** dossier. Pour plus d’informations, consultez [Identification et personnalisation des raccourcis clavier](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

> [!NOTE]
> Les options disponibles dans les boîtes de dialogue, ainsi que les noms et emplacements des commandes de menu que vous voyez, peuvent différer de ce qui est décrit dans l'aide selon vos paramètres actifs ou votre édition. Pour modifier vos paramètres, accédez au menu **outils** > **importation et exportation de paramètres**. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

|Commande|Touches|Description|
|-------------|----------|-----------------|
|Image.AirBrushTool|**Ctrl** + **A**|Dessine en utilisant un aérographe avec la taille sélectionnée et la couleur.|
|Image.BrushTool|**Ctrl** + **B**|Dessine à l’aide d’un pinceau avec la forme sélectionnée, la taille et la couleur.|
|Image.CopyAndOutlineSelection|**Ctrl** + **Shift** + **U**|Crée une copie de la sélection actuelle et met un contour. Si la couleur d’arrière-plan est contenue dans la sélection actuelle, celle-ci sera exclue si vous avez [transparent](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md) sélectionné.|
|Image.DrawOpaque|**Ctrl** + **J**|Rend la sélection actuelle soit [opaque ou transparent](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).|
|Image.EllipseTool|**Ctrl** + **P**|Dessine une ellipse avec la largeur de ligne sélectionné et la couleur.|
|Image.EraserTool|**Ctrl** + **Maj** + **I**|Efface une partie de l’image (avec la couleur d’arrière-plan actuelle).|
|Image.FilledEllipseTool|**CTRL** + **MAJ** + **Alt** + **P**|Dessine une ellipse remplie.|
|Image.FilledRectangleTool|**CTRL** + **MAJ** + **Alt** + **R**|Dessine un rectangle rempli.|
|Image.FilledRoundRectangleTool|**CTRL** + **MAJ** + **Alt** + **W**|Dessine un rectangle arrondi et rempli.|
|Image.FillTool|**Ctrl** + **F**|Remplit une zone.|
|Image.FlipHorizontal|**Ctrl** + **H**|Retourne l'image ou la sélection horizontalement.|
|Image.FlipVertical|**MAJ**+ **Alt** + **H**|Retourne l'image ou la sélection verticalement.|
|Image.LargerBrush|**Ctrl** + **=**|Augmente la taille de la brosse d'un pixel dans chaque direction. Pour réduire la taille de la brosse, consultez Image.SmallerBrush dans ce tableau.|
|Image.LineTool|**Ctrl** + **L**|Dessine une ligne droite de la forme, de la taille et de la couleur sélectionnées.|
|Image.MagnificationTool|**Ctrl** + **M**|Active le **Magnify** outil qui vous permet d’agrandir des sections spécifiques de votre image.|
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
|Image.ShowGrid|**Ctrl** + **Alt** + **S**|Active ou désactive la grille de pixels (sélectionne ou efface la **grille de pixels** option dans le [boîte de dialogue Paramètres de la grille](../windows/grid-settings-dialog-box-image-editor-for-icons.md)).|
|Image.ShowTileGrid|**CTRL** + **MAJ** + **Alt** + **S**|Active ou désactive la grille mosaïque (sélectionne ou efface la **grille mosaïque** option dans le [boîte de dialogue Paramètres de la grille](../windows/grid-settings-dialog-box-image-editor-for-icons.md)).|
|Image.SmallBrush|**Ctrl** + **.** (période)|Réduit la **pinceau** taille à un pixel. (Consultez également Image.LargerBrush et Image.SmallerBrush dans ce tableau.)|
|Image.SmallerBrush|**CTRL**  +  **-** (moins)|Réduit la taille du pinceau d'un pixel dans chaque direction. Pour développer de nouveau la taille du pinceau, consultez Image.LargerBrush dans ce tableau.|
|Image.TextTool|**Ctrl** + **T**|Ouvre le [boîte de dialogue Outil texte](../windows/text-tool-dialog-box-image-editor-for-icons.md).|
|Image.UseSelectionAsBrush|**Ctrl** + **U**|Dessine à l'aide de la sélection actuelle comme pinceau.|
|Image.ZoomIn|**Ctrl** + **Shift** + **.** (période)<br /><br /> ou<br /><br /> **CTRL** + **flèche vers le haut**|Augmente le facteur d'agrandissement de l'affichage actuel.|
|Image.ZoomOut|**Ctrl** + **,** (comma)<br /><br /> ou<br /><br /> **CTRL** + **flèche vers le bas**|Réduit le facteur d'agrandissement de l'affichage actuel.|

## <a name="requirements"></a>Configuration requise

Aucun.

## <a name="see-also"></a>Voir aussi

[Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)<br/>
[Guide pratique pour créer une icône ou une autre image](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Guide pratique pour modifier une image](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Guide pratique pour utiliser un outil de dessin](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[Guide pratique pour utiliser les couleurs](../windows/working-with-color-image-editor-for-icons.md)<br/>
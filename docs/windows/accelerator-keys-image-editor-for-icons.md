---
title: Touches accélérateur (C++ éditeur d’images pour les icônes)
ms.date: 02/15/2019
helpviewer_keywords:
- accelerator keys
- Image editor [C++], accelerator keys
ms.assetid: add37861-3e17-4a6f-89e8-46df12e74a90
ms.openlocfilehash: 867c7d2c217b5efb832654a7863e834a4351c126
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167574"
---
# <a name="accelerator-keys-c-image-editor-for-icons"></a>Touches accélérateur (C++ éditeur d’images pour les icônes)

Vous trouverez ci-dessous les touches accélérateur pour les commandes de l’éditeur d’images qui sont liées aux clés par défaut. Pour modifier les touches accélérateur, accédez à **Outils** de menu > **options** et choisissez **clavier** dans le dossier **environnement** . Pour plus d’informations, consultez [Identification et personnalisation des raccourcis clavier](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

> [!NOTE]
> Les options disponibles dans les boîtes de dialogue, ainsi que les noms et emplacements des commandes de menu que vous voyez, peuvent différer de ce qui est décrit dans l'aide selon vos paramètres actifs ou votre édition. Pour modifier vos paramètres, accédez à **Outils** de menu > **paramètres d’importation et d’exportation**. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

|Commande|Keys|Description|
|-------------|----------|-----------------|
|Image.AirBrushTool|**Ctrl** + **A**|Dessine à l’aide d’un aérographe avec la taille et la couleur sélectionnées.|
|Image.BrushTool|**Ctrl** + **B**|Dessine à l’aide d’un pinceau avec la forme, la taille et la couleur sélectionnées.|
|Image.CopyAndOutlineSelection|**Ctrl** + **MAJ** + **U**|Crée une copie de la sélection actuelle et met un contour. Si la couleur d’arrière-plan est contenue dans la sélection actuelle, elle sera exclue si vous avez sélectionné [transparent](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md) .|
|Image.DrawOpaque|**Ctrl** + **J**|Rend la sélection actuelle [opaque ou transparente](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).|
|Image.EllipseTool|**Ctrl** + **P**|Dessine une ellipse avec la largeur et la couleur de ligne sélectionnées.|
|Image.EraserTool|**Ctrl** + **Maj** + **I**|Efface une partie de l’image (avec la couleur d’arrière-plan actuelle).|
|Image.FilledEllipseTool|**Ctrl** + **maj** + **ALT** + **P**|Dessine une ellipse remplie.|
|Image.FilledRectangleTool|**Ctrl** + **maj** + **ALT** + **R**|Dessine un rectangle rempli.|
|Image.FilledRoundRectangleTool|**Ctrl** + **maj** + **ALT** + **W**|Dessine un rectangle arrondi et rempli.|
|Image.FillTool|**Ctrl** + **F**|Remplit une zone.|
|Image.FlipHorizontal|**Ctrl** + **H**|Retourne l'image ou la sélection horizontalement.|
|Image.FlipVertical|**Maj**+ **ALT** + **H**|Retourne l'image ou la sélection verticalement.|
|Image.LargerBrush|**Ctrl** +  **=**|Augmente la taille de la brosse d'un pixel dans chaque direction. Pour réduire la taille de la brosse, consultez Image.SmallerBrush dans ce tableau.|
|Image.LineTool|**Ctrl** + **L**|Dessine une ligne droite de la forme, de la taille et de la couleur sélectionnées.|
|Image.MagnificationTool|**Ctrl** + **M**|Active l’outil **loupe** , qui vous permet d’agrandir des sections spécifiques de votre image.|
|Image.Magnify|**Ctrl** + **Maj** + **M**|Bascule entre le facteur d'agrandissement actuel et le facteur 1:1.|
|Image.NewImageType|**Insérer**|Lance la [boîte de dialogue nouveau type d’image > de l’appareil \<](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md) dans laquelle vous pouvez créer une image pour un type d’image différent.|
|Image.NextColor|**Ctrl** +  **]**<br /><br /> - ou -<br /><br /> **Ctrl** + **flèche droite**|Change la couleur de dessin de premier plan par la couleur suivante de la palette.|
|Image.NextRightColor|**Ctrl** + **Maj** +  **]**<br /><br /> - ou -<br /><br /> **Maj** + **CTRL** + **flèche droite**|Change la couleur de dessin d'arrière-plan par la couleur suivante de la palette.|
|Image.OutlinedEllipseTool|**Maj** + **ALT** + **P**|Dessine une ellipse remplie avec un contour.|
|Image.OutlinedRectangleTool|**Maj** + **ALT** + **R**|Dessine un rectangle rempli avec un contour|
|Image.OutlinedRoundRectangleTool|**Maj** + **ALT** + **W**|Dessine un rectangle arrondi rempli avec un contour.|
|Image.PencilTool|**Ctrl** + **I**|Dessine à l'aide d'un pinceau d'un pixel.|
|Image.PreviousColor|**Ctrl** +  **[**<br /><br /> - ou -<br /><br /> **Ctrl** + **flèche gauche**|Change la couleur de dessin de premier plan par la couleur précédente de la palette.|
|Image.PreviousRightColor|**Ctrl** + **Maj** +  **[**<br /><br /> - ou -<br /><br /> **Maj** + **CTRL** + **flèche gauche**|Change la couleur de dessin d'arrière-plan par la couleur précédente de la palette.|
|Image.RectangleSelectionTool|**Maj** + **ALT** + **S**|Sélectionne une partie rectangulaire de l’image à déplacer, copier ou modifier.|
|Image.RectangleTool|ATL + R|Dessine un rectangle avec la largeur et la couleur de ligne sélectionnées.|
|Image.Rotate90Degrees|**Ctrl** + **Maj** + **H**|Fait pivoter l'image ou la sélection de 90 degrés.|
|Image.RoundedRectangleTool|**Alt** + **W**|Dessine un rectangle arrondi avec la largeur et la couleur de ligne sélectionnées.|
|Image.ShowGrid|**Ctrl** + **ALT** + **S**|Active ou désactive l’option **grille** de pixels dans la [boîte de dialogue Paramètres](../windows/grid-settings-dialog-box-image-editor-for-icons.md)de la grille.|
|Image.ShowTileGrid|**Ctrl** + **maj** + **ALT** + **S**|Active/désactive la grille de mosaïques (active ou désactive l’option **grille mosaïque** dans la [boîte de dialogue Paramètres](../windows/grid-settings-dialog-box-image-editor-for-icons.md)de la grille).|
|Image.SmallBrush|**Ctrl** +  **.** (point)|Réduit la taille du **pinceau** à un pixel. (Consultez également Image.LargerBrush et Image.SmallerBrush dans ce tableau.)|
|Image.SmallerBrush|**Ctrl** +  **-** (moins)|Réduit la taille du pinceau d'un pixel dans chaque direction. Pour développer de nouveau la taille du pinceau, consultez Image.LargerBrush dans ce tableau.|
|Image.TextTool|**Ctrl** + **T**|Ouvre la [boîte de dialogue outil texte](../windows/text-tool-dialog-box-image-editor-for-icons.md).|
|Image.UseSelectionAsBrush|**Ctrl** + **U**|Dessine à l'aide de la sélection actuelle comme pinceau.|
|Image.ZoomIn|**Ctrl** + **Shift** + MAJ **.** (point)<br /><br /> - ou -<br /><br /> **Ctrl** + **flèche haut**|Augmente le facteur d'agrandissement de l'affichage actuel.|
|Image.ZoomOut|**Ctrl** +  **,** (virgule)<br /><br /> - ou -<br /><br /> **Ctrl** + **flèche bas**|Réduit le facteur d'agrandissement de l'affichage actuel.|

## <a name="requirements"></a>Spécifications

None

## <a name="see-also"></a>Voir aussi

[Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)<br/>
[Comment : créer une icône ou une autre image](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Comment : modifier une image](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Comment : utiliser un outil de dessin](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[Comment : utiliser la couleur](../windows/working-with-color-image-editor-for-icons.md)<br/>

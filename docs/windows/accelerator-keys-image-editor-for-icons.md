---
description: 'En savoir plus sur : touches accélérateur (éditeur d’images C++ pour les icônes)'
title: Touches accélérateur (éditeur d’images C++ pour les icônes)
ms.date: 02/15/2019
helpviewer_keywords:
- accelerator keys
- Image editor [C++], accelerator keys
ms.assetid: add37861-3e17-4a6f-89e8-46df12e74a90
ms.openlocfilehash: 74062789a7fc6ff6b3b15364d1379861f7bea1c6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280285"
---
# <a name="accelerator-keys-c-image-editor-for-icons"></a>Touches accélérateur (éditeur d’images C++ pour les icônes)

Vous trouverez ci-dessous les touches accélérateur pour les commandes de l’éditeur d’images qui sont liées aux clés par défaut. Pour modifier les touches d’accès rapide, accédez à **Outils** de menu  >  **options** et choisissez **clavier** dans le dossier **environnement** . Pour plus d’informations, consultez [Identification et personnalisation des raccourcis clavier](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

> [!NOTE]
> Les options disponibles dans les boîtes de dialogue, ainsi que les noms et emplacements des commandes de menu que vous voyez, peuvent différer de ce qui est décrit dans l'aide selon vos paramètres actifs ou votre édition. Pour modifier vos paramètres, accédez à **Outils** de menu  >  **Importer et exporter les paramètres**. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

|Commande|Keys|Description|
|-------------|----------|-----------------|
|Image. AirBrushTool|**CTRL**  +  **Un**|Dessine à l’aide d’un aérographe avec la taille et la couleur sélectionnées.|
|Image.BrushTool|**Ctrl** + **B**|Dessine à l’aide d’un pinceau avec la forme, la taille et la couleur sélectionnées.|
|Image. CopyAndOutlineSelection|**CTRL**  +  **MAJ**  +  **U**|Crée une copie de la sélection actuelle et met un contour. Si la couleur d’arrière-plan est contenue dans la sélection actuelle, elle sera exclue si vous avez sélectionné [transparent](./image-editor-for-icons.md) .|
|Image.DrawOpaque|**Ctrl** + **J**|Rend la sélection actuelle [opaque ou transparente](./image-editor-for-icons.md).|
|Image.EllipseTool|**CTRL**  +  **P**|Dessine une ellipse avec la largeur et la couleur de ligne sélectionnées.|
|Image. EraserTool|**CTRL**  +  **MAJ**  +  **Je**|Efface une partie de l’image (avec la couleur d’arrière-plan actuelle).|
|Image.FilledEllipseTool|**CTRL**  +  **MAJ**  +  **ALT**  +  **P**|Dessine une ellipse remplie.|
|Image.FilledRectangleTool|**CTRL**  +  **MAJ**  +  **ALT**  +  **R**|Dessine un rectangle rempli.|
|Image. FilledRoundRectangleTool|**CTRL**  +  **MAJ**  +  **ALT**  +  **W**|Dessine un rectangle arrondi et rempli.|
|Image.FillTool|**CTRL**  +  **F**|Remplit une zone.|
|Image.FlipHorizontal|**CTRL**  +  **H**|Retourne l'image ou la sélection horizontalement.|
|Image.FlipVertical|**MAJ** +  **ALT**  +  **H**|Retourne l'image ou la sélection verticalement.|
|Image.LargerBrush|**Clavier** + **=**|Augmente la taille de la brosse d'un pixel dans chaque direction. Pour réduire la taille de la brosse, consultez Image.SmallerBrush dans ce tableau.|
|Image.LineTool|**CTRL**  +  **L**|Dessine une ligne droite de la forme, de la taille et de la couleur sélectionnées.|
|Image.MagnificationTool|**CTRL**  +  **M**|Active l’outil **loupe** , qui vous permet d’agrandir des sections spécifiques de votre image.|
|Image.Magnify|**CTRL**  +  **MAJ**  +  **M**|Bascule entre le facteur d'agrandissement actuel et le facteur 1:1.|
|Image.NewImageType|**Insérer**|Ouvre la [ \<Device> boîte de dialogue nouveau type d’image](./creating-an-icon-or-other-image-image-editor-for-icons.md) dans laquelle vous pouvez créer une image pour un autre type d’image.|
|Image.NextColor|**CTRL**  +  **]**<br /><br /> - ou -<br /><br /> **CTRL**  +  **Flèche droite**|Change la couleur de dessin de premier plan par la couleur suivante de la palette.|
|Image.NextRightColor|**CTRL**  +  **MAJ**  +  **]**<br /><br /> - ou -<br /><br /> **MAJ**  +  **CTRL**  +  **Flèche droite**|Change la couleur de dessin d'arrière-plan par la couleur suivante de la palette.|
|Image.OutlinedEllipseTool|**MAJ**  +  **ALT**  +  **P**|Dessine une ellipse remplie avec un contour.|
|Image.OutlinedRectangleTool|**MAJ**  +  **ALT**  +  **R**|Dessine un rectangle rempli avec un contour|
|Image. OutlinedRoundRectangleTool|**MAJ**  +  **ALT**  +  **W**|Dessine un rectangle arrondi rempli avec un contour.|
|Image.PencilTool|**CTRL**  +  **Je**|Dessine à l'aide d'un pinceau d'un pixel.|
|Image.PreviousColor|**CTRL**  +  **[**<br /><br /> - ou -<br /><br /> **CTRL**  +  **Flèche gauche**|Change la couleur de dessin de premier plan par la couleur précédente de la palette.|
|Image.PreviousRightColor|**CTRL**  +  **MAJ**  +  **[**<br /><br /> - ou -<br /><br /> **MAJ**  +  **CTRL**  +  **Flèche gauche**|Change la couleur de dessin d'arrière-plan par la couleur précédente de la palette.|
|Image.RectangleSelectionTool|**MAJ**  +  **ALT**  +  **S**|Sélectionne une partie rectangulaire de l’image à déplacer, copier ou modifier.|
|Image.RectangleTool|ATL + R|Dessine un rectangle avec la largeur et la couleur de ligne sélectionnées.|
|Image.Rotate90Degrees|**CTRL**  +  **MAJ**  +  **H**|Fait pivoter l'image ou la sélection de 90 degrés.|
|Image.RoundedRectangleTool|**ALT**  +  **W**|Dessine un rectangle arrondi avec la largeur et la couleur de ligne sélectionnées.|
|Image.ShowGrid|**CTRL**  +  **ALT**  +  **S**|Active ou désactive l’option **grille** de pixels dans la [boîte de dialogue Paramètres](./image-editor-for-icons.md)de la grille.|
|Image.ShowTileGrid|**CTRL**  +  **MAJ**  +  **ALT**  +  **S**|Active/désactive la grille de mosaïques (active ou désactive l’option **grille mosaïque** dans la [boîte de dialogue Paramètres](./image-editor-for-icons.md)de la grille).|
|Image.SmallBrush|**CTRL**  +  **.** (point)|Réduit la taille du **pinceau** à un pixel. (Consultez également Image.LargerBrush et Image.SmallerBrush dans ce tableau.)|
|Image.SmallerBrush|  +  CTRL **-** levant|Réduit la taille du pinceau d'un pixel dans chaque direction. Pour développer de nouveau la taille du pinceau, consultez Image.LargerBrush dans ce tableau.|
|Image.TextTool|**CTRL**  +  **T**|Ouvre la [boîte de dialogue outil texte](./image-editor-for-icons.md).|
|Image. UseSelectionAsBrush|**CTRL**  +  **U**|Dessine à l'aide de la sélection actuelle comme pinceau.|
|Image.ZoomIn|**CTRL**  +  **MAJ**  +  **.** (point)<br /><br /> - ou -<br /><br /> **CTRL**  +  **Flèche haut**|Augmente le facteur d'agrandissement de l'affichage actuel.|
|Image.ZoomOut|**CTRL**  +  **,** (virgule)<br /><br /> - ou -<br /><br /> **CTRL**  +  **Flèche bas**|Réduit le facteur d'agrandissement de l'affichage actuel.|

## <a name="requirements"></a>Spécifications

None

## <a name="see-also"></a>Voir aussi

[Éditeur d’images pour les icônes](image-editor-for-icons.md)<br/>
[Comment : créer une icône ou une autre image](creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Comment : modifier une image](selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Comment : utiliser un outil de dessin](using-a-drawing-tool-image-editor-for-icons.md)<br/>
[Comment : utiliser la couleur](working-with-color-image-editor-for-icons.md)<br/>

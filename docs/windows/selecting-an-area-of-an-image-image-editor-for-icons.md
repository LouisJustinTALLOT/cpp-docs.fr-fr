---
title: 'Comment : modifier une image'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.editing
helpviewer_keywords:
- Image editor [C++], image selection
- Image editor [C++], selecting images
- images [C++], selecting
- cursors [C++], selecting areas of
- Image editor [C++], editing images
- Clipboard [C++], pasting
- images [C++], editing
- images [C++], deleting selected parts
- images [C++], copying selected parts
- images [C++], moving selected parts
- images [C++], dragging and replicating selected parts
- images [C++], pasting into
- graphics [C++], editing
- Image editor [C++], flipping and rotating images
- images [C++], flipping
- images [C++], rotating
- Image editor [C++], resizing images
- graphics [C++], resizing
- images [C++], resizing
- resizing images
- size [C++], images
- images [C++], cropping
- images [C++], extending
- Image editor [C++], cropping or extending images
- Image editor [C++], shrinking and stretching images
- images [C++], stretching
- images [C++], shrinking
- bitmaps [C++], shrinking
- bitmaps [C++], stretching
- Image editor [C++], editing images
- images [C++], editing
- images [C++], properties
- Image editor [C++], Properties window
- Properties window, image editor
ms.assetid: 8b6ce4ad-eba1-4ece-86ba-cea92c3edff2
ms.openlocfilehash: ecfd69594c05c210743e0c22c804a4713a8229ef
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509635"
---
# <a name="how-to-edit-an-image"></a>Comment : modifier une image

Vous pouvez utiliser les outils de sélection pour définir une zone d’une image que vous souhaitez couper, copier, effacer, redimensionner, inverser ou déplacer. Avec l’outil Sélection d’un **rectangle** , vous pouvez définir et sélectionner une zone rectangulaire de l’image. Avec l’outil **sélection irrégulière** , vous pouvez dessiner un contour à main levée de la zone que vous souhaitez sélectionner pour une opération couper, copier ou autre.

> [!NOTE]
> Consultez les outils **sélection de rectangles** et **sélection irrégulière** illustrés dans la [barre d’outils Éditeur d’images](./image-editor-for-icons.md) ou affichez les info-bulles associées à chaque bouton de la barre d’outils de l’éditeur d' **images** .

Vous pouvez également créer un pinceau personnalisé à partir d’une sélection. Pour plus d’informations, consultez [création d’un pinceau personnalisé](./using-a-drawing-tool-image-editor-for-icons.md).

## <a name="how-to"></a>Procédure

Pour modifier une image, consultez Comment :

### <a name="to-select-an-image"></a>Pour sélectionner une image

1. Utilisez la barre d’outils de l' **éditeur d’images** ou accédez à menu **Image**  >  **Outils** image et choisissez l’outil de sélection de votre choix.

1. Déplacez le point d’insertion dans un coin de la zone d’image que vous souhaitez sélectionner. Les réticules apparaissent lorsque le point d’insertion se trouve sur l’image.

1. Faites glisser le point d’insertion vers le coin opposé de la zone que vous souhaitez sélectionner. Un rectangle indique les pixels qui seront sélectionnés. Tous les pixels dans le rectangle, y compris ceux qui se trouvent sous le rectangle, sont inclus dans la sélection.

1. Relâchez le bouton de la souris. La bordure de sélection encadre la zone sélectionnée.

#### <a name="to-select-an-entire-image"></a>Pour sélectionner l’intégralité d’une image

Sélectionnez l’image en dehors de la sélection actuelle. La bordure de sélection change le focus et englobe la totalité de l’image.

### <a name="to-edit-parts-of-an-image"></a>Pour modifier des parties d’une image

Vous pouvez effectuer des opérations de modification standard (couper, copier, effacer et déplacer) sur une [sélection](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md), qu’il s’agisse de la totalité de l’image ou d’une partie de celle-ci. Étant donné que l' **éditeur d’images** utilise le **presse-papiers Windows**, vous pouvez transférer des images entre l' **éditeur d’images** et d’autres applications pour Windows.

En outre, vous pouvez redimensionner la sélection, qu’elle comprenne la totalité de l’image ou juste une partie.

#### <a name="to-cut-the-current-selection-and-move-it-to-the-clipboard"></a>Pour couper la sélection actuelle et la déplacer dans le presse-papiers

Accédez au menu **modifier**  >  **couper**.

#### <a name="to-copy-the-selection"></a>Pour copier la sélection

1. Placez le pointeur à l’intérieur de la bordure de sélection ou n’importe où, à l’exception des poignées de redimensionnement.

1. Maintenez la touche **CTRL** enfoncée tout en faisant glisser la sélection vers un nouvel emplacement. La zone de la sélection d’origine est inchangée.

1. Pour copier la sélection dans l’image à son emplacement actuel, sélectionnez à l’extérieur du curseur de sélection.

#### <a name="to-paste-the-clipboard-contents-into-an-image"></a>Pour coller le contenu du presse-papiers dans une image

1. Accédez au menu **Edition**  >  **coller**.

   Le contenu du presse-papiers, entouré de la bordure de sélection, s’affiche dans l’angle supérieur gauche du volet.

1. Placez le pointeur dans la bordure de sélection et faites glisser l’image vers l’emplacement souhaité sur l’image.

1. Pour ancrer l’image à son nouvel emplacement, sélectionnez en dehors de la bordure de sélection.

#### <a name="to-delete-the-current-selection-without-moving-it-to-the-clipboard"></a>Pour supprimer la sélection actuelle sans la déplacer dans le presse-papiers

Accédez au menu **modifier**  >  **supprimer**.

   La zone d’origine de la sélection est remplie avec la couleur d’arrière-plan actuelle.

> [!NOTE]
> Vous pouvez accéder aux commandes **couper**, **copier**, **coller**et **supprimer** en cliquant avec le bouton droit dans la fenêtre de **affichage des ressources** .

#### <a name="to-move-the-selection"></a>Pour déplacer la sélection

1. Placez le pointeur à l’intérieur de la bordure de sélection ou n’importe où, à l’exception des poignées de redimensionnement.

1. Faites glisser la sélection vers son nouvel emplacement.

1. Pour ancrer la sélection dans l’image à son nouvel emplacement, sélectionnez à l’extérieur de la bordure de sélection.

Pour plus d’informations sur le dessin avec une sélection, consultez [création d’un pinceau personnalisé](./using-a-drawing-tool-image-editor-for-icons.md).

### <a name="to-flip-an-image"></a>Pour retourner une image

Vous pouvez retourner ou faire pivoter une image pour créer une image miroir de l’original, faire pivoter l’image ou la faire pivoter vers la droite de 90 degrés à la fois.

- Pour retourner l’image horizontalement (image miroir), accédez à **image**menu  >  **retourner horizontalement**.

- Pour retourner l’image verticalement (tourner à l’envers), accédez à menu **image**  >  **miroir verticale**.

- Pour faire pivoter l’image de 90 degrés, accédez à menu **image**  >  **rotation 90 degrés**.

   > [!NOTE]
   > Vous pouvez également utiliser les [touches accélérateur (raccourci)](../windows/accelerator-keys-image-editor-for-icons.md) pour ces commandes ou accéder aux commandes à partir du menu contextuel (sélectionnez à l’extérieur de l’image dans l' **éditeur d’images**).

### <a name="to-resize-an-image"></a>Pour redimensionner une image

Le comportement de l' **éditeur d’images** pendant le redimensionnement d’une image varie selon que vous avez [sélectionné](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) la totalité de l’image ou seulement une partie de celle-ci.

Lorsque la sélection comprend uniquement une partie de l’image, l' **éditeur d’images** réduit la sélection en supprimant des lignes ou des colonnes de pixels et en remplissant les régions libérées avec la couleur d’arrière-plan actuelle. Elle peut également étirer la sélection en dupliquant des lignes ou des colonnes de pixels.

Lorsque la sélection comprend la totalité de l’image, l' **éditeur d’images** réduit et étire l’image, ou la rogne et l’étend.

Il existe deux mécanismes pour redimensionner une image : les poignées de redimensionnement et le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Vous faites glisser les poignées de redimensionnement pour modifier la taille de tout ou partie d’une image. Les poignées de redimensionnement que vous pouvez faire glisser sont solides. Vous ne pouvez pas faire glisser des poignées qui sont vides. Utilisez la fenêtre **Propriétés** pour redimensionner l’intégralité de l’image, et non une partie sélectionnée.

![Poignées de dimensionnement d'une image bitmap](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")<br/>
Poignées de redimensionnement

> [!NOTE]
> Si vous avez sélectionné l’option **grille mosaïque** dans la [boîte de dialogue Paramètres](./image-editor-for-icons.md)de la grille, le redimensionnement s’aligne sur la ligne de grille mosaïque suivante. Si seule l’option **grille de pixels** est sélectionnée (paramètre par défaut), le redimensionnement s’aligne sur le pixel suivant disponible.

#### <a name="to-resize-an-entire-image-using-the-properties-window"></a>Pour redimensionner l’intégralité d’une image à l’aide de la fenêtre Propriétés

1. Ouvrez l’image dont vous souhaitez modifier les propriétés.

1. Dans les zones **largeur** et **hauteur** de la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), tapez les dimensions souhaitées.

   Si vous augmentez la taille de l’image, l' **éditeur d’images** étend l’image vers la droite, vers le bas, ou les deux, et remplit la nouvelle région avec la couleur d’arrière-plan actuelle. L’image n’est pas étirée.

   Si vous raccourcissez la taille de l’image, l' **éditeur d’images** rogne l’image sur le bord droit ou inférieur, ou les deux.

   > [!NOTE]
   > Vous pouvez utiliser les propriétés **Width** et **Height** pour redimensionner uniquement l’image entière, et non pour redimensionner une sélection partielle.

#### <a name="to-crop-or-extend-an-entire-image"></a>Pour rogner ou étendre une image entière

1. Sélectionnez l’image entière.

   Si une partie de l’image est actuellement sélectionnée et que vous souhaitez sélectionner la totalité de l’image, sélectionnez n’importe où sur l’image en dehors de la bordure de sélection actuelle.

1. Faites glisser une poignée de dimensionnement jusqu’à ce que l’image soit de la bonne taille.

Normalement, l' **éditeur d’images** rogne ou agrandit une image lorsque vous la redimensionnez en déplaçant une poignée de dimensionnement. Si vous maintenez la touche **MAJ** enfoncée pendant que vous déplacez une poignée de dimensionnement, l' **éditeur d’images** réduit ou étire l’image.

#### <a name="to-shrink-or-stretch-an-entire-image"></a>Pour réduire ou étirer l’intégralité d’une image

1. Sélectionnez l’image entière.

   Si une partie de l’image est actuellement sélectionnée et que vous souhaitez sélectionner la totalité de l’image, sélectionnez n’importe où sur l’image en dehors de la bordure de sélection actuelle.

1. Maintenez la touche **MAJ** enfoncée et faites glisser une poignée de redimensionnement jusqu’à ce que l’image soit de la bonne taille.

#### <a name="to-shrink-or-stretch-part-of-an-image"></a>Pour réduire ou étirer une partie d’une image

1. Sélectionnez la partie de l’image que vous souhaitez redimensionner. Pour plus d’informations, consultez [sélection d’une zone de l’image](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md).

1. Faites glisser l’une des poignées de redimensionnement jusqu’à ce que la sélection soit de la bonne taille.

### <a name="to-edit-an-image-outside-of-a-project"></a>Pour modifier une image en dehors d’un projet

Vous pouvez ouvrir et modifier des images dans l’environnement de développement comme vous le feriez dans n’importe quelle application graphique, par exemple en ouvrant une image bitmap pour une modification autonome. Les images que vous utilisez n’ont pas besoin de faire partie d’un projet Visual Studio.

1. Accédez à **fichier**menu  >  **ouvrir**.

1. Dans la zone **types de fichiers** , sélectionnez **tous les fichiers**.

1. Recherchez et ouvrez l’image que vous souhaitez modifier.

### <a name="to-change-image-properties"></a>Pour modifier les propriétés d’une image

Vous pouvez définir ou modifier les propriétés d’une image à l’aide de l' [fenêtre Propriétés](/visualstudio/ide/reference/properties-window).

1. Ouvrez l’image dans l' **éditeur d’images**.

1. Dans la fenêtre **Propriétés** , modifiez une ou toutes les propriétés de votre image.

   |Propriété|Description|
   |--------------|-----------------|
   |**Couleurs**|Spécifie le modèle de couleurs de l’image. Sélectionnez **monochrome**, **16**ou **256**, ou **couleurs vraies**.<br/><br/>Si vous avez déjà dessiné l’image avec une palette de 16 couleurs, la sélection de **monochrome** provoque des substitutions de noir et blanc pour les couleurs de l’image. Le contraste n’est pas toujours géré : par exemple, les zones adjacentes de rouge et de vert sont toutes deux converties en noir.|
   |**Nom du fichier**|Spécifie le nom du fichier image.<br/><br/>Par défaut, Visual Studio assigne un nom de fichier de base créé en supprimant les quatre premiers caractères (« IDB_ ») de l’identificateur de ressource par défaut (IDB_BITMAP1) et en ajoutant l’extension appropriée. Dans cet exemple, le nom de fichier de l’image serait *BITMAP1.bmp*. Vous pouvez le renommer *MYBITMAP1.bmp*.|
   |**Height**|Définit la hauteur de l’image (en pixels). La valeur par défaut est 48.<br/><br/>L’image est rognée ou un espace vide est ajouté sous l’image existante.|
   |**Identifiant**|Définit l’identificateur de la ressource.<br/><br/>Pour une image, Microsoft Visual Studio, par défaut, affecte l’identificateur disponible suivant dans une série : IDB_BITMAP1, IDB_BITMAP2, etc. Des noms similaires sont utilisés pour les icônes et les curseurs.|
   |**Palette**|Modifie les propriétés de couleur.<br/><br/>Double-cliquez pour sélectionner une couleur et afficher la [boîte de dialogue Sélecteur de couleurs personnalisées](./image-editor-for-icons.md). Définissez la couleur en tapant des valeurs RVB ou TSL dans les zones de texte appropriées.|
   |**SaveCompressed**|Indique si l’image est dans un format compressé. Cette propriété est en lecture seule.<br/><br/>Visual Studio ne vous permet pas d’enregistrer des images dans un format compressé. par conséquent, pour toutes les images créées dans Visual Studio, cette propriété a la **valeur false**. Si vous ouvrez une image compressée (créée dans un autre programme) dans Visual Studio, cette propriété a la **valeur true**. Si vous enregistrez une image compressée à l’aide de Visual Studio, elle sera décompressée et cette propriété reviendra à la **valeur false**.|
   |**Width**|Définit la largeur de l’image (en pixels). La valeur par défaut pour les bitmaps est 48.<br/><br/>L’image est rognée ou un espace vide est ajouté à droite de l’image existante.|

## <a name="requirements"></a>Configuration requise

Aucun

## <a name="see-also"></a>Voir aussi

[Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)<br/>
[Comment : créer une icône ou une autre image](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Comment : utiliser un outil de dessin](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[Comment : utiliser la couleur](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)<br/>

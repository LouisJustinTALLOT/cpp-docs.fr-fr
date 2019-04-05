---
title: 'Procédure : Modifier une Image'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.editing
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
ms.openlocfilehash: 849da0d14987a057d39d5f9531e97545b3d4b8cf
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033285"
---
# <a name="how-to-edit-an-image"></a>Procédure : Modifier une Image

Vous pouvez utiliser les outils de sélection pour définir une zone d’une image que vous souhaitez couper, copier, effacer, redimensionner, inverser ou déplacer. Avec le **sélection d’un Rectangle** outil, vous pouvez définir et sélectionner une zone rectangulaire de l’image. Avec le **Sélection irrégulière** outil que vous pouvez dessiner un contour à main levée de la zone que vous souhaitez sélectionner pour l’opérations couper, copier ou autre opération.

> [!NOTE]
> Consultez le **sélection d’un Rectangle** et **Sélection irrégulière** décrit dans la section outils [barre d’outils Éditeur d’images](../windows/toolbar-image-editor-for-icons.md) ou afficher l’info-bulles associées à chaque bouton sur le **Éditeur d’images** barre d’outils.

Vous pouvez également créer un pinceau personnalisé à partir d’une sélection. Pour plus d’informations, consultez [création d’un pinceau personnalisé](../windows/creating-a-custom-brush-image-editor-for-icons.md).

## <a name="how-to"></a>Comment

Pour modifier une image, consultez Comment :

### <a name="to-select-an-image"></a>Pour sélectionner une image

1. Utilisez le **Éditeur d’images** barre d’outils ou accédez au menu **Image** > **outils** et choisissez l’outil de sélection que vous souhaitez.

1. Déplacer le point d’insertion vers un coin de la zone d’image que vous souhaitez sélectionner. Croix s’affiche lorsque le point d’insertion se trouve sur l’image.

1. Faites glisser le point d’insertion vers le coin opposé de la zone que vous souhaitez sélectionner. Un rectangle montre les pixels qui seront sélectionnés. Tous les pixels dans le rectangle, y compris ceux sous le rectangle, sont inclus dans la sélection.

1. Relâchez le bouton de la souris. La bordure de sélection délimite la zone sélectionnée.

#### <a name="to-select-an-entire-image"></a>Pour sélectionner l’intégralité d’une image

Sélectionnez l’image en dehors de la sélection actuelle. La bordure de sélection met le focus et englobe l’image entière une fois encore.

### <a name="to-edit-parts-of-an-image"></a>Pour modifier des parties d’une image

Vous pouvez effectuer les opérations de modification standard — couper, copier, effacer et déplacement — sur un [sélection](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md), si la sélection est l’image entière ou uniquement une partie de celui-ci. Étant donné que le **Éditeur d’images** utilise le **Presse-papiers de Windows**, vous pouvez transférer des images entre le **Éditeur d’images** et d’autres applications pour Windows.

En outre, vous pouvez redimensionner la sélection, si elle inclut l’image entière ou seulement une partie.

#### <a name="to-cut-the-current-selection-and-move-it-to-the-clipboard"></a>Pour couper la sélection actuelle et déplacez-le vers le Presse-papiers

Accédez au menu **modifier** > **couper**.

#### <a name="to-copy-the-selection"></a>Pour copier la sélection

1. Placez le pointeur à l’intérieur de la bordure de sélection ou n’importe où sur celle-ci, sauf les poignées de redimensionnement.

1. Maintenez la **Ctrl** enfoncée quand vous faites glisser la sélection vers un nouvel emplacement. La zone de la sélection d’origine est inchangée.

1. Pour copier la sélection dans l’image à son emplacement actuel, sélectionnez en dehors du curseur de sélection.

#### <a name="to-paste-the-clipboard-contents-into-an-image"></a>Pour coller le contenu du Presse-papiers dans une image

1. Accédez au menu **modifier** > **coller**.

   Le contenu du Presse-papiers, entouré de la bordure de sélection, s’affichent dans le coin supérieur gauche du volet.

1. Placez le pointeur de la bordure de sélection et faites glisser l’image à l’emplacement souhaité sur l’image.

1. Pour ancrer l’image à son nouvel emplacement, sélectionnez en dehors de la bordure de sélection.

#### <a name="to-delete-the-current-selection-without-moving-it-to-the-clipboard"></a>Pour supprimer la sélection actuelle sans le déplacer dans le Presse-papiers

Accédez au menu **modifier** > **supprimer**.

   La zone d’origine de la sélection est remplie avec la couleur d’arrière-plan actuelle.

> [!NOTE]
> Vous pouvez accéder à la **couper**, **copie**, **coller**, et **supprimer** commandes par un clic droit dans le **affichagedesressources** fenêtre.

#### <a name="to-move-the-selection"></a>Pour déplacer la sélection

1. Placez le pointeur à l’intérieur de la bordure de sélection ou n’importe où sur celle-ci, sauf les poignées de redimensionnement.

1. Faites glisser la sélection vers son nouvel emplacement.

1. Pour ancrer la sélection dans l’image à son nouvel emplacement, sélectionnez en dehors de la bordure de sélection.

Pour plus d’informations sur le dessin avec une sélection, consultez [création d’un pinceau personnalisé](../windows/creating-a-custom-brush-image-editor-for-icons.md).

### <a name="to-flip-an-image"></a>Pour faire pivoter une image

Vous pouvez inverser ou faire pivoter une image pour créer une image miroir de l’original, retournez l’image ou faire pivoter l’image vers la droite de 90 degrés à la fois.

- Pour retourner l’image horizontalement (image miroir), accédez au menu **Image** > **retournement Horizontal**.

- Pour retourner l’image verticalement (renverser), accédez au menu **Image** > **retournement Vertical**.

- Pour faire pivoter l’image de 90 degrés, accédez au menu **Image** > **pivoter de 90 degrés**.

   > [!NOTE]
   > Vous pouvez également utiliser le [touches accélérateur (raccourci)](../windows/accelerator-keys-image-editor-for-icons.md) pour ces commandes ou accéder aux commandes dans le menu contextuel (sélectionnez hors de l’image lors de la **Éditeur d’images**).

### <a name="to-resize-an-image"></a>Pour redimensionner une image

Le comportement de la **Éditeur d’images** tandis que le redimensionnement d’une image varie selon que vous avez [sélectionné](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) l’image entière ou une partie.

Lorsque la sélection contient uniquement une partie de l’image, le **Éditeur d’images** réduit la sélection en supprimant des lignes ou des colonnes de pixels et en remplissant les régions libérées avec la couleur d’arrière-plan actuelle. Il permet également d’étendre la sélection en dupliquant des lignes ou des colonnes de pixels.

Lorsque la sélection inclut l’image entière, le **Éditeur d’images** soit réduit et étire l’image, ou les cultures et l’étend.

Il existe deux mécanismes pour redimensionner une image : les poignées de redimensionnement et la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Vous faites glisser les poignées de redimensionnement pour modifier la taille de tout ou partie d’une image. Les poignées de dimensionnement que vous pouvez faire glisser sont pleines. Vous ne pouvez pas faire glisser les poignées qui sont vides. Utilisez le **propriétés** fenêtre pour redimensionner l’intégralité de l’image uniquement, pas une partie sélectionnée.

![Dimensionnement des handles sur une image bitmap](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")<br/>
Poignées de redimensionnement

> [!NOTE]
> Si vous avez le **grille mosaïque** option sélectionnée dans le [boîte de dialogue Paramètres de la grille](../windows/grid-settings-dialog-box-image-editor-for-icons.md), puis redimensionnement s’aligne sur la ligne de grille mosaïque suivante. Si seul le **grille de pixels** option est sélectionnée (paramètre par défaut), redimensionnement s’aligne sur le pixel suivant.

#### <a name="to-resize-an-entire-image-using-the-properties-window"></a>Pour redimensionner l’intégralité d’une image à l’aide de la fenêtre Propriétés

1. Ouvrez l’image dont vous souhaitez modifier les propriétés.

1. Dans le **largeur** et **hauteur** zones dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), tapez les dimensions que vous souhaitez.

   Si vous augmentez la taille de l’image, le **Éditeur d’images** étend l’image vers la droite, vers le bas, ou les deux et remplit la nouvelle région avec la couleur d’arrière-plan actuelle. L’image n’est pas étiré.

   Si vous réduisez la taille de l’image, le **Éditeur d’images** rogne l’image sur le bord droit ou inférieur, ou les deux.

   > [!NOTE]
   > Vous pouvez utiliser la **largeur** et **hauteur** propriétés pour redimensionner l’image entière en ne pas pour une sélection partielle.

#### <a name="to-crop-or-extend-an-entire-image"></a>Pour rogner ou étendre l’intégralité d’une image

1. Sélectionnez l’image entière.

   Si la partie de l’image est actuellement sélectionnée et que vous souhaitez sélectionner l’image entière, sélectionnez n’importe où sur l’image en dehors de la bordure de sélection actuel.

1. Faites glisser une poignée de redimensionnement jusqu'à ce que l’image est la bonne taille.

Normalement, le **Éditeur d’images** rogne ou agrandit une image lors du redimensionnement en déplaçant une poignée de redimensionnement. Si vous maintenez le **MAJ** enfoncée quand vous déplacez une poignée de redimensionnement, la **Éditeur d’images** réduit ou étire l’image.

#### <a name="to-shrink-or-stretch-an-entire-image"></a>Pour réduire ou étirer l’intégralité d’une image

1. Sélectionnez l’image entière.

   Si une partie de l’image est actuellement sélectionnée et que vous souhaitez sélectionner l’image entière, sélectionnez n’importe où sur l’image en dehors de la bordure de sélection actuel.

1. Maintenez la **MAJ** de clé et faites glisser une poignée de redimensionnement jusqu'à ce que l’image est la bonne taille.

#### <a name="to-shrink-or-stretch-part-of-an-image"></a>Pour réduire ou étirer une partie d’une image

1. Sélectionnez la partie de l’image que vous voulez redimensionner. Pour plus d’informations, consultez [sélection d’une zone de l’Image](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md).

1. Faites glisser l’une des poignées de redimensionnement jusqu'à ce que la sélection est la bonne taille.

### <a name="to-edit-an-image-outside-of-a-project"></a>Pour modifier une image en dehors d’un projet

Vous pouvez ouvrir et modifier des images dans l’environnement de développement comme vous le feriez dans n’importe quelle application graphique, par exemple l’ouverture d’une image bitmap pour l’édition autonome. Les images que vous utilisez ne sont pas nécessairement partie d’un projet Visual Studio.

1. Accédez au menu **fichier** > **Open**.

1. Dans le **types de fichiers** boîte, sélectionnez **tous les fichiers**.

1. Recherchez et ouvrez l’image que vous souhaitez modifier.

### <a name="to-change-image-properties"></a>Pour modifier les propriétés de l’image

Vous pouvez définir ou modifier les propriétés d’une image à l’aide de la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window).

1. Ouvrir l’image dans le **Éditeur d’images**.

1. Dans le **propriétés** fenêtre, modifiez les propriétés de votre image.

   |Propriété|Description|
   |--------------|-----------------|
   |**Couleurs**|Spécifie le jeu de couleurs de l’image. Sélectionnez **Monochrome**, **16**, ou **256**, ou **couleurs vraies**.<br/><br/>Si vous avez déjà dessiné l’image avec une palette de couleurs-16, en sélectionnant **Monochrome** provoque des substitutions de noir et blanc pour les couleurs dans l’image. Contraste n’est pas toujours conservé : par exemple, les zones adjacentes rouge et verte sont converties en noir.|
   |**Nom de fichier**|Spécifie le nom du fichier image.<br/><br/>Par défaut, Visual Studio assigne un nom de fichier de base créé en supprimant les quatre premiers caractères (« IDB_ ») à partir de l’identificateur de ressource par défaut (IDB_BITMAP1) et en ajoutant l’extension appropriée. Le nom de fichier pour l’image dans cet exemple serait *BITMAP1.bmp*. Vous pouvez le renommer *MABITMAP1.bmp*.|
   |**Hauteur **|Définit la hauteur de l’image (en pixels). La valeur par défaut est 48.<br/><br/>L’image est rognée ou espace vide est ajouté en dessous de l’image existante.|
   |**Id**|Définit l’identificateur de ressource.<br/><br/>Pour une image, Microsoft Visual Studio, par défaut, attribue l’identificateur disponible suivant dans une série : IDB_BITMAP1, IDB_BITMAP2 et ainsi de suite. Des noms similaires sont utilisés pour les icônes et curseurs.|
   |**Palette**|Modifications des propriétés de couleur.<br/><br/>Double-clic pour sélectionner une couleur et afficher la [boîte de dialogue Sélecteur de couleurs personnalisées](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md). Définir la couleur en tapant des valeurs RVB ou TSL dans les zones de texte appropriées.|
   |**SaveCompressed**|Indique si l’image est dans un format compressé. Cette propriété est en lecture seule.<br/><br/>Visual Studio ne vous permet d’enregistrer des images dans un format compressé, donc pour toutes les images créées dans Visual Studio, cette propriété sera **False**. Si vous ouvrez une image compressée (créée dans un autre programme) dans Visual Studio, cette propriété sera **True**. Si vous enregistrez une image compressée à l’aide de Visual Studio, elle sera décompressée et cette propriété est rétablis au **False**.|
   |**Largeur**|Définit la largeur de l’image (en pixels). La valeur par défaut pour les bitmaps est 48.<br/><br/>L’image est rognée ou espace vide est ajouté à droite de l’image existante.|

## <a name="requirements"></a>Configuration requise

Aucun.

## <a name="see-also"></a>Voir aussi

[Éditeur d'images pour les icônes](../windows/image-editor-for-icons.md)<br/>
[Procédure : Créez une icône ou une autre Image](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Procédure : Utiliser un outil de dessin](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[Procédure : Utiliser des couleurs](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
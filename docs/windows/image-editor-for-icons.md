---
title: Éditeur d’images pour lesC++icônes ()
ms.date: 02/15/2019
f1_keywords:
- vc.editors.cursor.F1
- vc.editors.icon.F1
- vc.editors.cursor
- vc.editors.bitmap.F1
- vc.editors.bitmap
- vc.editors.dialog.GridSettings
- vc.editors.gridsettings
- vc.editors.bitmap
- vc.editors.icon
- vc.editors.texttool
- vc.editors.bitmap
- vc.editors.icon
helpviewer_keywords:
- editors, images
- resource editors [C++], graphics
- Image editor [C++]
- resource editors [C++], Image editor
- Image menu
- Grid Settings dialog box [C++]
- Graphics toolbar
- Image editor [C++], toolbar
- Image editor [C++], Option selector
- Properties window
- Option selector, Image editor
- toolbars [C++], showing
- toolbars [C++], hiding
- text, adding to an image
- Text Tool dialog box [C++]
- Text Tool Font dialog box [C++]
- fonts, changing on an image
- text, on images
- graphics editor [C++]
- Image editor [C++], panes
- Image editor [C++], magnification
- grids, pixel
- pixel grid, Image editor
- Image editor [C++], pixel grid
- Image editor [C++], grid settings
- grid settings, Image editor
ms.assetid: 586d2b8b-0348-4883-a85d-1ff0ddbf14dd
ms.openlocfilehash: 0f8fe228b804538b6a0d0377f05d79c34e787587
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514222"
---
# <a name="image-editor-for-icons-c"></a>Éditeur d’images pour lesC++icônes ()

Lorsque vous sélectionnez un fichier image (par exemple,. ico,. bmp,. png) dans **Explorateur de solutions**, l’image s’ouvre dans l' **éditeur d’images** de la même façon que les fichiers de code s’ouvrent dans l’éditeur de **code**. Quand un onglet **éditeur d’images** est actif, vous voyez des barres d’outils avec de nombreux outils pour la création et la modification d’images. Outre les bitmaps, les icônes et les curseurs, vous pouvez modifier des images au format GIF ou JPEG en utilisant les commandes du menu **image** et les outils de la barre d’outils de l' **éditeur d’images** .

Les ressources graphiques sont les images que vous définissez pour votre application. Vous pouvez dessiner à main levée ou dessiner à l’aide de formes. Vous pouvez sélectionner des parties d’une image à des fins de modification, de retournement ou de redimensionnement, ou vous pouvez créer un pinceau personnalisé à partir d’une partie sélectionnée d’une image et dessiner avec ce pinceau. Vous pouvez définir des propriétés d’image, enregistrer des images dans différents formats et convertir des images d’un format à un autre.

> [!NOTE]
> À l’aide de l' **éditeur d’images**, vous pouvez afficher des images 32 bits, mais vous ne pouvez pas les modifier.

Vous pouvez également utiliser l' **éditeur d’images** et l' [Éditeur binaire](binary-editor.md) pour travailler avec des fichiers de ressources dans des projets managés. Toutes les ressources managées que vous souhaitez modifier doivent être liées. Les éditeurs de ressources Visual Studio ne prennent pas en charge la modification des ressources incorporées.

Outre la création de nouvelles ressources graphiques, vous pouvez [importer des images existantes](../windows/how-to-copy-resources.md#import-and-export-resources) pour les modifier, puis les ajouter à votre projet. Vous pouvez également ouvrir et modifier des images qui ne font pas partie d’un projet pour la [modification d’images autonomes](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md).

Pour plus d’informations sur l' **éditeur d’images**, consultez Comment [créer une icône ou une autre image](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md), [modifier une image](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md), [utiliser un outil de dessin](../windows/using-a-drawing-tool-image-editor-for-icons.md), [travailler avec des couleurs](../windows/working-with-color-image-editor-for-icons.md)et des [touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md).

> [!NOTE]
> Téléchargez gratuitement la bibliothèque d' **images Visual Studio** qui contient de nombreux animations, bitmaps et icônes que vous pouvez utiliser dans vos applications. Pour plus d’informations sur le téléchargement de la bibliothèque, consultez la [bibliothèque d’images Visual Studio](/visualstudio/designers/the-visual-studio-image-library).

## <a name="image-menu"></a>Image, menu

Le menu **image** , qui s’affiche uniquement lorsque l' **éditeur d’images** est actif, contient des commandes pour modifier les images, gérer les palettes de couleurs et définir les options de la fenêtre de l’éditeur d' **images** . En outre, les commandes permettant d’utiliser des images d’appareil sont disponibles lorsque vous travaillez avec des icônes et des curseurs.

|Commande|Description|
|---|---|
|**Inverser les couleurs**|Inverse vos couleurs.|
|**Symétrie horizontale**|Retourne l'image ou la sélection horizontalement.|
|**Symétrie verticale**|Retourne l'image ou la sélection verticalement.|
|**Faire pivoter de 90 degrés**|Fait pivoter l'image ou la sélection de 90 degrés.|
|**Afficher la fenêtre des couleurs**|Ouvre la fenêtre **couleurs** , dans laquelle vous pouvez choisir les couleurs à utiliser pour votre image.|
|**Utiliser la sélection comme pinceau**|Vous permet de créer un pinceau personnalisé à partir d’une partie d’une image.<br/><br/>Votre sélection devient un pinceau personnalisé qui répartit les couleurs de la sélection sur l’image. Les copies de la sélection sont conservées le long du tracé de glissement. Plus le déplacement est lent, plus les copies sont effectuées.|
|**Copier et détourer la sélection**|Crée une copie de la sélection actuelle et met un contour.<br/><br/>Si la couleur d’arrière-plan est contenue dans la sélection actuelle, elle sera exclue si vous avez sélectionné transparent.
|**Ajuster les couleurs**|Ouvre le **Sélecteur de couleurs personnalisées**, qui vous permet de personnaliser les couleurs que vous utilisez pour votre image.|
|**Charger la palette**|Ouvre la boîte de dialogue **charger la palette de couleurs** , qui vous permet de charger les couleurs de la palette précédemment enregistrées dans un fichier. PAL.|
|**Enregistrer la palette**|Enregistre les couleurs de la palette dans un fichier. PAL.|
|**Dessin opaque**|Lorsque cette option est sélectionnée, la sélection actuelle est opaque.<br/><br/>Lorsque cette option est désactivée, la sélection actuelle est transparente.|
|**Éditeur de barres d’outils**|Ouvre la [boîte de dialogue nouvelle ressource de barre d’outils](../windows/new-toolbar-resource-dialog-box.md).|
|**Paramètres de la grille**|Ouvre la boîte de dialogue Paramètres de la **grille** dans laquelle vous pouvez spécifier des grilles pour votre image.|
|**Nouveau type d’image**|Ouvre la [boîte \<de dialogue nouveau type d’image de > d’appareil](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md).<br/><br/>Une seule ressource icône peut contenir plusieurs images de différentes tailles et les fenêtres peuvent utiliser la taille d’icône appropriée en fonction de l’affichage. Un nouveau type d’appareil ne modifie pas la taille de l’icône, mais crée plutôt une nouvelle image dans l’icône. S’applique uniquement aux icônes et aux curseurs.|
|**Type d’image icône/curseur actuel**|Ouvre un sous-menu qui répertorie les neuf premières images de curseur ou d’icône disponibles. La dernière commande du sous-menu, **plus**, ouvre la boîte de [dialogue Ouvrir \<l’image du > d’appareil](../windows/open-device-image-dialog-box-image-editor-for-icons.md).|
|**Supprimer le type d’image**|Supprime l’image d’appareil sélectionnée.|
|**Outils**|Lance un sous-menu qui contient tous les outils disponibles à partir de la barre d’outils de l' **éditeur d’images** .|

La boîte de dialogue Paramètres de la **grille** vous permet de spécifier les paramètres de grille pour votre image et d’afficher des quadrillages sur l’image modifiée. Les lignes sont utiles pour la modification de l’image, mais elles ne sont pas enregistrées dans le cadre de l’image elle-même.

|Propriété|Description|
|---|---|
|**Grille de pixels**|Lorsque cette option est activée, une grille apparaît autour de chaque pixel de l' **éditeur d’images**.<br/><br/>La grille s’affiche uniquement avec une résolution de 4 × et supérieure.|
|**Grille mosaïque**|Lorsqu’elle est sélectionnée, cette option affiche une grille autour des blocs de pixels dans l' **éditeur d’images**, spécifiée par les valeurs d’espacement de la grille.|
|**Width**|Spécifie la largeur de chaque bloc de mosaïques.<br/><br/>Cette propriété est utile lors du dessin de bitmaps contenant plusieurs images disposées à intervalles réguliers.|
|**Height**|Spécifie la hauteur de chaque bloc de mosaïques.<br/><br/>Cette propriété est utile lors du dessin de bitmaps contenant plusieurs images disposées à intervalles réguliers.|

## <a name="toolbar"></a>ToolBar

La barre d’outils de l' **éditeur d’images** contient des outils de dessin, de peinture, d’entrée de texte, d’effacement et de manipulation de vues. Il contient également un sélecteur d’options, avec lequel vous pouvez sélectionner des options pour utiliser chaque outil. Par exemple, vous pouvez choisir parmi différentes largeurs de pinceau, facteurs d’agrandissement et styles de ligne.

Tous les outils disponibles dans la barre d’outils de l' **éditeur d’images** sont également disponibles dans les**Outils**d' **image** > de menu. Pour utiliser la barre d’outils de l' **éditeur d’images** et le sélecteur d' **options** , sélectionnez l’outil ou l’option de votre choix.

![Barre d’outils Éditeur d’images](../mfc/media/vcimageeditortoolbar.gif "vcImageEditorToolbar")<br/>
Barre d’outils **éditeur d’images**

> [!TIP]
> Les info-bulles s’affichent lorsque vous placez le curseur sur un bouton de barre d’outils. Ces conseils peuvent vous aider à identifier la fonction de chaque bouton.

Étant donné que la plupart des outils de dessin sont disponibles à partir du [clavier](../windows/accelerator-keys-image-editor-for-icons.md), il est parfois utile de masquer la barre d’outils de l' **éditeur d’images** .

- Pour afficher ou masquer la barre d’outils de l' **éditeur d’images** , accédez à menu **Afficher** > les**barres d’outils** et choisissez **éditeur d’images**.

> [!NOTE]
> Les éléments de cette barre d’outils s’affichent non disponibles lorsqu’un fichier image du projet ou de la solution en cours n’est pas ouvert dans l' **éditeur d’images**.

### <a name="option-selector"></a>Option (sélecteur)

Le sélecteur d' **options** vous permet de spécifier la largeur d’une ligne, d’un trait de pinceau et bien plus encore. L’icône sur le bouton de sélection de l' **option** change en fonction de l’outil que vous avez sélectionné.

![Sélecteur&#45;de forme de dessin dans la barre d’outils de l’éditeur d’images](../mfc/media/vcimageeditortoolbaroptionselector.gif "vcImageEditorToolbarOptionSelector")<br/>
Sélecteur d' **option** dans la barre d’outils de l' **éditeur d’images**

### <a name="text-tool"></a>Outil texte

Utilisez la boîte de dialogue **outil texte** pour ajouter du texte à une ressource curseur, bitmap ou icône.

Pour accéder à cette boîte de dialogue, ouvrez l' **éditeur d’images** et accédez au menu**Outils**d' **image** > , puis sélectionnez la commande **outil texte** .

> [!TIP]
> Vous pouvez cliquer avec le bouton droit sur la boîte de dialogue **outil texte** pour accéder à un menu contextuel par défaut qui contient une liste de commandes Windows standard.

Ouvrez la boîte de dialogue police de l' **outil texte** pour modifier la police, le style ou la taille de la police du curseur. Les modifications sont appliquées au texte affiché dans la zone de **texte** .

Pour accéder à cette boîte de dialogue, sélectionnez le bouton **police** dans la boîte de dialogue **outil texte** . Les propriétés disponibles sont les suivantes:

|Propriété|Description|
|---|---|
|**Police**|Répertorie les polices disponibles.|
|**Style de police**|Répertorie les styles disponibles pour la police spécifiée.|
|**Taille**|Répertorie les tailles de points disponibles pour la police spécifiée.|
|**Exemple**|Montre un exemple de la façon dont le texte s’affiche avec les paramètres de police spécifiés.|
|**Script**|Répertorie les scripts de langue disponibles pour la police spécifiée.<br/><br/>Lorsque vous sélectionnez un autre script de langue, le jeu de caractères de cette langue devient disponible pour la création de documents multilingues.|

#### <a name="to-change-the-font-of-text-on-an-image"></a>Pour modifier la police du texte d’une image

Voici un exemple qui montre comment ajouter du texte à une icône dans une application Windows et comment manipuler la police de votre texte.

1. Créez une C++ application Windows Forms. Pour plus d’informations, consultez [Guide pratique pour Créer des applications](/previous-versions/visualstudio/visual-studio-2008/s69bf10x(v%3dvs.90))Windows Forms. Un fichier *app. ico* est ajouté à votre projet par défaut.

1. Dans **Explorateur de solutions**, double-cliquez sur le fichier *app. ico*. L' **éditeur d’images** s’ouvre.

1. Accédez à menu**Outils** d' **image** > et sélectionnez **outil texte**.

1. Dans la boîte de dialogue **outil texte** , *C++* tapez dans la zone de texte vide. Ce texte s’affiche dans une zone redimensionnable située dans l’angle supérieur gauche d' *app. ico* dans l' **éditeur d’images**.

1. Dans l' **éditeur d’images**, faites glisser la zone redimensionnable jusqu’au centre de *app. ico* pour améliorer la lisibilité de votre texte.

1. Dans la boîte de dialogue **outil texte** , sélectionnez le bouton **police** .

1. Dans la boîte de dialogue police de l' **outil texte** :

   - Sélectionnez **Times New Roman** dans la liste des polices disponibles qui sont répertoriées dans la zone de liste **police** .

   - Sélectionnez **gras** dans la liste des styles de police disponibles répertoriés dans la zone de liste **style de police** .

   - Sélectionnez **10** dans la liste des tailles de points disponibles répertoriées dans la zone de liste **taille** .

   - Cliquez sur **OK**. La boîte de dialogue police de l' **outil texte** se ferme et les nouveaux paramètres de police s’appliquent à votre texte.

1. Choisissez **Fermer** dans la boîte de dialogue **outil texte** . La zone redimensionnable autour de votre texte disparaît de l' **éditeur d’images**.

La zone de texte affiche le texte qui apparaît dans la ressource. Initialement, cette zone est vide.

> [!NOTE]
> Si l' **arrière-plan transparent** est défini, seul le texte est placé dans l’image. Si l' **arrière-plan opaque** est défini, un rectangle englobant, rempli avec la couleur d’arrière-plan, est placé derrière le texte.

## <a name="window-panes"></a>Volets de fenêtre

La fenêtre de l' **éditeur d’images** affiche deux vues d’une image, avec une barre de fractionnement qui sépare les deux volets. Vous pouvez faire glisser la barre de fractionnement pour modifier la taille des volets. Une bordure de sélection entoure le volet actif.

Une vue est la taille réelle et l’autre est agrandie par un facteur d’agrandissement par défaut de 6. Les affichages de ces deux volets sont mis à jour automatiquement, toutes les modifications que vous apportez dans un volet sont immédiatement affichées dans l’autre. Les deux volets vous permettent de travailler facilement sur une vue agrandie de votre image, dans laquelle vous pouvez distinguer des pixels individuels et, en même temps, observer l’effet de votre travail sur la vue de taille réelle de l’image.

Le volet gauche utilise autant d’espace que nécessaire (jusqu’à la moitié de la fenêtre **image** ) pour afficher la vue d’agrandissement 1:1 par défaut de votre image. Le volet droit affiche une image de zoom par défaut 6:1 Zoom. Vous pouvez modifier l’agrandissement dans chaque volet à l' aide de l’outil Loupe de la barre d’outils de l' **éditeur d’images** ou à l’aide des touches accélérateur.

Vous pouvez agrandir le plus petit volet de la fenêtre de l' **éditeur d’images** et utiliser les deux volets pour afficher différentes régions d’une grande image. Sélectionnez dans le volet pour le choisir.

Vous pouvez modifier les tailles relatives des volets en positionnant le pointeur sur la barre de fractionnement et en déplaçant la barre de fractionnement vers la droite ou la gauche. La barre de fractionnement peut être déplacée de chaque côté si vous souhaitez travailler sur un seul volet.

Si le volet de l' **éditeur d’images** est agrandi d’un facteur de 4 au plus, vous pouvez afficher une grille de pixels qui délimite les pixels individuels dans l’image.

### <a name="to-change-the-magnification-factor"></a>Pour modifier le facteur d’agrandissement

Par défaut, l' **éditeur d’images** affiche la vue dans le volet gauche à la taille réelle et la vue dans le volet droit à 6 fois la taille réelle. Le facteur d’agrandissement (visible dans la barre d’État en bas de l’espace de travail) est le rapport entre la taille réelle de l’image et la taille affichée. Le facteur par défaut est 6 et la plage est comprise entre 1 et 10.

1. Sélectionnez le volet de l' **éditeur d’images** dont vous souhaitez modifier le facteur d’agrandissement.

1. Dans la barre d’outils de l' **éditeur d’images** , sélectionnez la flèche à droite de l’outil **loupe** et sélectionnez le facteur d’agrandissement dans le sous-menu: **1x**, **2x**, **6**ou **8x**.

   > [!NOTE]
   > Pour sélectionner un facteur d’agrandissement différent de ceux listés dans l’outil loupe, utilisez les touches accélérateur.

### <a name="to-display-or-hide-the-pixel-grid"></a>Pour afficher ou masquer la grille de pixels

Pour tous les volets de l' **éditeur d’images** dont le facteur d’agrandissement est supérieur ou égal à 4, vous pouvez afficher une grille qui délimite les pixels individuels dans l’image.

1. Accédez au menu**paramètres de grille**de l' **image** > .

1. Activez la case à cocher **grille en pixels** pour afficher la grille, ou désactivez la case à cocher pour masquer la grille.

## <a name="requirements"></a>Configuration requise

Aucun

## <a name="see-also"></a>Voir aussi

[Éditeurs de ressources](../windows/resource-editors.md)<br/>
[Icônes](/windows/win32/menurc/icons)
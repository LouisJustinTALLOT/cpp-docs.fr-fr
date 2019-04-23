---
title: Éditeur d’images pour les icônes (C++)
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
ms.openlocfilehash: dd7da76d3df68fa63c87f64610524accfd4302ef
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041547"
---
# <a name="image-editor-for-icons-c"></a>Éditeur d’images pour les icônes (C++)

Lorsque vous sélectionnez un fichier image (par exemple, .ico, .bmp, .png) dans **l’Explorateur de solutions**, l’image s’ouvre dans le **Éditeur d’images** dans la même façon que vous ouvrent des fichiers de code dans le **éditeur de Code** . Quand un **Éditeur d’images** onglet est actif, vous voyez des barres d’outils avec de nombreux outils pour créer et modifier des images. En même temps que les bitmaps, icônes et curseurs, vous pouvez modifier des images au format GIF ou JPEG en utilisant les commandes le **Image** menu Outils et sur le **Éditeur d’images** barre d’outils.

Ressources graphiques sont les images que vous définissez pour votre application. Vous pouvez dessiner à main levée ou dessiner à l’aide de formes. Vous pouvez sélectionner des parties d’une image pour modification, la retourner ou la redimensionner, ou vous pouvez créer un pinceau personnalisé à partir d’une partie sélectionnée d’une image et dessiner avec ce pinceau. Vous pouvez définir les propriétés de l’image, enregistrer des images dans différents formats et convertir des images d’un format vers un autre.

> [!NOTE]
> À l’aide de la **Éditeur d’images**, vous pouvez afficher des images 32 bits, mais vous ne pouvez pas les modifier.

Vous pouvez également utiliser le **Éditeur d’images** et [éditeur binaire](binary-editor.md) pour travailler avec des fichiers de ressources dans les projets managés. Toutes les ressources managées que vous souhaitez modifier doivent être liées. Les éditeurs de ressources Visual Studio ne prennent pas en charge la modification des ressources incorporées.

Outre la création de nouvelles ressources graphiques, vous pouvez [importer des images existantes](../windows/how-to-copy-resources.md#import-and-export-resources) pour la modification, puis ajoutez-les à votre projet. Vous pouvez également ouvrir et modifier des images qui ne font pas partie d’un projet pour [modification d’image autonome](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md).

Pour plus d’informations sur la **Éditeur d’images**, consultez Comment [créer une icône ou une autre Image](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md), [modifier une Image](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md), [utiliser un outil de dessin](../windows/using-a-drawing-tool-image-editor-for-icons.md), [Utiliser des couleurs](../windows/working-with-color-image-editor-for-icons.md), et [touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md).

> [!NOTE]
> Télécharger gratuitement le **bibliothèque d’images Visual Studio** qui contient de nombreuses animations, bitmaps et icônes que vous pouvez utiliser dans vos applications. Pour plus d’informations sur la façon de télécharger la bibliothèque, consultez le [bibliothèque d’images Visual Studio](/visualstudio/designers/the-visual-studio-image-library).

## <a name="image-menu"></a>Image, menu

Le **Image** menu qui s’affiche uniquement lorsque le **Éditeur d’images** est actif, dispose de commandes pour modifier les images, la gestion des palettes de couleurs et la définition **Éditeur d’images** fenêtre Options. En outre, les commandes pour l’utilisation des images de périphérique sont disponibles lorsque vous travaillez avec des icônes et des curseurs.

|Commande|Description|
|---|---|
|**Couleurs inversées**|Inverse les couleurs.|
|**Symétrie horizontale**|Retourne l'image ou la sélection horizontalement.|
|**Symétrie verticale**|Retourne l'image ou la sélection verticalement.|
|**Faire pivoter de 90 degrés**|Fait pivoter l'image ou la sélection de 90 degrés.|
|**Afficher la fenêtre couleurs**|Ouvre le **couleurs** fenêtre, dans laquelle vous pouvez choisir les couleurs à utiliser pour votre image.|
|**Utiliser la sélection comme pinceau**|Vous permet de créer un pinceau personnalisé à partir d’une partie d’une image.<br/><br/>Votre sélection devient un pinceau personnalisé qui distribue les couleurs dans la sélection sur l’image. Copies de la sélection sont laissées sur le tracé de glissement. Vous faites glisser plus lentement, le nombre de copies est effectuées.|
|**Copie et sélection de la structure**|Crée une copie de la sélection actuelle et met un contour.<br/><br/>Si la couleur d’arrière-plan est contenue dans la sélection actuelle, celle-ci sera exclue si transparent est sélectionné.
|**Ajuster les couleurs**|Ouvre le **sélecteur de couleurs personnalisées**, qui vous permet de personnaliser les couleurs à utiliser pour votre image.|
|**Charger la Palette**|Ouvre le **charger la Palette de couleurs** boîte de dialogue qui vous permet de charger la palette de couleurs précédemment enregistré dans un fichier .pal.|
|**Enregistrer la Palette**|Enregistre la palette de couleurs d’un fichier .pal.|
|**Dessin Opaque**|Cette option convertit la sélection actuelle opaque.<br/><br/>Lorsqu’elle est désactivée, rend transparente la sélection actuelle.|
|**Éditeur de barres d’outils**|Ouvre le [boîte de dialogue Nouvelle ressource de barre d’outils](../windows/new-toolbar-resource-dialog-box.md).|
|**Paramètres de la grille**|Ouvre le **paramètres de la grille** boîte de dialogue dans laquelle vous pouvez spécifier des grilles pour votre image.|
|**Nouveau Type d’Image**|Ouvre le [New \<appareil > boîte de dialogue Type d’Image](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md).<br/><br/>Une ressource icône unique peut contenir plusieurs images de différentes tailles et windows puisse utiliser la taille d’icône appropriée en fonction de la façon dont elle va être affiché. Un nouveau type d’appareil ne modifie pas la taille de l’icône, mais crée une nouvelle image au sein de l’icône. S’applique uniquement aux icônes et des curseurs.|
|**Type d’Image icône/curseur actuel**|Ouvre un sous-menu qui répertorie les neuf premières disponibles images curseur ou icône. La dernière commande dans le sous-menu, **plus**, ouvre le [Open \<appareil > boîte de dialogue Image](../windows/open-device-image-dialog-box-image-editor-for-icons.md).|
|**Supprimer le Type d’Image**|Supprime l’image de périphérique sélectionné.|
|**Outils**|Lance un sous-menu contenant tous les outils disponibles à partir de la **Éditeur d’images** barre d’outils.|

Le **paramètres de la grille** boîte de dialogue vous permet de spécifier les paramètres de grille pour votre image et affiche les lignes de la grille sur l’image modifiée. Les lignes sont utiles pour la modification de l’image, mais ne sont pas enregistrées dans le cadre de l’image elle-même.

|Propriété|Description|
|---|---|
|**Grille de pixels**|Lorsqu’elle est activée, affiche une grille autour de chaque pixel de la **Éditeur d’images**.<br/><br/>La grille s’affiche uniquement 4 × et résolutions plus élevées.|
|**Grille mosaïque**|Sélectionné, affiche une grille autour des blocs de pixels dans le **Éditeur d’images**, spécifié par les valeurs d’espacement de grille.|
|**Width**|Spécifie la largeur de chaque bloc.<br/><br/>Cette propriété est utile lors du dessin de bitmaps qui contiennent plusieurs images sont organisées à intervalles réguliers.|
|**Height**|Spécifie la hauteur de chaque bloc.<br/><br/>Cette propriété est utile lors du dessin de bitmaps qui contiennent plusieurs images sont organisées à intervalles réguliers.|

## <a name="toolbar"></a>ToolBar

Le **Éditeur d’images** barre d’outils contient les outils de dessin, peinture, saisie de texte, effacer et manipulation des vues. Il contient également un sélecteur d’options, avec lequel vous pouvez sélectionner des options pour l’utilisation de chaque outil. Par exemple, vous pouvez choisir à partir de différentes largeurs de pinceau facteurs d’agrandissement et des styles de ligne.

Tous les outils disponibles sur le **Éditeur d’images** barre d’outils sont également disponibles dans le menu **Image** > **outils**. Pour utiliser le **Éditeur d’images** barre d’outils et **Option** sélecteur, sélectionnez l’outil ou l’option que vous souhaitez.

![Barre d’outils Éditeur d’images](../mfc/media/vcimageeditortoolbar.gif "vcImageEditorToolbar")<br/>
**Éditeur d’images** barre d’outils

> [!TIP]
> Info-bulles s’affichent lorsque vous placez votre curseur sur un bouton de barre d’outils. Ces conseils peuvent vous aider à identifier la fonction de chaque bouton.

Dans la mesure où la plupart des outils de dessin sont disponibles à partir de la [clavier](../windows/accelerator-keys-image-editor-for-icons.md), il est parfois utile de masquer la **Éditeur d’images** barre d’outils.

- Pour afficher ou masquer la **Éditeur d’images** barre d’outils, accédez au menu **vue** > **barres d’outils** et choisissez **Éditeur d’images**.

> [!NOTE]
> Éléments à partir de cette barre d’outils seront affiche pas disponibles quand un fichier image à partir du projet actuel ou la solution n’est pas ouverte dans le **Éditeur d’images**.

### <a name="option-selector"></a>Option (sélecteur)

Avec le **Option** sélecteur, vous pouvez spécifier la largeur d’une ligne, le trait de pinceau et bien plus encore. L’icône sur le **Option** sélecteur bouton change en fonction de l’outil que vous avez sélectionné.

![Dessin&#45;sélecteur de forme dans la barre d’outils Éditeur d’images](../mfc/media/vcimageeditortoolbaroptionselector.gif "vcImageEditorToolbarOptionSelector")<br/>
**Option** sélecteur sur le **Éditeur d’images** barre d’outils

### <a name="text-tool"></a>Outil texte

Utilisez le **outil texte** boîte de dialogue pour ajouter du texte à une ressource curseur, bitmap ou icône.

Pour accéder à cette boîte de dialogue, ouvrez le **Éditeur d’images** et accédez au menu **Image** > **outils**, puis sélectionnez le **outil texte** commande.

> [!TIP]
> Vous pouvez avec le bouton droit sur le **outil texte** boîte de dialogue pour accéder à un menu de raccourci par défaut qui contient une liste de commandes Windows standard.

Ouvrez le **police de l’outil texte** boîte de dialogue pour modifier la police, le style ou la taille de la police du curseur. Modifications sont appliquées au texte affiché dans le **texte** zone.

Pour accéder à cette boîte de dialogue, sélectionnez le **police** situé dans le **outil texte** boîte de dialogue. Les propriétés disponibles sont :

|Propriété|Description|
|---|---|
|**Police**|Répertorie les polices disponibles.|
|**Style de police**|Répertorie les styles disponibles pour la police spécifiée.|
|**Taille**|Répertorie les tailles disponibles pour la police spécifiée.|
|**Exemple**|Montre un exemple de comment le texte s’affiche avec les paramètres de police spécifiée.|
|**Script**|Répertorie les scripts de langue disponibles pour la police spécifiée.<br/><br/>Lorsque vous sélectionnez un script de langue différente, le jeu de caractères pour cette langue devient disponible pour la création de documents multilingues.|

#### <a name="to-change-the-font-of-text-on-an-image"></a>Pour modifier la police du texte d’une image

Voici un exemple montrant comment ajouter du texte à une icône dans une application Windows et de manipuler la police du texte.

1. Créez une Application de formulaires Windows de C++. Pour plus d’informations, consultez [Guide pratique pour Créer des Applications Windows Forms](/previous-versions/visualstudio/visual-studio-2008/s69bf10x(v%3dvs.90)). Un *app.ico* fichier est ajouté à votre projet par défaut.

1. Dans **l’Explorateur de solutions**, double-cliquez sur le fichier *app.ico*. Le **Éditeur d’images** s’ouvre.

1. Accédez au menu **Image** > **outils** et sélectionnez **outil texte**.

1. Dans le **outil texte** boîte de dialogue, tapez *C++* dans la zone de texte vide. Ce texte s’affiche dans une zone redimensionnable située dans le coin supérieur gauche de *app.ico* dans le **Éditeur d’images**.

1. Dans le **Éditeur d’images**, faites glisser la zone redimensionnable au centre du *app.ico* pour améliorer la lisibilité de votre texte.

1. Dans le **outil texte** boîte de dialogue, sélectionnez le **police** bouton.

1. Dans le **police de l’outil texte** boîte de dialogue :

   - Sélectionnez **Times New Roman** dans la liste des polices disponibles qui sont répertoriées dans le **police** zone de liste.

   - Sélectionnez **gras** dans la liste des styles de police disponibles répertoriées dans le **style de police** zone de liste.

   - Sélectionnez **10** à partir de la liste des disponibles point tailles répertoriées dans le **taille** zone de liste.

   - Cliquez sur **OK**. Le **police de l’outil texte** boîte de dialogue se ferme et les nouveaux paramètres de police s’appliquent à votre texte.

1. Choisissez **fermer** sur le **outil texte** boîte de dialogue. La zone redimensionnable autour du texte disparaît de la **Éditeur d’images**.

La zone de texte affiche le texte qui apparaît dans le cadre de la ressource. Initialement, cette zone est vide.

> [!NOTE]
> Si **arrière-plan Transparent** est défini, seul le texte sera placé dans l’image. Si **arrière-plan Opaque** est défini, un rectangle englobant, rempli avec la couleur d’arrière-plan, sera placé derrière le texte.

## <a name="window-panes"></a>Volets de fenêtre

Le **Éditeur d’images** fenêtre affiche deux vues d’une image, avec une barre sépare les deux volets de fractionnement. Vous pouvez faire glisser la barre de fractionnement pour modifier la taille des volets. Une bordure de sélection entoure le volet actif.

Une vue est la taille réelle et l’autre est agrandie par un facteur d’agrandissement par défaut de 6. Les vues dans ces deux volets sont mis à jour automatiquement, toute modification apportée dans un volet est immédiatement indiquées dans l’autre. Les deux volets facilitent vous permettent de travailler sur une vue agrandie de votre image, dans laquelle vous pouvez distinguer les pixels et, en même temps, observer l’effet de votre travail sur la vue de la taille réelle de l’image.

Le volet gauche utilise autant d’espace nécessaire (la moitié de la **Image** fenêtre) pour afficher la vue de facteur de zoom 1:1 par défaut de votre image. Le volet droit affiche une image de zoom du facteur d’agrandissement 6:1 par défaut. Vous pouvez modifier le facteur d’agrandissement dans chaque volet en utilisant le **Magnify** outil sur le **Éditeur d’images** barre d’outils ou en utilisant les touches accélérateur.

Vous pouvez agrandir le volet de plus petites de la **Éditeur d’images** fenêtre et utiliser les deux volets pour afficher différentes zones d’une grande image. Sélectionnez cette option dans le volet pour le choisir.

Vous pouvez modifier les tailles relatives des volets en plaçant le pointeur sur la barre de fractionnement et de déplacement de la barre de fractionnement vers la droite ou la gauche. La barre de fractionnement peut déplacer jusqu’au côté, si vous souhaitez travailler sur un seul volet.

Si le **Éditeur d’images** est agrandie par un facteur de 4 ou version ultérieure, vous pouvez afficher une grille de pixels qui délimite les pixels individuels dans l’image.

### <a name="to-change-the-magnification-factor"></a>Pour modifier le facteur d’agrandissement

Par défaut, le **Éditeur d’images** affiche la vue dans le volet de gauche en taille réelle et la vue dans le volet droit en taille réelle de 6 heures. Le facteur d’agrandissement (indiqué dans la barre d’état en bas de l’espace de travail) est le rapport entre la taille réelle de l’image et la taille affichée. Le facteur par défaut est 6 et la plage est comprise entre 1 et 10.

1. Sélectionnez le **Éditeur d’images** volet dont vous souhaitez modifier le facteur d’agrandissement.

1. Sur le **Éditeur d’images** barre d’outils, cliquez sur la flèche à droite de la **Magnify** outil et sélectionnez le facteur d’agrandissement dans le sous-menu : **1 X**, **2 X**, **6 X**, ou **8 X**.

   > [!NOTE]
   > Pour sélectionner un facteur d’agrandissement autre que ceux répertoriés dans le **Magnify** outil, utilisez les touches accélérateur.

### <a name="to-display-or-hide-the-pixel-grid"></a>Pour afficher ou masquer la grille de pixels

Pour toutes les **Éditeur d’images** volets avec un facteur d’agrandissement ou supérieure à 4, vous pouvez afficher une grille qui délimite les pixels individuels dans l’image.

1. Accédez au menu **Image** > **paramètres de la grille**.

1. Sélectionnez le **grille de pixels** case à cocher pour afficher la grille, ou désactivez la case pour masquer la grille.

## <a name="requirements"></a>Configuration requise

Aucun.

## <a name="see-also"></a>Voir aussi

[Éditeurs de ressources](../windows/resource-editors.md)<br/>

<!--[Icons](https://msdn.microsoft.com/library/windows/desktop/ms646973.aspx)-->
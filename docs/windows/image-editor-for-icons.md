---
title: Éditeur d'images pour les icônes
ms.date: 10/17/2018
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
ms.openlocfilehash: 48b363b7b9021042fe6242be70c74f0daeade0c2
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320703"
---
# <a name="image-editor-for-icons"></a>Éditeur d'images pour les icônes

Lorsque vous cliquez sur un fichier image (par exemple, .ico, .bmp, .png) dans l’Explorateur de solutions, l’image s’ouvre dans l’éditeur d’images de la même façon que les fichiers de code ouverts dans l’éditeur de Code. Lorsqu’un onglet de l’éditeur d’images est actif, vous voyez des barres d’outils avec de nombreux outils pour créer et modifier des images. En même temps que les bitmaps, icônes et curseurs, vous pouvez modifier des images au format GIF ou JPEG en utilisant les commandes le **Image** menu Outils et sur le **Éditeur d’images** barre d’outils.

Ressources graphiques sont les images que vous définissez pour votre application. Vous pouvez dessiner à main levée ou dessiner à l’aide de formes. Vous pouvez sélectionner des parties d’une image pour modification, la retourner ou la redimensionner, ou vous pouvez créer un pinceau personnalisé à partir d’une partie sélectionnée d’une image et dessiner avec ce pinceau. Vous pouvez définir les propriétés de l’image, enregistrer des images dans différents formats et convertir des images d’un format vers un autre.

Outre la création de nouvelles ressources graphiques, vous pouvez [importer des images existantes](../windows/how-to-import-and-export-resources.md) pour la modification, puis ajoutez-les à votre projet. Vous pouvez également ouvrir et modifier des images qui ne font pas partie d’un projet pour [modification d’image autonome](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md).

> [!NOTE]
> À l’aide de la **Éditeur d’images**, vous pouvez afficher des images 32 bits, mais vous ne pouvez pas les modifier.

Avec l'Éditeur d'images, vous pouvez :

- [Utiliser des couleurs](../windows/working-with-color-image-editor-for-icons.md)

- [Travailler avec des icônes et curseurs : Ressources d’images pour périphériques d’affichage](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)

- [Utiliser des touches accélérateur pour les commandes de l'Éditeur d'images](../windows/accelerator-keys-image-editor-for-icons.md)

Le **Éditeur d’images** fenêtre affiche deux vues d’une image, avec une barre sépare les deux volets de fractionnement. Vous pouvez faire glisser la barre de fractionnement pour modifier la taille des volets. Une bordure de sélection entoure le volet actif.

Le **Éditeur d’images** fenêtre peut être ajustée pour s’ajuster à vos besoins et préférences. Vous pouvez [modifier le facteur de zoom](../windows/changing-the-magnification-factor-image-editor-for-icons.md) et [afficher ou masquer la grille de pixels](../windows/displaying-or-hiding-the-pixel-grid-image-editor-for-icons.md).

> [!NOTE]
> À l’aide de la **Éditeur d’images**, vous pouvez afficher des images 32 bits, mais vous ne pouvez pas les modifier.

## <a name="image-menu"></a>Image, menu

Le **Image** menu qui s’affiche uniquement lorsque le **Image** éditeur est actif, qu’il dispose des commandes pour modifier les images, la gestion des palettes de couleurs et la définition **Éditeur d’images** fenêtre Options. En outre, les commandes pour l’utilisation des images de périphérique sont disponibles lorsque vous travaillez avec des icônes et des curseurs.

|Commande|Description|
|---|---|
|**Couleurs inversées**|Inverse les couleurs. Pour plus d’informations, consultez [inversion des couleurs dans une sélection](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md).|
|**Symétrie horizontale**|Retourne l'image ou la sélection horizontalement. Pour plus d’informations, consultez [retournement d’une Image](../windows/flipping-an-image-image-editor-for-icons.md).|
|**Symétrie verticale**|Retourne l'image ou la sélection verticalement. Pour plus d’informations, consultez [retournement d’une Image](../windows/flipping-an-image-image-editor-for-icons.md).|
|**Faire pivoter de 90 degrés**|Fait pivoter l'image ou la sélection de 90 degrés. Pour plus d’informations, consultez [retournement d’une Image](../windows/flipping-an-image-image-editor-for-icons.md).|
|**Afficher la fenêtre couleurs**|Ouvre le [fenêtre couleurs](../windows/colors-window-image-editor-for-icons.md), dans laquelle vous pouvez choisir les couleurs à utiliser pour votre image. Pour plus d’informations, consultez [utilisation des couleurs](../windows/working-with-color-image-editor-for-icons.md).|
|**Utiliser la sélection comme pinceau**|Vous permet de créer un pinceau personnalisé à partir d’une partie d’une image. Votre sélection devient un pinceau personnalisé qui distribue les couleurs dans la sélection sur l’image. Copies de la sélection sont laissées sur le tracé de glissement. Vous faites glisser plus lentement, le nombre de copies est effectuées. Pour plus d’informations, consultez [création d’un pinceau personnalisé](../windows/creating-a-custom-brush-image-editor-for-icons.md).|
|**Copie et sélection de la structure**|Crée une copie de la sélection actuelle et met un contour. Si la couleur d’arrière-plan est contenue dans la sélection actuelle, celle-ci sera exclue si vous avez [transparent](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md) sélectionné.
|**Ajuster les couleurs**|Ouvre le [sélecteur de couleurs personnalisées](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md), qui vous permet de personnaliser les couleurs à utiliser pour votre image. Pour plus d’informations, consultez [personnalisation ou modification des couleurs](../windows/customizing-or-changing-colors-image-editor-for-icons.md).|
|**Charger la Palette**|Ouvre le [boîte de dialogue Charger la Palette de couleurs](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md), ce qui vous permet de charger la palette de couleurs précédemment enregistré dans un fichier .pal.|
|**Enregistrer la Palette**|Enregistre la palette de couleurs d’un fichier .pal.|
|**Dessin Opaque**|Cette option convertit la sélection actuelle opaque. Lorsqu’elle est désactivée, rend transparente la sélection actuelle. Pour plus d’informations, consultez [en choisissant un arrière-plan Transparent ou Opaque](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).|
|**Éditeur de barres d’outils**|Ouvre le [boîte de dialogue Nouvelle ressource de barre d’outils](../windows/new-toolbar-resource-dialog-box.md).|
|**Paramètres de la grille**|Ouvre le **paramètres de la grille** boîte de dialogue dans laquelle vous pouvez spécifier des grilles pour votre image.|
|**Nouveau Type d’Image**|Ouvre le [New \<appareil > boîte de dialogue Type d’Image](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md). Une ressource icône unique peut contenir plusieurs images de différentes tailles et windows puisse utiliser la taille d’icône appropriée en fonction de la façon dont elle va être affiché. Un nouveau type d’appareil ne modifie pas la taille de l’icône, mais crée une nouvelle image au sein de l’icône. S’applique uniquement aux icônes et des curseurs.|
|**Type d’Image icône/curseur actuel**|Ouvre un sous-menu qui répertorie les premier curseur ou icône images disponibles (les neuf premières). La dernière commande dans le sous-menu, **plus...** , ouvre le [Open \<appareil > boîte de dialogue Image](../windows/open-device-image-dialog-box-image-editor-for-icons.md).|
|**Supprimer le Type d’Image**|Supprime l’image de périphérique sélectionné.|
|**Outils**|Lance un sous-menu contenant tous les outils disponibles à partir de la [barre d’outils Éditeur d’images](../windows/toolbar-image-editor-for-icons.md).|

Le **paramètres de la grille** boîte de dialogue vous permet de spécifier les paramètres de grille pour votre image et affiche les lignes de la grille sur l’image modifiée. Les lignes sont utiles pour la modification de l’image, mais ne sont pas enregistrées dans le cadre de l’image elle-même.

|Propriété|Description|
|---|---|
|**Grille de pixels**|Lorsqu’elle est activée, affiche une grille autour de chaque pixel dans l’éditeur d’images. La grille s’affiche uniquement 4 × et résolutions plus élevées.|
|**Grille mosaïque**|Lorsque sélectionné, affiche une grille autour des blocs de pixels dans l’éditeur d’images, spécifié par les valeurs d’espacement de grille.|
|**Width**|Spécifie la largeur de chaque bloc. Cette propriété est utile lors du dessin de bitmaps qui contiennent plusieurs images sont organisées à intervalles réguliers.|
|**Height**|Spécifie la hauteur de chaque bloc. Cette propriété est utile lors du dessin de bitmaps qui contiennent plusieurs images sont organisées à intervalles réguliers.|

## <a name="toolbar"></a>ToolBar

Le **Éditeur d’images** barre d’outils contient les outils de dessin, peinture, saisie de texte, effacer et manipulation des vues. Il contient également un sélecteur d’options, avec lequel vous pouvez sélectionner des options pour l’utilisation de chaque outil. Par exemple, vous pouvez choisir à partir de différentes largeurs de pinceau facteurs d’agrandissement et des styles de ligne.

> [!NOTE]
> Tous les outils disponibles sur le **Éditeur d’images** barre d’outils sont également disponibles à partir de la **Image** menu (sous le **outils** commande).

![Barre d’outils Éditeur d’images](../mfc/media/vcimageeditortoolbar.gif "vcImageEditorToolbar") barre d’outils Éditeur d’images

Pour utiliser le **Éditeur d’images** barre d’outils et **Option** sélecteur, sélectionnez l’outil ou l’option que vous souhaitez.

> [!TIP]
> Info-bulles s’affichent lorsque vous placez votre curseur sur un bouton de barre d’outils. Ces conseils peuvent vous aider à identifier la fonction de chaque bouton.

Avec le **Option** sélecteur, vous pouvez spécifier la largeur d’une ligne, le trait de pinceau et bien plus encore. L’icône sur le **Option** sélecteur bouton change en fonction de l’outil que vous avez sélectionné.

![Dessin&#45;sélecteur de forme dans la barre d’outils Éditeur d’images](../mfc/media/vcimageeditortoolbaroptionselector.gif "vcImageEditorToolbarOptionSelector") sélecteur d’options de la barre d’outils Éditeur d’images

### <a name="use-the-text-tool-dialog-box"></a>Utilisez la boîte de dialogue Outil texte

Utilisez le **outil texte** boîte de dialogue pour ajouter du texte à une ressource curseur, bitmap ou icône.

Pour accéder à cette boîte de dialogue, ouvrez le [Éditeur d’images](../windows/window-panes-image-editor-for-icons.md). Sélectionnez **outils** à partir de la **Image** menu, puis sélectionnez le **outil texte** commande.

#### <a name="font-button"></a>Bouton de police

Ouvre le **police de l’outil texte** boîte de dialogue, dans laquelle vous pouvez modifier la police, le style ou la taille de la police du curseur. Modifications sont appliquées au texte affiché dans le **texte** zone.

Pour accéder à cette boîte de dialogue, sélectionnez le **police** situé dans le **outil texte** boîte de dialogue. Les propriétés disponibles sont :

|Propriété|Description|
|---|---|
|**Police**|Répertorie les polices disponibles.|
|**Style de police**|Répertorie les styles disponibles pour la police spécifiée.|
|**Taille**|Répertorie les tailles disponibles pour la police spécifiée.|
|**Exemple**|Montre un exemple de comment le texte s’affiche avec les paramètres de police spécifiée.|
|**Script**|Répertorie les scripts de langue disponibles pour la police spécifiée. Lorsque vous sélectionnez un script de langue différente, le jeu de caractères pour cette langue devient disponible pour la création de documents multilingues.|

Pour modifier la police du texte sur une image :

La procédure suivante est un exemple montrant comment ajouter du texte à une icône dans une application Windows et de manipuler la police du texte.

1. Créez une Application de formulaires Windows de C++. Pour plus d’informations, consultez [création d’un projet d’Application Windows](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5). Un *app.ico* fichier est ajouté à votre projet par défaut.

1. Dans **l’Explorateur de solutions**, double-cliquez sur le fichier *app.ico*. Le [Éditeur d’images](../windows/image-editor-for-icons.md) s’ouvre.

1. À partir de la **Image** menu, sélectionnez **outils** , puis sélectionnez **outil texte**. Le **outil texte** boîte de dialogue s’affiche.

1. Dans le **outil texte** boîte de dialogue, tapez *C++* dans la zone de texte vide. Ce texte s’affiche dans une zone redimensionnable située dans le coin supérieur gauche de *app.ico*, dans le **Éditeur d’images**.

1. Dans le **Éditeur d’images**, faites glisser la zone redimensionnable au centre du fichier app.ico pour améliorer la lisibilité de votre texte.

1. Dans le **outil texte** boîte de dialogue, sélectionnez le **police** bouton. Le **police de l’outil texte** boîte de dialogue s’affiche.

1. Dans le **police de l’outil texte** boîte de dialogue, sélectionnez **Times New Roman** dans la liste des polices disponibles qui sont répertoriées dans le **police** zone de liste.

1. Sélectionnez **gras** dans la liste des styles de police disponibles répertoriées dans le **style de police** zone de liste.

1. Sélectionnez **10** à partir de la liste des disponibles point tailles répertoriées dans le **taille** zone de liste.

1. Sélectionnez le bouton **OK**. Le **police de l’outil texte** boîte de dialogue se ferme et les nouveaux paramètres de police s’appliquent à votre texte.

1. Sélectionnez le **fermer** bouton sur le **outil texte** boîte de dialogue. La zone redimensionnable autour du texte disparaît de la **Éditeur d’images**.

#### <a name="text-area"></a>Zone de texte

Affiche le texte qui apparaît dans le cadre de la ressource. Initialement, cette zone est vide.

> [!NOTE]
> Si **arrière-plan Transparent** est défini, seul le texte sera placé dans l’image. Si **arrière-plan Opaque** est défini, un rectangle englobant, rempli avec les [couleur d’arrière-plan](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md), seront placés derrière le texte. Pour plus d’informations, consultez [choix Opaque et arrière-plans transparents](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).

Vous pouvez avec le bouton droit sur le **outil texte** boîte de dialogue pour accéder à un menu de raccourci par défaut qui contient une liste de commandes Windows standard.

### <a name="to-display-or-hide-the-image-editor-toolbar"></a>Pour afficher ou masquer la barre d’outils Éditeur d’images

Dans la mesure où la plupart des outils de dessin sont disponibles à partir de la [clavier](../windows/accelerator-keys-image-editor-for-icons.md), il est parfois utile de masquer la **Éditeur d’images** barre d’outils.

Sur le **vue** menu, sélectionnez **barres d’outils** puis choisissez **Éditeur d’images**.

   > [!NOTE]
   > Éléments à partir de cette barre d’outils seront affiche pas disponibles quand un fichier image à partir du projet actuel ou la solution n’est pas ouverte dans le **Éditeur d’images**. Consultez [création d’une icône ou une autre Image](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md), pour plus d’informations sur l’ajout de fichiers image à vos projets.

## <a name="window-panes"></a>Volets de fenêtre

Le **Éditeur d’images** fenêtre affiche une image en général deux volets séparés par une barre de fractionnement. Une vue est la taille réelle et l’autre est agrandie (facteur d’agrandissement de la valeur par défaut est 6). Les vues dans ces deux volets sont mis à jour automatiquement : les modifications apportées dans un volet sont immédiatement répercutées dans l’autre. Les deux volets facilitent vous permettent de travailler sur une vue agrandie de votre image, dans laquelle vous pouvez distinguer les pixels et, en même temps, observer l’effet de votre travail sur la vue de la taille réelle de l’image.

Le volet gauche utilise autant d’espace nécessaire (la moitié de la **Image** fenêtre) pour afficher la vue 1:1 facteur d’agrandissement (il s’agit de la valeur par défaut) de votre image. Le volet droit affiche l’image agrandie (facteur d’agrandissement 6:1 par défaut). Vous pouvez modifier le facteur d’agrandissement dans chaque volet en utilisant le **Magnify** outil sur le [barre d’outils Éditeur d’images](../windows/toolbar-image-editor-for-icons.md) ou en utilisant les touches accélérateur.

Vous pouvez agrandir le volet de plus petites de la **Éditeur d’images** fenêtre et utiliser les deux volets pour afficher différentes zones d’une grande image. Sélectionnez cette option dans le volet pour le choisir.

Vous pouvez modifier les tailles relatives des volets en plaçant le pointeur sur la barre de fractionnement et de déplacement de la barre de fractionnement vers la droite ou la gauche. La barre de fractionnement peut déplacer jusqu’au côté, si vous souhaitez travailler sur un seul volet.

Si le **Éditeur d’images** est agrandie par un facteur de 4 ou version ultérieure, vous pouvez afficher une grille de pixels qui délimite les pixels individuels dans l’image.

### <a name="to-change-the-magnification-factor"></a>Pour modifier le facteur d’agrandissement

Par défaut, le **Image** éditeur affiche la vue dans le volet de gauche en taille réelle la vue dans le volet droit à 6 heures et taille réelle. Le facteur d’agrandissement (indiqué dans la barre d’état en bas de l’espace de travail) est le rapport entre la taille réelle de l’image et la taille affichée. Le facteur par défaut est 6 et la plage est comprise entre 1 et 10.

1. Sélectionnez le **Éditeur d’images** volet dont vous souhaitez modifier le facteur d’agrandissement.

1. Sur le [barre d’outils Éditeur d’images](../windows/toolbar-image-editor-for-icons.md), sélectionnez la flèche à droite de la [outil Loupe](../windows/toolbar-image-editor-for-icons.md) et sélectionnez le facteur d’agrandissement dans le sous-menu : **1 X**, **2 X**, **6 X**, ou **8 X**.

   > [!NOTE]
   > Pour sélectionner un facteur d’agrandissement autre que ceux répertoriés dans le **Magnify** outil, utilisez les touches accélérateur.

### <a name="to-display-or-hide-the-pixel-grid"></a>Pour afficher ou masquer la grille de pixels

Pour toutes les **Éditeur d’images** volets avec un facteur d’agrandissement ou supérieure à 4, vous pouvez afficher une grille qui délimite les pixels individuels dans l’image.

1. Sur le **Image** menu, sélectionnez **paramètres de la grille**.

1. Sélectionnez le **grille de pixels** case à cocher pour afficher la grille, ou désactivez la case pour masquer la grille.

> [!TIP]
> Info-bulles s’affichent lorsque vous placez votre curseur sur un bouton de barre d’outils. Ces conseils peuvent vous aider à identifier la fonction de chaque bouton.

## <a name="visual-studio-image-library"></a>Bibliothèque d'images Visual Studio

Vous pouvez télécharger gratuitement le **bibliothèque d’images Visual Studio** qui contient de nombreuses animations, bitmaps et icônes que vous pouvez utiliser dans vos applications. Pour plus d'informations sur le téléchargement de cette bibliothèque, consultez [Bibliothèque d'images Visual Studio](/visualstudio/designers/the-visual-studio-image-library).

## <a name="managed-resources"></a>Ressources managées

Vous pouvez utiliser la **Image** éditeur et le [éditeur binaire](binary-editor.md) pour travailler avec des fichiers de ressources dans les projets managés. Toutes les ressources managées que vous souhaitez modifier doivent être liées. Les éditeurs de ressources Visual Studio ne prennent pas en charge la modification des ressources incorporées.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Spécifications

Aucun.

## <a name="see-also"></a>Voir aussi

[Éditeurs de ressources](../windows/resource-editors.md)<br/>
[Icônes](https://msdn.microsoft.com/library/windows/desktop/ms646973.aspx)
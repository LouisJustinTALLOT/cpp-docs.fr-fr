---
title: 'Procédure : Utiliser des couleurs'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.color
- vc.editors.customcolorselector
- vc.editors.loadcolorpalette
- vc.editors.colorswindow
helpviewer_keywords:
- images [C++], background colors
- Image editor [C++], Colors Palette
- colors [C++], image
- Colors Palette, Image editor
- palettes, Image editor colors
- foreground colors [C++], Image editor
- colors [C++]
- Image editor [C++], colors
- colors [C++], Image editor
- colors [C++], image
- images [C++], colors
- Image editor [C++], colors
- Fill tool
- colors [C++], image
- images [C++], colors
- colors [C++], selection tools
- Image editor [C++], colors
- Select Color tool
- dithered color, Image editor
- Custom Color Selector dialog box [C++]
- Image editor [C++], Colors Palette
- colors [C++], image
- bitmaps [C++], colors
- images [C++], colors
- HSL values
- Colors Palette, Image editor
- RGB color values
- Adjust Colors command [C++]
- Image editor [C++], dithered color
- Image editor [C++], Colors Palette
- Colors Palette, Image editor
- colors [C++], inverting
- colors [C++]
- Color Indicator
- colors [C++], Colors window
- Colors window, hiding colors
- Show Colors Window command
- Colors window, displaying colors
- color palettes [C++]
- palettes
- palettes, Image editor
- colors [C++], Image editor
- Image editor [C++], palettes
- color palettes
- Load Palette Colors dialog box [C++]
- opaque backgrounds [C++]
- colors [C++], image
- Image editor [C++], transparent or opague backgrounds
- images [C++], transparency
- images [C++], opaque background
- colors [C++], image
- Image editor [C++], color inversion
- images [C++], colors
- colors [C++], inverting
ms.assetid: d34ff96f-241d-494f-abdd-13811ada8cd3
ms.openlocfilehash: f50d734ab35968aa107e23b8450d60f316b6002e
ms.sourcegitcommit: b4645761ce5acf8c2fc7a662334dd5a471ea976d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/07/2019
ms.locfileid: "57563145"
---
# <a name="how-to-work-with-color"></a>Procédure : Utiliser des couleurs

Le **Éditeur d’images** contient de nombreuses fonctionnalités qui permettent de gérer et personnaliser les couleurs. Vous pouvez définir une couleur de premier plan ou d’arrière-plan, couleur de remplissage des zones délimités ou sélectionnez une couleur dans une image à utiliser comme la couleur de premier plan ou d’arrière-plan actuelle. Vous pouvez utiliser les outils sur le [barre d’outils Éditeur d’images](../windows/toolbar-image-editor-for-icons.md) ainsi que de la palette de couleurs dans le **couleurs** fenêtre pour créer des images.

Toutes les couleurs pour les images monochromes et 16 couleurs sont affichées dans le **couleurs** palette dans la **couleurs** fenêtre. En même temps que 16 couleurs standard, vous pouvez créer vos propres couleurs personnalisées. La modification des couleurs dans la palette, change immédiatement la couleur correspondante dans l’image.

Lorsque vous travaillez avec l’icône de 256 couleurs et images de curseur, la **couleurs** propriété dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) est utilisé. Pour plus d’informations, consultez [création d’une icône de 256 couleurs ou d’un curseur](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md).

Couleurs vraies images peuvent également être créées. Toutefois, les échantillons de couleurs n’apparaissent pas dans la palette de la **couleurs** fenêtre ; ils apparaissent uniquement dans la zone d’indicateur de couleur de premier plan ou d’arrière-plan. Les couleurs vraies sont créées à l’aide de la **sélecteur de couleurs personnalisées** boîte de dialogue.

Vous pouvez enregistrer des palettes de couleurs personnalisées sur le disque et les recharger en fonction des besoins. La palette de couleurs que vous avez utilisé le plus récemment est enregistrée dans le Registre et chargée automatiquement la prochaine fois que vous démarrez Visual Studio.

Le **couleurs** fenêtre comporte deux parties :

- Le **Palette de couleurs**, qui est un tableau d’échantillons de couleurs qui représentent les couleurs que vous pouvez utiliser. Vous pouvez sélectionner les exemples pour choisir les couleurs de premier plan et arrière-plan lorsque vous utilisez les outils graphics.

- Le **indicateur de couleur**, qui affiche les couleurs de premier plan et d’arrière-plan et les sélecteurs pour l’écran et la couleur inversée.

   ![Fenêtre couleurs](../windows/media/vccolorswindow.gif "vcColorsWindow")<br/>
   **Couleurs** fenêtre

> [!NOTE]
> Le **écran couleur** et **couleur inversée** outils sont uniquement disponibles pour les icônes et curseurs.

Vous pouvez utiliser la **couleurs** fenêtre avec le [barre d’outils Éditeur d’images](../windows/toolbar-image-editor-for-icons.md).

- Pour afficher le **couleurs** fenêtre, avec le bouton droit dans une **Éditeur d’images** volet et choisissez **afficher la fenêtre des couleurs**, ou accédez au menu [Image](../windows/image-menu-image-editor-for-icons.md)  >  **Afficher la fenêtre des couleurs**.

- Pour masquer le **couleurs** fenêtre, désépingler la fenêtre (cette action autorise la fenêtre à masquage automatique lorsqu’il n’est pas en cours d’utilisation) ou sélectionnez le **fermer** bouton.

Le **couleurs** palette affiche initialement 16 couleurs standard. Avec les couleurs affichées, vous pouvez également créer vos propres couleurs personnalisées. Vous pouvez ensuite enregistrer et charger une palette de couleurs personnalisées.

Le **sélecteur de couleurs personnalisées** boîte de dialogue vous permet de personnaliser les couleurs à utiliser pour votre image avec les propriétés suivantes :

|Propriété|Description|
|--------------------------|--------------------------|
|**Affichage de la couleur de dégradé**|Modifie les valeurs de la couleur sélectionnée.<br/><br/>Positionner la croix sur la couleur que vous souhaitez modifier et déplacez le curseur vers le haut ou vers le bas pour modifier la luminosité ou les valeurs RVB de la couleur.|
|**Barre de luminosité**|Définit la luminosité de la couleur que vous sélectionnez dans la **affichage des dégradés de couleur** boîte.<br/><br/>Sélectionnez et faites glisser la flèche blanche de la barre de luminosité supérieure ou vers le bas à moindre coût. Le **couleur** zone affiche la couleur que vous avez sélectionné et l’effet de la luminosité que vous définissez.|
|**Color**|Répertorie la teinte (valeur de roue de couleur) de la couleur que vous définissez. Les valeurs comprises entre 0 et 240, où 0 est rouge, 60 est jaune, 120 est vert, 180 est cyan, 200 est magenta et 240 est bleu.|
|**HUE**|Répertorie la teinte (valeur de roue de couleur) de la couleur que vous définissez. Les valeurs comprises entre 0 et 240, où 0 est rouge, 60 est jaune, 120 est vert, 180 est cyan, 200 est magenta et 240 est bleu.|
|**Sat**|Spécifie la valeur de saturation de la couleur que vous définissez. Saturation correspond à la quantité de couleur dans une teinte spécifiée. Les valeurs comprises entre 0 et 240.|
|**Lum**|Répertorie la luminosité de la couleur que vous définissez. Les valeurs comprises entre 0 et 240.|
|**Rouge**|Spécifie la valeur rouge de la couleur que vous définissez. Les valeurs comprises entre 0 et 255.|
|**Vert**|Spécifie la valeur verte de la couleur que vous définissez. Les valeurs comprises entre 0 et 255.|
|**Blue**|Spécifie la valeur bleue de la couleur que vous définissez. Les valeurs comprises entre 0 et 255.|

Vous pouvez enregistrer et charger un **couleurs** palette qui contient des couleurs personnalisées. Par défaut, le **couleurs** palette plus récemment utilisée est automatiquement chargé lorsque vous démarrez Visual Studio.

> [!TIP]
> Dans la mesure où le **Éditeur d’images** n’a aucun moyen de rétablir la valeur par défaut **couleurs** palette, vous devez enregistrer la valeur par défaut **couleurs** palette sous un nom tel que  *standard.PAL* ou *defaut.PAL* afin que vous pouvez facilement restaurer les paramètres par défaut.

Utiliser le **charger les couleurs de Palette** boîte de dialogue pour charger des palettes de couleurs spécial à utiliser dans votre projet C++ avec les propriétés suivantes :

|Propriété|Description|
|-----------------|-----------------|
|**Regarder dans**|Spécifie l’emplacement où vous souhaitez localiser un fichier ou dossier.<br/><br/>Sélectionnez la flèche pour choisir un autre emplacement, ou sélectionnez l’icône de dossier dans la barre d’outils pour déplacer les niveaux.|
|**Nom de fichier**|Offre un espace vous permettant de taper le nom du fichier que vous souhaitez ouvrir.<br/><br/>Pour trouver rapidement un fichier que vous avez déjà ouvert, sélectionnez le nom de fichier dans la liste déroulante, si elle est disponible.<br/><br/>Si vous recherchez un fichier, vous pouvez utiliser des astérisques (*) comme caractères génériques. Par exemple, vous pouvez taper \*.\* pour afficher la liste de tous les fichiers. Vous pouvez également taper le chemin d’accès complet d’un fichier, par exemple, *Documents\MyColorPalette.PAL C:\My* ou  *\\\NetworkServer\MyFolder\MyColorPalette.pal*.|
|**Types de fichiers**|Répertorie les types de fichiers à afficher.<br/><br/>Palette (* .pal) est le type de fichier par défaut pour les palettes de couleurs.|

## <a name="how-to"></a>Comment

### <a name="to-select-foreground-or-background-colors"></a>Pour sélectionner des couleurs de premier plan ou arrière-plan

À l’exception de la **gomme**, les outils sur le **Éditeur d’images** draw de barre d’outils avec la couleur de premier plan ou d’arrière-plan actuelle lorsque vous appuyez sur le bouton gauche ou droit de la souris, respectivement.

- Pour sélectionner une couleur de premier plan, avec le bouton gauche de la souris, sélectionnez la couleur voulue sur la **couleurs** palette.

- Pour sélectionner une couleur d’arrière-plan, avec le bouton droit de la souris, sélectionnez la couleur voulue sur la **couleurs** palette.

### <a name="to-fill-a-bounded-area-of-an-image-with-a-color"></a>Pour remplir une zone délimitée d’une image avec une couleur

Le **Éditeur d’images** fournit le **remplir** outil pour remplir les placée entre la zone d’image avec la couleur de dessin actuelle ou la couleur d’arrière-plan actuelle.

### <a name="to-use-the-fill-tool"></a>Pour utiliser l’outil remplissage

1. Utilisez le **Éditeur d’images** barre d’outils ou accédez au menu **Image** > **outils** et sélectionnez le **remplir** outil.

1. Si nécessaire, choisissez les couleurs de dessin. Dans le [palette de couleurs](../windows/colors-window-image-editor-for-icons.md), sélectionnez le bouton gauche de la souris pour sélectionner une couleur de premier plan ou le bouton droit de la souris pour sélectionner une couleur d’arrière-plan.

1. Déplacer le **remplissage** outil à la zone à remplir.

1. Sélectionnez le bouton gauche ou droit de la souris à remplir avec la couleur de premier plan ou la couleur d’arrière-plan, respectivement.

### <a name="to-pick-up-a-color-from-an-image-to-use-elsewhere"></a>Pour sélectionner une couleur à partir d’une image à utiliser ailleurs

Le **sélectionner une couleur**, ou de la sélection de couleur, outil transforme la couleur de l’image de la couleur de premier plan actuelle ou la couleur d’arrière-plan, selon si vous appuyez sur la gauche ou sur le bouton droit de la souris. Pour annuler le **sélectionner une couleur** outil, choisissez un autre outil.

1. Utilisez le **Éditeur d’images** barre d’outils ou accédez au menu **Image** > **outils** et sélectionnez le **sélectionner une couleur** outil.

1. Sélectionnez la couleur que vous souhaitez récupérer à partir de l’image.

   > [!NOTE]
   > Après avoir sélectionné une couleur, le **Éditeur d’images** réactivé utilisés le plus récemment outil.

1. Dessiner à l’aide du bouton gauche de la souris pour la couleur de premier plan, ou le bouton droit de la souris pour la couleur d’arrière-plan.

### <a name="to-choose-the-background"></a>Pour choisir l’arrière-plan

Lorsque vous déplacez ou copiez une sélection d’une image, les pixels de la sélection qui correspondent à la couleur d’arrière-plan actuelle sont, par défaut, transparent et ils n’assombrissent pas pixels dans l’emplacement cible.

Vous pouvez passer d’un arrière-plan transparent (la valeur par défaut) à un arrière-plan opaque et inversement. Lorsque vous utilisez un outil de sélection, le **arrière-plan Transparent** et **arrière-plan Opaque** options s’affichent dans le **Option** sélecteur sur le **Éditeur d’images** barre d’outils.

![Options d’arrière-plan &#45; opaque ou transparent](../windows/media/vcimageeditoropaqtranspback.gif "options d’arrière-plan &#45; opaque ou transparent")<br/>
**Options transparentes et opaques** sur la **barre d’outils Éditeur d’images**

#### <a name="to-switch-between-a-transparent-and-opaque-background"></a>Pour basculer entre un arrière-plan transparent et opaque

Dans le **Éditeur d’images** barre d’outils, sélectionnez le **Option** sélecteur, puis choisissez l’arrière-plan approprié :

- **Arrière-plan opaque (O)**: Image existante est obscurcie par toutes les parties de la sélection.

- **Arrière-plan transparent (T)**: Illustration existant par le biais de la sélection des parties qui correspondent à la couleur d’arrière-plan actuelle.

> [!TIP]
> Pour créer un raccourci, sur le **Image** menu, cochez ou décochez **dessin Opaque**.

Vous pouvez modifier la couleur d’arrière-plan alors qu’une sélection est déjà en vigueur pour modifier les parties de l’image sont transparents.

### <a name="to-invert-the-colors-in-a-selection"></a>Pour inverser les couleurs dans une sélection

Le **Éditeur d’images** fournit un moyen pratique d’inverser les couleurs dans la partie sélectionnée de l’image afin de savoir comment une image apparaît avec des couleurs inversées.

Pour inverser les couleurs dans la sélection actuelle, accédez au menu **Image** > **inverser les couleurs**.

### <a name="to-customize-or-change-colors-on-the-colors-palette"></a>Pour personnaliser ou modifier les couleurs de la palette de couleurs

1. Accédez au menu **Image** > **ajuster les couleurs**.

1. Dans le **sélecteur de couleurs personnalisées** boîte de dialogue zone, définir la couleur en tapant des valeurs RVB ou TSL dans les zones appropriées ou choisissez une couleur dans le **affichage des dégradés de couleur** boîte.

1. Définissez la luminosité en déplaçant le curseur le **luminosité** barre.

1. De nombreuses couleurs personnalisées sont tramées. Si vous souhaitez la couleur unie la plus proche de la couleur tramée, double-cliquez sur le **couleur** boîte.

   Si vous décidez plus tard vous voulez que la couleur tramée, déplacez le curseur le **luminosité** à barres ou déplacez le réticule le **affichage des dégradés de couleur** boîte afin de rétablir le dégradé.

1. Sélectionnez **OK** pour ajouter la nouvelle couleur.

### <a name="to-save-a-custom-colors-palette"></a>Pour enregistrer une palette de couleurs personnalisées

1. Accédez au menu **Image** > **enregistrer la Palette**.

1. Accédez au répertoire où vous souhaitez enregistrer la palette, puis tapez le nom de cette dernière.

1. Sélectionnez **Enregistrer**.

### <a name="to-load-a-custom-colors-palette"></a>Pour charger une palette de couleurs personnalisées

1. Accédez au menu **Image** > **charger la Palette**.

1. Dans le **charger la Palette de couleurs** boîte de dialogue zone, accédez au répertoire approprié et sélectionnez la palette à charger. **Couleur** palettes sont enregistrés avec une extension de fichier .pal.

## <a name="requirements"></a>Spécifications

Aucun.

## <a name="see-also"></a>Voir aussi

[Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)<br/>
[Guide pratique pour créer une icône ou une autre image](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Guide pratique pour modifier une image](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Guide pratique pour utiliser un outil de dessin](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)<br/>

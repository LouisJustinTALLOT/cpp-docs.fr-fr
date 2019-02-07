---
title: 'Icônes et curseurs : Ressources d’images pour périphériques d’affichage (Éditeur d’images C++ pour les icônes)'
ms.date: 11/04/2016
f1_keywords:
- vc.editors.icon
- vc.editors.newimagetype
- vc.editors.customimage
- vc.editors.opendeviceimage
- vc.editors.image.editing
helpviewer_keywords:
- cursors [C++], creating
- image resources [C++], display devices
- icons [C++], creating
- cursors [C++], types
- icons [C++]
- Image editor [C++], icons and cursors
- cursors [C++]
- display devices [C++], creating icons for
- cursors [C++], hot spots
- icons [C++], types
- icons [C++], creating
- display devices [C++], creating image
- images [C++], creating for display devices
- icons [C++], inserting
- New <Device> Image Type dialog box [C++]
- Custom Image dialog box [C++]
- Open <Device> Image dialog box [C++]
- New Device Image command
- display devices [C++], adding images
- cursors [C++], adding
- icons, adding
- display devices [C++], copying images
- cursors [C++], copying
- icons, copying
- cursors [C++], deleting
- display devices [C++], deleting device image
- icons, erasing
- icons, deleting
- cursors [C++], undoing changes
- icons, undoing changes
- cursors [C++], screen regions
- inverse colors [C++], device images
- transparent regions, device images
- transparency, device images
- Image editor [C++], device images
- inverse regions, device images
- cursors [C++], transparent regions
- screen colors
- regions, transparent
- icons [C++], transparent regions
- display devices [C++], transparent and screen regions
- transparent regions in devices
- regions, inverse
- colors [C++], Image editor
- device projects [C++], transparent images
- icons [C++], screen regions
- 256-color palette
- cursors [C++], color
- colors [C++], icons
- colors [C++], cursors
- icons, color
- colors [C++], icons and cursors
- color palettes, 256-color
- palettes, 256-color
- cursors [C++], hot spots
- hot spots
ms.assetid: 8f0809a8-0cf0-4da9-b23d-51f28bf15f5b
ms.openlocfilehash: 027c3c0380a73c624432bbe45758b3296732949a
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849943"
---
# <a name="icons-and-cursors-image-resources-for-display-devices-c-image-editor-for-icons"></a>Icônes et curseurs : Ressources d’images pour périphériques d’affichage (Éditeur d’images C++ pour les icônes)

Les icônes et curseurs sont des ressources graphiques qui peuvent contenir plusieurs images de différentes tailles et modèles de couleurs pour différents types de périphériques d’affichage. En outre, un curseur a une « zone réactive, « l’emplacement utilisé par Windows pour effectuer le suivi de sa position. Icônes et curseurs sont créés et modifiés à l’aide du **Image** éditeur, comme les bitmaps et autres images.

Lorsque vous créez une nouvelle icône ou curseur, la **Image** éditeur crée d’abord une image d’un type standard. Cette image est remplie initialement avec la couleur d’écran (transparente). Si l’image est un curseur, la zone réactive est initialement le coin supérieur gauche (coordonnées 0,0).

Par défaut, le **Image** éditeur prend en charge la création d’images supplémentaires pour les périphériques répertoriés dans le tableau suivant. Vous pouvez créer des images pour d’autres périphériques en tapant les paramètres de hauteur, largeur et nombre de couleurs dans la boîte de dialogue [Image personnalisée](custom-image-dialog-box-image-editor-for-icons.md).

> [!NOTE]
> À l’aide de la **Éditeur d’images**, vous pouvez afficher des images 32 bits, mais vous ne pouvez pas les modifier.

|Color|Largeur (pixels)|Hauteur (pixels)|
|-----------|----------------------|-----------------------|
|Monochrome|16|16|
|Monochrome|32|32|
|Monochrome|48|48|
|Monochrome|64|64|
|Monochrome|96|96|
|16|16|16|
|16|32|32|
|16|64|64|
|16|48|48|
|16|96|96|
|256|16|16|
|256|32|32|
|256|48|48|
|256|64|64|
|256|96|96|

## <a name="create-a-device-image-icon-or-cursor"></a>Créer une image de périphérique (icône ou curseur)

Lorsque vous créez une nouvelle icône ou une ressource du curseur, la **Image** éditeur crée d’abord une image dans un style spécifique (32 x 32, 16 couleurs pour les icônes et 32 x 32, Monochrome pour les curseurs). Vous pouvez ensuite ajouter des images de différentes tailles et les styles à l’icône d’origine et modifier chaque image supplémentaire, en fonction des besoins, pour les périphériques d’affichage différent. Vous pouvez également modifier une image à l’aide d’une opération de couper-coller à partir d’un type d’image existant ou d’une bitmap créée dans un programme graphique.

Lorsque vous ouvrez la ressource icône ou curseur dans le [Éditeur d’images](../windows/image-editor-for-icons.md), l’image de la plupart des étroitement le périphérique d’affichage actuel est ouverte par défaut.

### <a name="new-ltdevicegt-image-type-dialog-box"></a>Nouvelle &lt;appareil&gt; boîte de dialogue Type d’Image

Le **New &lt;appareil&gt; Type d’Image** boîte de dialogue vous permet de créer une nouvelle image de périphérique d’un type spécifié. Pour ouvrir le **New \<appareil > Image** boîte de dialogue, sélectionnez **nouveau Type d’Image** sur le **Image** menu. Les propriétés suivantes incluses sont **Type d’Image cible** et **personnalisé**.

#### <a name="target-image-type"></a>Type d’Image cible

Répertorie les types d’images disponibles. Sélectionnez le type d’image que vous souhaitez ouvrir :

||||
|-|-|-|
|-16 x 16, 16 couleurs|-48 x 48, 16 couleurs|-96 x 96, 16 couleurs|
|-16 x 16, 256 couleurs|-48 x 48, 256 couleurs|-96 x 96, 256 couleurs|
|-16 x 16, Monochrome|-48 x 48, Monochrome|- 96 x 96, Monochrome|
|-32 x 32, 16 couleurs|-64 x 64, 16 couleurs||
|-32 x 32, 256 couleurs|-64 x 64, 256 couleurs||
|-32 x 32, Monochrome|-64 x 64, Monochrome||

> [!NOTE]
> Toutes les images existantes seront affichera pas dans cette liste.

#### <a name="custom"></a>Personnalisé

Ouvre le **Image personnalisée** boîte de dialogue dans laquelle vous pouvez créer une nouvelle image avec une taille personnalisée et le nombre de couleurs.

Le **Image personnalisée** boîte de dialogue vous permet de créer une nouvelle image avec une taille personnalisée et le nombre de couleurs. Les propriétés suivantes incluses sont :

|Propriété|Description|
|---|---|
|**Width**|Fournit un espace vous permettant d’entrer la largeur de l’image personnalisée en pixels (1-512, limite de 2048).|
|**Height**|Fournit un espace vous permettant d’entrer la hauteur de l’image personnalisée en pixels (1-512, limite de 2048).|
|**Couleurs**|Fournit un espace vous permettant de choisir le nombre de couleurs pour l’image personnalisée : 2, 16 ou 256.|

### <a name="open-ltdevicegt-image-dialog-box"></a>Ouvrez &lt;appareil&gt; Image boîte de dialogue

Utilisez le **ouvrir &lt;appareil&gt; Image** boîte de dialogue pour ouvrir des images de périphérique dans les projets C++. Il répertorie les images de périphérique existantes dans la ressource actuelle (les images qui font partie de la ressource actuelle). La propriété suivante incluse est :

|Propriété|Description|
|---|---|
|**Images actuelles**|Répertorie les images incluses dans la ressource. Sélectionnez le type d’image que vous souhaitez ouvrir.|

### <a name="to-create-a-new-icon-or-cursor"></a>Pour créer une nouvelle icône ou curseur

1. Dans [affichage des ressources](../windows/resource-view-window.md), avec le bouton droit de votre fichier .rc, puis choisissez **insérer la ressource** dans le menu contextuel. (Si vous disposez déjà d’une ressource image dans votre fichier .rc, par exemple un curseur, vous pouvez cliquer sur le **curseur** dossier et sélectionnez **insérer Cursor** dans le menu contextuel.)

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [création d’un fichier de Script de ressources](../windows/how-to-create-a-resource-script-file.md).

1. Dans le [boîte de dialogue Ajouter une ressource](../windows/add-resource-dialog-box.md), sélectionnez **icône** ou **curseur** et choisissez **New**. Pour les icônes, cette action crée une ressource icône 16 couleurs, 32 x 32. Pour les curseurs, 32 x 32, Monochrome image (2-color) est créé.

   Si un signe plus (**+**) s’affiche en regard du type de ressource d’image dans le **insérer la ressource** boîte de dialogue, cela signifie que les modèles de la barre d’outils sont disponibles. Sélectionnez le signe plus pour développer la liste des modèles, sélectionnez un modèle et choisissez **New**.

## <a name="add-an-image-for-a-different-display-device"></a>Ajouter une image pour un autre périphérique d’affichage

1. Sur le **Image** menu, sélectionnez **nouvelle Image de périphérique** (ou avec le bouton droit dans le **Éditeur d’images** volet et choisissez **nouvelle Image de périphérique** à partir de la menu contextuel).

1. Sélectionnez le type d’image que vous souhaitez ajouter. Vous pouvez également sélectionner **personnalisé** pour créer une icône dont la taille n’est pas disponible dans la liste par défaut.

## <a name="copy-a-device-image"></a>Copier une image de périphérique

1. Sur le **Image** menu, sélectionnez **nouveau type d’Image** et choisir une image à partir de la liste des images. Par exemple, choisir la version 16 couleurs d’une icône 32 x 32.

1. Copier l’image d’icône actuellement affiché (**Ctrl**+**C**).

1. Ouvrez une autre image de l’icône dans un autre **Éditeur d’images** fenêtre. Par exemple, ouvrez la version 16 couleurs de l’icône 16 x 16.

1. Collez l’image d’icône (**Ctrl**+**V**) à partir d’un **Éditeur d’images** fenêtre à l’autre. Si vous collez une plus grande taille dans une plus petite taille, vous pouvez utiliser les poignées de l’icône pour redimensionner l’image.

## <a name="delete-a-device-image"></a>Supprimer une image de périphérique

Tandis que l’image d’icône s’affiche dans le **Image** éditeur, sélectionnez **supprimer une Image de périphérique** à partir de la **Image** menu. Lorsque vous supprimez la dernière image d’icône dans la ressource, la ressource est également supprimée.

   > [!NOTE]
   > Quand vous appuyez sur la **Del** clé, que les images et les couleurs que vous avez dessiné sur une icône sont supprimées mais l’icône reste ; vous pouvez la redessiner. Si vous appuyez sur **Del** par erreur, vous pouvez appuyer sur **Ctrl**+**Z** annuler l’action.

## <a name="create-transparent-or-inverse-regions-in-device-images"></a>Créer des régions transparentes ou inversées dans des images de périphérique

Dans le [Éditeur d’images](../windows/image-editor-for-icons.md), l’image d’icône ou curseur a un attribut transparent. Bien que les images d’icône et curseur sont rectangulaires, nombreuses n’apparaissent pas, car les parties de l’image sont transparents ; l’image sous-jacente à l’écran affiche via l’icône ou un curseur. Lorsque vous faites glisser une icône, les parties de l’image peuvent apparaître dans une couleur inversée. Vous créez cet effet en définissant la couleur de l’écran et inverse dans le [fenêtre couleurs](../windows/colors-window-image-editor-for-icons.md).

Les couleurs de l’écran et inverse que vous appliquez aux icônes et curseurs mettre en forme et la couleur de l’image dérivée ou affecter des régions inversées. Les couleurs indiquent les parties de l’image qui ont ces attributs. Vous pouvez modifier les couleurs qui représentent les attributs de couleur de l’écran et couleur inversée lors de la modification. Ces modifications n’affectent pas l’apparence de l’icône ou le curseur dans votre application.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s’affichent peuvent être différentes de celles décrites dans l’**aide**, en fonction de vos paramètres actifs ou de l’édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

### <a name="to-create-transparent-or-inverse-regions"></a>Pour créer des régions transparentes ou inversées

1. Dans le **couleurs** fenêtre, sélectionnez le **couleur de l’écran** sélecteur ou **couleur inversée** sélecteur.

1. Appliquer l’écran ou la couleur inversée à votre image à l’aide d’un outil de dessin. Pour plus d’informations sur les outils de dessin, consultez [à l’aide d’un outil de dessin](using-a-drawing-tool-image-editor-for-icons.md).

### <a name="to-change-the-screen-or-inverse-color"></a>Pour modifier la couleur d’écran ou inverse

1. Sélectionnez le **couleur de l’écran** sélecteur ou **couleur inversée** sélecteur.

1. Choisissez une couleur dans le **couleurs** palette dans la **couleurs** fenêtre.

   La couleur complémentaire est automatiquement attribuée pour l’autre sélecteur.

   > [!TIP]
   > Si vous double-cliquez sur le **couleur de l’écran** ou **couleur inversée** sélecteur, les [boîte de dialogue Sélecteur de couleurs personnalisées](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md) s’affiche.

## <a name="use-the-256-color-palette"></a>Utilisez la palette 256 couleurs

À l’aide de la **Image** éditeur, icônes et curseurs peuvent être de grande taille (64 x 64) avec une palette de 256 couleurs. Après avoir créé la ressource, un style d’image de périphérique est sélectionné.

### <a name="to-create-a-256-color-icon-or-cursor"></a>Pour créer une icône de 256 couleurs ou d’un curseur

1. Dans [affichage des ressources](../windows/resource-view-window.md), avec le bouton droit de votre fichier .rc, puis choisissez **insérer la ressource** dans le menu contextuel. (Si vous disposez déjà d’une ressource image dans votre fichier .rc, par exemple un curseur, vous pouvez cliquer sur le **curseur** dossier et sélectionnez **insérer Cursor** dans le menu contextuel.)

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

1. Dans le [boîte de dialogue Ajouter une ressource](../windows/add-resource-dialog-box.md), sélectionnez **icône** ou **curseur** et choisissez **New**.

1. Sur le **Image** menu, sélectionnez **nouvelle Image de périphérique**.

1. Sélectionnez le style de l’image de 256 couleurs souhaité.

### <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>Pour choisir une couleur de la palette 256 couleurs pour les grandes icônes

Pour dessiner avec une sélection à partir de la palette 256 couleurs, vous devez sélectionner les couleurs à partir de la **couleurs** palette dans la [fenêtre couleurs](../windows/colors-window-image-editor-for-icons.md).

1. Sélectionnez la grande icône ou curseur, ou créez une nouvelle grande icône ou curseur.

1. Choisir une couleur parmi les 256 couleurs affichées dans le **couleurs** palette dans la **couleurs** fenêtre.

   La couleur sélectionnée devient la couleur actuelle dans le **couleurs** palette dans la **couleurs** fenêtre.

   > [!NOTE]
   > La palette d’origine utilisée pour les images de 256 couleurs correspond à la palette retournée par la `CreateHalftonePalette` API de Windows. Toutes les icônes pour le shell Windows doivent utiliser cette palette pour empêcher le scintillement pendant la réalisation de la palette.

## <a name="set-a-cursor39s-hot-spot"></a>Définir un curseur&#39;s réactive

La zone réactive d’un curseur est le point qui se réfère Windows pour suivre la position du curseur. Par défaut, la zone réactive est définie à l’angle supérieur gauche du curseur (coordonnées 0,0). Le **Hotspot** propriété dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) affiche les coordonnées de la zone réactive.

### <a name="to-set-a-cursors-hot-spot"></a>Pour définir la zone réactive d’un curseur

1. Sur le [barre d’outils Éditeur d’images](../windows/toolbar-image-editor-for-icons.md), choisissez le **définir la zone réactive** outil.

1. Sélectionnez le pixel que vous souhaitez affecter en tant que zone réactive du curseur.

   Le **Hotspot** propriété dans le **propriétés** fenêtre affiche les nouvelles coordonnées.

   > [!TIP]
   > Info-bulles s’affichent lorsque vous placez votre curseur sur un bouton de barre d’outils. Ces conseils peuvent vous aider à identifier la fonction de chaque bouton.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Spécifications

Aucun.

## <a name="see-also"></a>Voir aussi

[Menu image](../windows/image-menu-image-editor-for-icons.md)<br/>
[Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)<br/>
[Icônes](/windows/desktop/menurc/icons)<br/>
[Curseurs](/windows/desktop/menurc/cursors)<br/>
[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)<br/>

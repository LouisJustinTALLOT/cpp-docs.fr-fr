---
title: 'Procédure : Créez une icône ou une autre Image'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
- vc.editors.newimagetype
- vc.editors.customimage
- vc.editors.opendeviceimage
- vc.editors.image.editing
- vc.editors.image.editing
helpviewer_keywords:
- bitmaps [C++]
- images [C++], creating
- resources [C++], creating images
- bitmaps [C++], creating
- graphics [C++], creating
- Image editor [C++], creating images
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
- .gif files [C++], saving bitmaps as
- jpg files [C++], saving bitmaps as
- jpeg files [C++], saving bitmaps as
- .jpg files [C++], saving bitmaps as
- Image editor [C++], converting image formats
- gif files [C++], saving bitmaps as
- bitmaps [C++], converting formats
- .jpeg files [C++], saving bitmaps as
- graphics [C++], converting formats
- images [C++], converting formats
- images [C++], stand-alone editing
- Image editor [C++], converting image formats
- graphics [C++], converting formats
- images [C++], converting formats
ms.assetid: 66db3fb2-cfc1-48a2-9bdd-53f61eb7ee30
ms.openlocfilehash: d10593ffbae7aef55adc3334057402b6952d8ba7
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027595"
---
# <a name="how-to-create-an-icon-or-other-image"></a>Procédure : Créez une icône ou une autre Image

Vous pouvez créer une nouvelle image bitmap, icône, curseur, et/ou de barre d’outils, puis utiliser le **Éditeur d’images** pour personnaliser son apparence. Vous pouvez également créer une nouvelle image bitmap modélisé d’après un [modèle de ressource](../windows/how-to-use-resource-templates.md).

## <a name="icons-and-cursors-image-resources-for-display-devices"></a>Icônes et curseurs : Ressources d’images pour périphériques d’affichage

Les icônes et curseurs sont des ressources graphiques qui peuvent contenir plusieurs images de différentes tailles et modèles de couleurs pour différents types de périphériques d’affichage. Un curseur a également une zone réactive, l’emplacement Windows utilise pour effectuer le suivi de sa position. Icônes et curseurs sont créés et modifiés à l’aide du **Éditeur d’images**, comme les bitmaps et autres images.

Lorsque vous créez une nouvelle icône ou curseur, la **Éditeur d’images** crée d’abord une image d’un type standard. Cette image est remplie initialement avec la couleur d’écran (transparente). Si l’image est un curseur, la zone réactive est initialement le coin supérieur gauche avec les coordonnées `0,0`.

Par défaut, le **Éditeur d’images** prend en charge la création d’images supplémentaires pour les périphériques répertoriés dans le tableau suivant. Vous pouvez créer des images pour d’autres périphériques en tapant les paramètres de hauteur, largeur et nombre de couleurs dans le **Custom Image** boîte de dialogue.

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

### <a name="create-a-device-image-icon-or-cursor"></a>Créer une image de périphérique (icône ou curseur)

Lorsque vous créez une nouvelle icône ou une ressource du curseur, la **Éditeur d’images** crée d’abord une image dans un style spécifique (32 x 32, 16 couleurs pour les icônes et 32 x 32, Monochrome pour les curseurs). Vous pouvez ensuite ajouter des images de différentes tailles et les styles à l’icône d’origine et modifier chaque image supplémentaire, en fonction des besoins, pour les périphériques d’affichage différent. Vous pouvez également modifier une image à l’aide d’une opération de couper-coller à partir d’un type d’image existant ou d’une bitmap créée dans un programme graphique.

Lorsque vous ouvrez la ressource icône ou curseur dans le [Éditeur d’images](../windows/image-editor-for-icons.md), l’image de la plupart des étroitement le périphérique d’affichage actuel est ouverte par défaut.

> [!NOTE]
> Si votre projet ne contient pas déjà un fichier .rc, consultez [création d’un fichier de Script de ressources](../windows/how-to-create-a-resource-script-file.md).

Le **New &lt;appareil&gt; Type d’Image** boîte de dialogue vous permet de créer une nouvelle image de périphérique d’un type spécifié. Pour ouvrir le **New \<appareil > Image** boîte de dialogue, accédez au menu **Image** > **nouveau Type d’Image**. Les propriétés suivantes incluses sont **Type d’Image cible** et **personnalisé**.

Le **Type d’Image cible** propriété répertorie les types d’images disponibles lorsque vous sélectionnez l’image de type que vous souhaitez ouvrir :

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

Le **personnalisé** propriété ouvre le **Image personnalisée** boîte de dialogue dans laquelle vous pouvez créer une nouvelle image avec une taille personnalisée et le nombre de couleurs.

Le **Image personnalisée** boîte de dialogue vous permet de créer une nouvelle image avec une taille personnalisée et le nombre de couleurs. Les propriétés suivantes incluses sont :

|Propriété|Description|
|---|---|
|**Largeur**|Fournit un espace vous permettant d’entrer la largeur de l’image personnalisée en pixels (1-512, limite de 2048).|
|**Hauteur **|Fournit un espace vous permettant d’entrer la hauteur de l’image personnalisée en pixels (1-512, limite de 2048).|
|**Couleurs**|Fournit un espace vous permettant de choisir le nombre de couleurs pour l’image personnalisée : 2, 16 ou 256.|

Utilisez le **ouvrir &lt;appareil&gt; Image** boîte de dialogue pour ouvrir des images de périphérique dans les projets C++. Il répertorie les images de périphérique existantes dans la ressource actuelle (les images qui font partie de la ressource actuelle). La propriété suivante incluse est :

|Propriété|Description|
|---|---|
|**Images actuelles**|Répertorie les images incluses dans la ressource. Sélectionnez le type d’image que vous souhaitez ouvrir.|

#### <a name="to-create-a-new-icon-or-cursor"></a>Pour créer une nouvelle icône ou curseur

1. Dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources), avec le bouton droit votre *.rc* de fichier, puis choisissez **insérer la ressource**. Si vous disposez déjà d’une ressource image votre *.rc* fichier, par exemple un curseur, vous pouvez cliquer sur le **curseur** dossier et sélectionnez **insérer Cursor**.

1. Dans le [boîte de dialogue Ajouter une ressource](../windows/add-resource-dialog-box.md), sélectionnez **icône** ou **curseur** et choisissez **New**. Pour les icônes, cette action crée une ressource icône 16 couleurs, 32 x 32. Pour les curseurs, 32 x 32, Monochrome image (2-color) est créé.

   Si un signe plus (**+**) s’affiche en regard du type de ressource d’image dans le **insérer la ressource** boîte de dialogue, cela signifie que les modèles de la barre d’outils sont disponibles. Sélectionnez le signe plus pour développer la liste des modèles, sélectionnez un modèle et choisissez **New**.

### <a name="to-add-an-image-for-a-different-display-device"></a>Pour ajouter une image pour un autre périphérique d’affichage

1. Accédez au menu **Image** > **nouvelle Image de périphérique**, ou avec le bouton droit dans le **Éditeur d’images** volet et choisissez **nouvelle Image de périphérique**.

1. Sélectionnez le type d’image que vous souhaitez ajouter. Vous pouvez également sélectionner **personnalisé** pour créer une icône dont la taille n’est pas disponible dans la liste par défaut.

### <a name="to-copy-a-device-image"></a>Pour copier une image de périphérique

1. Accédez au menu **Image** > **nouveau type d’Image** et choisir une image à partir de la liste des images. Par exemple, choisir la version 16 couleurs d’une icône 32 x 32.

1. Copier l’image d’icône actuellement affiché (**Ctrl**+**C**).

1. Ouvrez une autre image de l’icône dans un autre **Éditeur d’images** fenêtre. Par exemple, ouvrez la version 16 couleurs de l’icône 16 x 16.

1. Collez l’image d’icône (**Ctrl**+**V**) à partir d’un **Éditeur d’images** fenêtre à l’autre. Si vous collez une plus grande taille dans une plus petite taille, vous pouvez utiliser les poignées de l’icône pour redimensionner l’image.

### <a name="to-delete-a-device-image"></a>Pour supprimer une image de périphérique

Tandis que l’image d’icône s’affiche dans le **Éditeur d’images**, accédez au menu **Image** > **supprimer une Image de périphérique**. Lorsque vous supprimez la dernière image d’icône dans la ressource, la ressource est également supprimée.

> [!NOTE]
> Quand vous appuyez sur la **Del** clé, que les images et les couleurs que vous avez dessiné sur une icône sont supprimées mais l’icône reste et vous pouvez la redessiner. Si vous appuyez sur **Del** par erreur, appuyez sur **Ctrl**+**Z** annuler l’action.

### <a name="to-create-transparent-or-inverse-regions-in-device-images"></a>Pour créer des régions transparentes ou inversées dans des images de périphérique

Dans le [Éditeur d’images](../windows/image-editor-for-icons.md), l’image d’icône ou curseur a un attribut transparent. Bien que les images d’icône et curseur sont rectangulaires, de nombreux n’apparaissent donc, car les parties de l’image sont transparents et l’image sous-jacente à l’écran affiche via l’icône ou un curseur. Lorsque vous faites glisser une icône, les parties de l’image peuvent apparaître dans une couleur inversée. Vous créez cet effet en définissant la couleur de l’écran et inverse dans le [fenêtre couleurs](../windows/colors-window-image-editor-for-icons.md).

Les couleurs de l’écran et inverse que vous appliquez aux icônes et curseurs mettre en forme et la couleur de l’image dérivée ou affecter des régions inversées. Les couleurs indiquent les parties de l’image qui ont ces attributs. Vous pouvez modifier les couleurs qui représentent les attributs de couleur de l’écran et couleur inversée lors de la modification. Ces modifications n’affectent pas l’apparence de l’icône ou le curseur dans votre application.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s’affichent peuvent être différentes de celles décrites dans l’**aide**, en fonction de vos paramètres actifs ou de l’édition utilisée. Pour modifier vos paramètres, accédez au menu **outils** > **importation et exportation de paramètres**. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

#### <a name="to-create-transparent-or-inverse-regions"></a>Pour créer des régions transparentes ou inversées

1. Dans le **couleurs** fenêtre, choisissez le sélecteur **couleur de l’écran** ou **couleur inversée**.

1. Appliquer l’écran ou la couleur inversée à votre image à l’aide d’un outil de dessin. Pour plus d’informations sur les outils de dessin, consultez [à l’aide d’un outil de dessin](using-a-drawing-tool-image-editor-for-icons.md).

#### <a name="to-change-the-screen-or-inverse-color"></a>Pour modifier la couleur d’écran ou inverse

1. Sélectionnez le **couleur de l’écran** sélecteur ou **couleur inversée** sélecteur.

1. Choisissez une couleur dans le **couleurs** palette dans la **couleurs** fenêtre.

   La couleur complémentaire est automatiquement attribuée pour l’autre sélecteur.

   > [!TIP]
   > Si vous double-cliquez sur le **couleur de l’écran** ou **couleur inversée** sélecteur, les [boîte de dialogue Sélecteur de couleurs personnalisées](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md) s’affiche.

### <a name="use-the-256-color-palette"></a>Utilisez la palette 256 couleurs

À l’aide de la **Éditeur d’images**, icônes et curseurs peuvent provenir grande taille (64 x 64) avec une palette 256 couleurs. Après avoir créé la ressource, un style d’image de périphérique est sélectionné.

#### <a name="to-create-a-256-color-icon-or-cursor"></a>Pour créer une icône de 256 couleurs ou d’un curseur

1. Dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources), avec le bouton droit votre *.rc* de fichier, puis choisissez **insérer la ressource**. Si vous disposez déjà d’une ressource image votre *.rc* fichier, par exemple un curseur, vous pouvez cliquer sur le **curseur** dossier et sélectionnez **insérer Cursor**.

1. Dans le [boîte de dialogue Ajouter une ressource](../windows/add-resource-dialog-box.md), sélectionnez **icône** ou **curseur** et choisissez **New**.

1. Accédez au menu **Image** > **nouvelle Image de périphérique** et sélectionnez l’image de 256 couleurs de style.

#### <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>Pour choisir une couleur de la palette 256 couleurs pour les grandes icônes

Pour dessiner avec une sélection à partir de la palette 256 couleurs, vous devez sélectionner les couleurs à partir de la **couleurs** palette dans la [fenêtre couleurs](../windows/colors-window-image-editor-for-icons.md).

1. Sélectionnez la grande icône ou curseur, ou créez une nouvelle grande icône ou curseur.

1. Choisir une couleur parmi les 256 couleurs affichées dans le **couleurs** palette dans la **couleurs** fenêtre.

   La couleur sélectionnée devient la couleur actuelle dans le **couleurs** palette dans la **couleurs** fenêtre.

   > [!NOTE]
   > La palette d’origine utilisée pour les images de 256 couleurs correspond à la palette retournée par la `CreateHalftonePalette` API de Windows. Toutes les icônes pour le shell Windows doivent utiliser cette palette pour empêcher le scintillement pendant la réalisation de la palette.

### <a name="to-set-a-cursors-hot-spot"></a>Pour définir la zone réactive d’un curseur

La zone réactive d’un curseur est le point qui se réfère Windows pour suivre la position du curseur. Par défaut, la zone réactive est définie à l’angle supérieur gauche du curseur avec les coordonnées `0,0`. Le **Hotspot** propriété dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) affiche les coordonnées de la zone réactive.

1. Sur le [barre d’outils Éditeur d’images](../windows/toolbar-image-editor-for-icons.md), choisissez le **définir la zone réactive** outil.

1. Sélectionnez le pixel que vous souhaitez affecter en tant que zone réactive du curseur.

   Le **Hotspot** propriété dans le **propriétés** fenêtre affiche les nouvelles coordonnées.

### <a name="to-create-and-save-a-bitmap-as-a-gif-or-jpeg"></a>Pour créer et enregistrer une image bitmap en tant que .gif ou .jpeg

Lorsque vous créez une image bitmap, l’image est créée au format bitmap (.bmp). Vous pouvez, toutefois, enregistrer l’image au format GIF ou JPEG ou dans d’autres formats graphiques.

> [!NOTE]
> Ce processus ne s’applique pas aux icônes et curseurs.

1. Accédez au menu **fichier** > **Open**, puis sélectionnez **fichier**.

1. Dans le **boîte de dialogue Nouveau fichier**, choisissez le **Visual C++** dossier, puis sélectionnez **fichier Bitmap (.bmp)** dans le **modèles** et sélectionnez  **Ouvrez**.

   La bitmap s’ouvre dans le **Éditeur d’images**.

1. Apportez des modifications à votre nouvelle image bitmap en fonction des besoins.

1. Avec la bitmap est ouverte dans le **Éditeur d’images**, accédez au menu **fichier** > **enregistrer *filename*.bmp comme**.

1. Dans le **enregistrer le fichier sous** boîte de dialogue, tapez le nom que vous souhaitez attribuer au fichier et l’extension qui dénote le format de fichier dans le **nom de fichier** boîte. Par exemple, *MonFichier.gif*.

   > [!NOTE]
   > Vous devez créer ou ouvrir l’image bitmap en dehors de votre projet afin d’enregistrer dans un autre format de fichier. Si vous créez ou ouvrez dans votre projet, le **enregistrer en tant que** n’est pas disponible. Pour plus d’informations, consultez [affichage des ressources dans un fichier de Script de ressources en dehors d’un projet (autonome)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

1. Sélectionnez **Enregistrer**.

### <a name="to-convert-an-image-from-one-format-to-another"></a>Pour convertir une image d’un format vers un autre

Vous pouvez ouvrir des images GIF ou JPEG dans la **Éditeur d’images** et enregistrez-les en tant que les bitmaps. En outre, vous pouvez ouvrir un fichier bitmap et enregistrez-le au format GIF ou JPEG. Vous travaillez avec des images ne sont pas nécessairement partie d’un projet pour le modifier dans l’environnement de développement (consultez [modification d’image autonome](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md)).

1. Ouvrir l’image dans le **Éditeur d’images**.

1. Accédez au menu **fichier** > **enregistrer *filename* comme**.

1. Dans le **enregistrer le fichier sous** boîte de dialogue le **nom de fichier** , tapez le nom de fichier et l’extension qui dénote le format souhaité.

1. Sélectionnez **Enregistrer**.

### <a name="to-add-a-new-image-resource-to-an-unmanaged-c-project"></a>Pour ajouter une nouvelle ressource image à un projet C++ non managé

1. Dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources), avec le bouton droit votre *.rc* de fichier, puis choisissez **insérer la ressource**. Si vous disposez déjà d’une ressource image votre *.rc* fichier, par exemple un curseur, vous pouvez simplement avec le bouton droit le **curseur** dossier et sélectionnez **insérer Cursor**.

1. Dans le [boîte de dialogue Ajouter une ressource](../windows/add-resource-dialog-box.md), sélectionnez le type de ressource image que vous souhaitez créer (**Bitmap**, par exemple) puis choisissez **New**.

   Si un signe plus (**+**) s’affiche en regard du type de ressource d’image dans le **insérer la ressource** boîte de dialogue, cela signifie que les modèles de la barre d’outils sont disponibles. Sélectionnez le signe plus pour développer la liste des modèles, sélectionnez un modèle et choisissez **New**.

### <a name="to-add-a-new-image-resource-to-a-project-in-a-net-programming-language"></a>Pour ajouter une nouvelle ressource image à un projet dans un langage de programmation .NET

1. Dans **l’Explorateur de solutions**, cliquez sur le dossier du projet (par exemple, *WindowsApplication1*).

1. Dans le menu contextuel, sélectionnez **ajouter**, puis choisissez **ajouter un nouvel élément**.

1. Dans le **catégories** volet, développez le **des éléments de projet Local** dossier, puis choisissez **ressources**.

1. Dans le **modèles** volet, choisissez le type de ressource que vous souhaitez ajouter à votre projet.

   La ressource est ajoutée à votre projet dans **l’Explorateur de solutions** et la ressource s’ouvre dans le [Éditeur d’images](../windows/image-editor-for-icons.md). Vous pouvez maintenant utiliser tous les outils disponibles dans le **Éditeur d’images** pour modifier votre image. Pour plus d’informations sur l’ajout d’images à un projet managé, consultez [chargement d’une image au moment du Design](/dotnet/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms).

## <a name="requirements"></a>Configuration requise

Aucun.

## <a name="see-also"></a>Voir aussi

[Éditeur d'images pour les icônes](../windows/image-editor-for-icons.md)<br/>
[Procédure : Modifier une Image](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Procédure : Utiliser un outil de dessin](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[Procédure : Utiliser des couleurs](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
<!--
[Converting Bitmaps to Toolbars](../windows/converting-bitmaps-to-toolbars.md)<br/>
[Creating New Toolbars](../windows/creating-new-toolbars.md)<br/>
[Icons](/windows/desktop/menurc/icons)<br/>
[Cursors](/windows/desktop/menurc/cursors)<br/>-->
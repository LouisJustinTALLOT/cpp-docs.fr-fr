---
title: 'Comment : créer une icône ou une autre image'
ms.date: 02/15/2019
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
ms.openlocfilehash: 931d84f16b46ea8fe21ecc0a63d20dac958ce960
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160436"
---
# <a name="how-to-create-an-icon-or-other-image"></a>Comment : créer une icône ou une autre image

Vous pouvez créer une image, une image bitmap, une icône, un curseur ou une barre d’outils, puis utiliser l' **éditeur d’images** pour personnaliser son apparence. Vous pouvez également créer une nouvelle bitmap basée sur un [modèle de ressource](../windows/how-to-use-resource-templates.md).

## <a name="icons-and-cursors-image-resources-for-display-devices"></a>Icônes et curseurs : ressources image pour les périphériques d'affichage

Les icônes et curseurs sont des ressources graphiques qui peuvent contenir plusieurs images de différentes tailles et modèles de couleurs pour différents types de périphériques d’affichage. Un curseur a également une zone réactive, l’emplacement utilisé par Windows pour suivre sa position. Les icônes et les curseurs sont créés et modifiés à l’aide de l' **éditeur d’images**, comme les bitmaps et autres images.

Lorsque vous créez une icône ou un curseur, l' **éditeur d’images** crée d’abord une image d’un type standard. Cette image est remplie initialement avec la couleur d’écran (transparente). Si l’image est un curseur, la zone réactive est initialement l’angle supérieur gauche avec les coordonnées `0,0`.

Par défaut, l' **éditeur d’images** prend en charge la création d’images supplémentaires pour les périphériques répertoriés dans le tableau suivant. Vous pouvez créer des images pour d’autres périphériques en tapant les paramètres de largeur, de hauteur et de nombre de couleurs dans la boîte de dialogue **image personnalisée** .

|Couleur|Largeur (pixels)|Hauteur (pixels)|
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

### <a name="create-a-device-image-icon-or-cursor"></a>Créer une image d’appareil (icône ou curseur)

Lorsque vous créez une nouvelle ressource icône ou curseur, l' **éditeur d’images** crée d’abord une image dans un style spécifique (32 × 32, 16 couleurs pour les icônes et 32 × 32, monochrome pour les curseurs). Vous pouvez ensuite ajouter des images dans des tailles et des styles différents à l’icône initiale ou au curseur et modifier chaque image supplémentaire, si nécessaire, pour les différents appareils d’affichage. Vous pouvez également modifier une image à l’aide d’une opération couper-coller à partir d’un type d’image existant ou d’une image bitmap créée dans un programme graphique.

Lorsque vous ouvrez la ressource icône ou curseur dans l' [éditeur d’images](../windows/image-editor-for-icons.md), l’image qui correspond le plus au périphérique d’affichage actuel est ouverte par défaut.

> [!NOTE]
> Si votre projet ne contient pas déjà un fichier. RC, consultez [création d’un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

La boîte de dialogue **nouveau type d’image&gt; d’appareil &lt;** vous permet de créer une nouvelle image d’appareil d’un type spécifié. Pour ouvrir la boîte de dialogue **nouvelle image du > de l’appareil \<** , accédez à **image** du menu > **nouveau type d’image**. Les propriétés suivantes sont incluses : **type d’image cible** et **personnalisé**.

La propriété **type d’image cible** répertorie les types d’images disponibles dans lesquels vous sélectionnez le type d’image que vous souhaitez ouvrir :

||||
|-|-|-|
|-16 x 16, 16 couleurs|-48 x 48, 16 couleurs|-96 x 96, 16 couleurs|
|-16 x 16, 256 couleurs|-48 x 48, 256 couleurs|-96 x 96, 256 couleurs|
|-16 x 16, monochrome|-48 x 48, monochrome|-96 x 96, monochrome|
|-32 x 32, 16 couleurs|-64 x 64, 16 couleurs||
|-32 x 32, 256 couleurs|-64 x 64, 256 couleurs||
|-32 x 32, monochrome|-64 x 64, monochrome||

> [!NOTE]
> Les images existantes ne seront pas affichées dans cette liste.

La propriété **personnalisée** ouvre la boîte de dialogue **image personnalisée** dans laquelle vous pouvez créer une image avec une taille personnalisée et un nombre de couleurs.

La boîte de dialogue **image personnalisée** vous permet de créer une image avec une taille personnalisée et un nombre de couleurs. Les propriétés incluses sont les suivantes :

|Propriété|Description|
|---|---|
|**Width**|Offre un espace vous permettant d’entrer la largeur de l’image personnalisée en pixels (1-512, limite de 2048).|
|**Height**|Offre un espace vous permettant d’entrer la hauteur de l’image personnalisée en pixels (1-512, limite de 2048).|
|**Couleurs**|Offre un espace vous permettant de choisir le nombre de couleurs pour l’image personnalisée : 2, 16 ou 256.|

Utilisez la boîte de dialogue Ouvrir l’image de l'&gt; de l' **appareil &lt;** pour ouvrir des images de périphérique dans des C++ projets. Elle répertorie les images d’appareil existantes dans la ressource actuelle (les images qui font partie de la ressource actuelle). La propriété incluse est la suivante :

|Propriété|Description|
|---|---|
|**Images actuelles**|Répertorie les images incluses dans la ressource. Sélectionnez le type d’image que vous souhaitez ouvrir.|

#### <a name="to-create-a-new-icon-or-cursor"></a>Pour créer une icône ou un curseur

1. Dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources), cliquez avec le bouton droit sur votre fichier *. RC* , puis choisissez **Insérer une ressource**. Si vous disposez déjà d’une ressource d’image dans votre fichier *. RC* , par exemple un curseur, vous pouvez cliquer avec le bouton droit sur le dossier de **curseur** et sélectionner **Insérer un curseur**.

1. Dans la [boîte de dialogue Insérer une ressource](../windows/add-resource-dialog-box.md), sélectionnez **icône** ou **curseur** , puis choisissez **nouveau**. Pour les icônes, cette action crée une ressource icône avec une icône 32 × 32, 16 couleurs. Pour les curseurs, une image 32 × 32, monochrome (2 couleurs) est créée.

   Si un signe plus ( **+** ) s’affiche en regard du type de ressource image dans la boîte de dialogue **Insérer une ressource** , cela signifie que les modèles de barre d’outils sont disponibles. Sélectionnez le signe plus (+) pour développer la liste des modèles, sélectionnez un modèle, puis choisissez **nouveau**.

### <a name="to-add-an-image-for-a-different-display-device"></a>Pour ajouter une image pour un autre périphérique d’affichage

1. Accédez à l' **image** du menu > **nouvelle image**de l’appareil, ou cliquez avec le bouton droit dans le volet de l' **éditeur d’images** et choisissez **nouvelle image**de l’appareil.

1. Sélectionnez le type d’image que vous souhaitez ajouter. Vous pouvez également sélectionner **personnalisé** pour créer une icône dont la taille n’est pas disponible dans la liste par défaut.

### <a name="to-copy-a-device-image"></a>Pour copier une image d’appareil

1. Accédez à l' **image** du menu > **ouvrir l’image** de l’appareil et choisissez une image dans la liste images actuelles. Par exemple, choisissez la version 32 × 32, 16 couleurs d’une icône.

1. Copiez l’image de l’icône actuellement affichée (**Ctrl**+**C**).

1. Ouvrez une image différente de l’icône dans une autre fenêtre de l' **éditeur d’images** . Par exemple, ouvrez la version 16 x 16, 16 couleurs de l’icône.

1. Collez l’image d’icône (**Ctrl**+**V**) d’une fenêtre de l' **éditeur d’images** à l’autre. Si vous collez une plus grande taille dans une taille plus petite, vous pouvez utiliser les poignées d’icône pour redimensionner l’image.

### <a name="to-delete-a-device-image"></a>Pour supprimer une image d’appareil

Lorsque l’image de l’icône s’affiche dans l' **éditeur d’images**, accédez à l' **image** du menu > supprimer l’image de l' **appareil**. Lorsque vous supprimez la dernière image d’icône de la ressource, la ressource est également supprimée.

> [!NOTE]
> Lorsque vous appuyez sur la touche **Suppr** , les images et les couleurs que vous avez dessinées sur une icône sont supprimées, mais l’icône est conservée et vous pouvez maintenant la reconcevoir. Si vous appuyez sur la touche **Suppr** par erreur, appuyez sur **CTRL**+**Z** pour annuler l’action.

### <a name="to-create-transparent-or-inverse-regions-in-device-images"></a>Pour créer des régions transparentes ou inversées dans des images d’appareil

Dans l' [éditeur d’images](../windows/image-editor-for-icons.md), l’icône initiale ou l’image de curseur a un attribut transparent. Bien que les images d’icône et de curseur soient rectangulaires, beaucoup ne s’affichent pas, car les parties de l’image sont transparentes et l’image sous-jacente de l’écran s’affiche à travers l’icône ou le curseur. Lorsque vous faites glisser une icône, certaines parties de l’image peuvent apparaître dans une couleur inversée. Vous créez cet effet en définissant la couleur de l’écran et la couleur inverse dans la [fenêtre couleurs](../windows/colors-window-image-editor-for-icons.md).

L’écran et les couleurs inversées que vous appliquez aux icônes et aux curseurs se forment et colorent l’image dérivée ou affectent les régions inversées. Les couleurs indiquent les parties de l’image qui ont ces attributs. Vous pouvez modifier les couleurs qui représentent les attributs de couleur d’écran et de couleur inverse lors de la modification. Ces modifications n’affectent pas l’apparence de l’icône ou du curseur dans votre application.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s’affichent peuvent être différentes de celles décrites dans l’**aide**, en fonction de vos paramètres actifs ou de l’édition utilisée. Pour modifier vos paramètres, accédez à **Outils** de menu > **paramètres d’importation et d’exportation**. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

#### <a name="to-create-transparent-or-inverse-regions"></a>Pour créer des régions transparentes ou inversées

1. Dans la fenêtre **couleurs** , choisissez la couleur de l' **écran** de sélection ou la **couleur inverse**.

1. Appliquez l’écran ou la couleur inverse sur votre image à l’aide d’un outil de dessin. Pour plus d’informations sur les outils de dessin, consultez [utilisation d’un outil de dessin](using-a-drawing-tool-image-editor-for-icons.md).

#### <a name="to-change-the-screen-or-inverse-color"></a>Pour modifier l’écran ou la couleur inverse

1. Sélectionnez le sélecteur **de couleur d’écran** ou le sélecteur **de couleurs inversées** .

1. Choisissez une couleur dans la palette de **couleurs** de la fenêtre **couleurs** .

   La couleur complémentaire est affectée automatiquement à l’autre sélecteur.

   > [!TIP]
   > Si vous double-cliquez sur la **couleur d’écran** ou le sélecteur **de couleurs inversées** , la [boîte de dialogue Sélecteur de couleurs personnalisé](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md) s’affiche.

### <a name="use-the-256-color-palette"></a>Utilisez la palette de couleurs 256

À l’aide de l' **éditeur d’images**, les icônes et les curseurs peuvent être de grande taille (64 × 64) avec une palette de 256 de couleurs. Une fois la ressource créée, un style d’image de périphérique est sélectionné.

#### <a name="to-create-a-256-color-icon-or-cursor"></a>Pour créer une icône ou un curseur de couleur 256

1. Dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources), cliquez avec le bouton droit sur votre fichier *. RC* , puis choisissez **Insérer une ressource**. Si vous disposez déjà d’une ressource d’image dans votre fichier *. RC* , par exemple un curseur, vous pouvez cliquer avec le bouton droit sur le dossier de **curseur** et sélectionner **Insérer un curseur**.

1. Dans la [boîte de dialogue Insérer une ressource](../windows/add-resource-dialog-box.md), sélectionnez **icône** ou **curseur** , puis choisissez **nouveau**.

1. Accédez à **image** du menu > **nouvelle image** de l’appareil et sélectionnez le style d’image 256 en couleurs de votre choix.

#### <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>Pour choisir une couleur dans la palette de couleurs 256 pour les grandes icônes

Pour dessiner avec une sélection à partir de la palette de couleurs 256, vous devez sélectionner les couleurs de la palette **couleurs** dans la [fenêtre couleurs](../windows/colors-window-image-editor-for-icons.md).

1. Sélectionnez la grande icône ou le curseur, ou créez une nouvelle icône ou un curseur de grande taille.

1. Choisissez une couleur parmi les couleurs 256 affichées dans la palette de **couleurs** de la fenêtre **couleurs** .

   La couleur sélectionnée devient la couleur actuelle dans la palette de **couleurs** de la fenêtre **couleurs** .

   > [!NOTE]
   > La palette initiale utilisée pour les images de couleur 256 correspond à la palette retournée par l’API Windows `CreateHalftonePalette`. Toutes les icônes destinées au shell Windows doivent utiliser cette palette pour empêcher le scintillement lors de la réalisation de la palette.

### <a name="to-set-a-cursors-hot-spot"></a>Pour définir la zone réactive d’un curseur

La zone réactive d’un curseur est le point auquel Windows fait référence pour suivre la position du curseur. Par défaut, la zone réactive est définie sur l’angle supérieur gauche du curseur, avec des coordonnées `0,0`. La propriété **hotspot** dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) affiche les coordonnées de la zone réactive.

1. Dans la [barre d’outils de l’éditeur d’images](../windows/toolbar-image-editor-for-icons.md), choisissez l’outil **définir la zone réactive** .

1. Sélectionnez le pixel que vous souhaitez affecter comme zone réactive du curseur.

   La propriété **hotspot** dans la fenêtre **Propriétés** affiche les nouvelles coordonnées.

### <a name="to-create-and-save-a-bitmap-as-a-gif-or-jpeg"></a>Pour créer et enregistrer une image bitmap sous forme de fichier. gif ou. jpeg

Lorsque vous créez une image bitmap, l’image est créée au format bitmap (. bmp). Toutefois, vous pouvez enregistrer l’image au format GIF ou JPEG ou dans d’autres formats graphiques.

> [!NOTE]
> Ce processus ne s’applique pas aux icônes et aux curseurs.

1. Accédez au menu **fichier** > **ouvrir**, puis sélectionnez **fichier**.

1. Dans la boîte de **dialogue nouveau fichier**, choisissez le dossier  **C++ visuel** , puis sélectionnez **fichier bitmap (. bmp)** dans la zone **modèles** et sélectionnez **ouvrir**.

   Le bitmap s’ouvre dans l' **éditeur d’images**.

1. Apportez les modifications nécessaires à votre nouvelle image bitmap.

1. Une fois l’image bitmap ouverte dans l' **éditeur d’images**, accédez à menu **fichier** > **Enregistrez *nom_fichier*. bmp sous**.

1. Dans la boîte de dialogue **enregistrer le fichier sous** , tapez le nom que vous souhaitez attribuer au fichier et l’extension qui dénote le format de fichier souhaité dans la zone **nom de fichier** . Par exemple, *MyFile. gif*.

   > [!NOTE]
   > Vous devez créer ou ouvrir la bitmap en dehors de votre projet afin de l’enregistrer dans un autre format de fichier. Si vous le créez ou l’ouvrez dans votre projet, la commande **Enregistrer sous** n’est pas disponible. Pour plus d’informations, consultez [affichage des ressources dans un fichier de script de ressources en dehors d’un projet (autonome)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

1. Sélectionnez **Enregistrer**.

### <a name="to-convert-an-image-from-one-format-to-another"></a>Pour convertir une image d’un format à un autre

Vous pouvez ouvrir des images GIF ou JPEG dans l' **éditeur d’images** et les enregistrer en tant que bitmaps. En outre, vous pouvez ouvrir un fichier bitmap et l’enregistrer au format GIF ou JPEG. Les images que vous utilisez n’ont pas besoin de faire partie d’un projet pour être modifiées dans l’environnement de développement (consultez [modification d’images autonomes](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md)).

1. Ouvrez l’image dans l' **éditeur d’images**.

1. Accédez au menu **fichier** > **enregistrer le *nom* de fichier sous**.

1. Dans la boîte de dialogue **enregistrer le fichier sous** , dans la zone **nom de fichier** , tapez le nom de fichier et l’extension qui désignent le format souhaité.

1. Sélectionnez **Enregistrer**.

### <a name="to-add-a-new-image-resource-to-an-unmanaged-c-project"></a>Pour ajouter une nouvelle ressource image à un C++ projet non managé

1. Dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources), cliquez avec le bouton droit sur votre fichier *. RC* , puis choisissez **Insérer une ressource**. Si vous disposez déjà d’une ressource d’image dans votre fichier *. RC* , par exemple un curseur, vous pouvez simplement cliquer avec le bouton droit sur le dossier **curseur** et sélectionner **Insérer un curseur**.

1. Dans la [boîte de dialogue Insérer une ressource](../windows/add-resource-dialog-box.md), sélectionnez le type de ressource d’image que vous souhaitez créer (**bitmap**, par exemple), puis choisissez **nouveau**.

   Si un signe plus ( **+** ) s’affiche en regard du type de ressource image dans la boîte de dialogue **Insérer une ressource** , cela signifie que les modèles de barre d’outils sont disponibles. Sélectionnez le signe plus (+) pour développer la liste des modèles, sélectionnez un modèle, puis choisissez **nouveau**.

### <a name="to-add-a-new-image-resource-to-a-project-in-a-net-programming-language"></a>Pour ajouter une nouvelle ressource image à un projet dans un langage de programmation .NET

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le dossier du projet (par exemple, *WindowsApplication1*).

1. Dans le menu contextuel, sélectionnez **Ajouter**, puis choisissez **Ajouter un nouvel élément**.

1. Dans le volet **catégories** , développez le dossier **éléments de projet locaux** , puis choisissez **ressources**.

1. Dans le volet **modèles** , choisissez le type de ressource que vous souhaitez ajouter à votre projet.

   La ressource est ajoutée à votre projet dans **Explorateur de solutions** et la ressource s’ouvre dans l' [éditeur d’images](../windows/image-editor-for-icons.md). Vous pouvez maintenant utiliser tous les outils disponibles dans l' **éditeur d’images** pour modifier votre image. Pour plus d’informations sur l’ajout d’images à un projet managé, consultez [chargement d’une image au moment du design](/dotnet/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms).

## <a name="requirements"></a>Spécifications

None

## <a name="see-also"></a>Voir aussi

[Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)<br/>
[Comment : modifier une image](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Comment : utiliser un outil de dessin](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[Comment : utiliser la couleur](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
<!--
[Converting Bitmaps to Toolbars](../windows/converting-bitmaps-to-toolbars.md)<br/>
[Creating New Toolbars](../windows/creating-new-toolbars.md)<br/>
[Icons](/windows/win32/menurc/icons)<br/>
[Cursors](/windows/win32/menurc/cursors)<br/>-->

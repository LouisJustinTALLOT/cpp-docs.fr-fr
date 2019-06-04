---
title: Éditeur de la barre d’outils (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.toolbar.F1
- vc.editors.toolbar
- vc.editors.newtoolbarresource
helpviewer_keywords:
- resource editors [C++], Toolbar editor
- editors, toolbars
- toolbars [C++], editing
- Toolbar editor
- toolbars [C++], creating
- Toolbar editor [C++], creating new toolbars
- Insert Resource
- bitmaps [C++], converting to toolbars
- Toolbar editor [C++], converting bitmaps
- toolbars [C++], converting bitmaps
- New Toolbar Resource dialog box [C++]
- buttons [C++], custom toolbars
- toolbar buttons [C++], editing
- buttons
- toolbar buttons [C++], creating
- Toolbar editor [C++], creating buttons
- toolbar buttons [C++], button image
- toolbar buttons [C++], creating
- toolbar buttons (in Toolbar editor)
- toolbar buttons [C++], moving
- Toolbar editor [C++], moving buttons
- Toolbar editor [C++], copying buttons
- toolbars [C++], copying buttons
- toolbar buttons [C++], copying
- toolbar buttons [C++], deleting
- Toolbar editor [C++], deleting buttons
- Toolbar editor [C++], spacing toolbar buttons
- toolbar buttons [C++], space between buttons
- toolbar controls [MFC], command ID
- toolbar buttons [C++], setting properties
- Toolbar editor [C++], toolbar button properties
- command IDs, toolbar buttons
- size, toolbar buttons
- toolbar buttons [C++], setting properties
- Toolbar editor [C++], toolbar button properties
- status bars [C++], active toolbar button text
- command IDs, toolbar buttons
- width, toolbar buttons
- tool tips [C++], adding to toolbar buttons
- "\n in tool tip"
- toolbar buttons [C++], tool tips
- buttons [C++], tool tips
- Toolbar editor [C++], creating tool tips
ms.assetid: aa9f0adf-60f6-4f79-ab05-bc330f15ec43
ms.openlocfilehash: f0faa93cd4ea1fdc2fad90a5d4d47f2feeef65e6
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66504214"
---
# <a name="toolbar-editor-c"></a>Éditeur de la barre d’outils (C++)

Le **barre d’outils Éditeur** vous permet de créer des ressources de barre d’outils et de convertir des bitmaps en ressources de barre d’outils. Le **barre d’outils Éditeur** utilise un affichage graphique pour afficher une barre d’outils et les boutons qui ressemblent étroitement à la façon dont ils regarde dans une application finie.

Le **barre d’outils Éditeur** fenêtre affiche deux vues d’une image du bouton, le même que le **Éditeur d’images** fenêtre. Une barre de fractionnement sépare les deux volets, et vous pouvez faire glisser la barre de fractionnement côté à côte pour modifier les tailles relatives des volets. Le volet actif affiche une bordure de sélection et au-dessus des deux affichages de l’image est la barre d’outils de l’objet.

![Barre d’outils Éditeur](../mfc/media/vctoolbareditor.gif "vcToolbarEditor")<br/>
**Éditeur de barres d’outils**

Le **barre d’outils Éditeur** est similaire à la **Éditeur d’images** dans les éléments de menu et de fonctionnalités, outils de graphique et la grille de bitmap entre les deux sont les mêmes. Il existe une commande de menu dans le **Image** menu pour basculer entre le **barre d’outils Éditeur** et **Éditeur d’images**. Pour plus d’informations sur l’utilisation de la **Graphics** barre d’outils, **couleurs** palette, ou **Image** menu, consultez [Éditeur d’images](../windows/image-editor-for-icons.md).

Vous pouvez créer une nouvelle barre d’outils dans un projet C++ en convertissant une image bitmap. Le graphique à partir de l’image bitmap convertit les images du bouton d’une barre d’outils. L’image bitmap contient généralement plusieurs images de bouton sur une seule bitmap, avec une seule image pour chaque bouton. Images peuvent être n’importe quelle taille que la valeur par défaut est 16 pixels de large et la hauteur de l’image. Vous pouvez spécifier la taille des images de bouton dans le **nouvelle ressource de barre d’outils** boîte de dialogue lorsque vous choisissez **barre d’outils Éditeur** à partir de la **Image** menu lors de la  **Éditeur d’images**.

Le **nouvelle ressource de barre d’outils** boîte de dialogue vous permet de spécifier la largeur et la hauteur des boutons que vous ajoutez à une ressource de barre d’outils dans un projet C++. La valeur par défaut est 16 x 15 pixels.

Une image bitmap qui sert à créer une barre d’outils a une largeur maximale de 2048, ainsi si vous définissez la **la largeur du bouton** à *512*, vous ne pouvez avoir quatre boutons. Si vous définissez la largeur sur *513*, vous ne pouvez avoir trois boutons.

Le **nouvelle ressource de barre d’outils** boîte de dialogue a les propriétés suivantes :

|Propriété|Description|
|---|---------------|
|**Largeur du bouton**|Fournit un espace vous permettant d’entrer la largeur pour les boutons de barre d’outils que vous voulez convertir à partir d’une ressource bitmap en une ressource de barre d’outils.|
|**Hauteur du bouton**|Fournit un espace vous permettant d’entrer la hauteur pour les boutons de barre d’outils que vous voulez convertir à partir d’une ressource bitmap en une ressource de barre d’outils.|

> [!NOTE]
> Les images sont rognées à la largeur et la hauteur spécifiée, et les couleurs sont ajustées pour utiliser les couleurs de barre d’outils standard (16 couleurs).

Par défaut, un nouveau bouton vide s’affiche à l’extrémité droite de la barre d’outils. Vous pouvez déplacer ce bouton avant de le modifier. Lorsque vous créez un nouveau bouton, un autre bouton vide s’affiche à droite du bouton modifié. Lorsque vous enregistrez une barre d’outils, le bouton vide n’est pas enregistré.

Un bouton de barre d’outils a les propriétés suivantes :

|Propriété|Description|
|--------------|-----------------|
|**ID**|Définit l’ID du bouton. La liste déroulante fournit courantes **ID** noms.|
|**Width**|Définit la largeur du bouton. valeur recommandée : 16 pixels.|
|**Height**|Définit la hauteur du bouton. La hauteur d’un bouton change la hauteur de tous les boutons de la barre d’outils. valeur recommandée : 15 pixels.|
|**Invite**|Définit le message affiché dans la barre d’état. Ajout de *\n* et ajoute un nom d’un **info-bulle** à ce bouton de barre d’outils. Pour plus d’informations, consultez [création d’une info-bulle](../windows/creating-a-tool-tip-for-a-toolbar-button.md).|

**Largeur** et **hauteur** s’appliquent à tous les boutons. Une image bitmap qui sert à créer une barre d’outils a une largeur maximale de 2048, ainsi si vous définissez la largeur du bouton *512*, vous ne pouvez avoir quatre boutons et si vous définissez la largeur sur *513*, vous ne pouvez avoir trois boutons.

## <a name="how-to"></a>Comment

Le **barre d’outils Éditeur** vous permet de :

### <a name="to-create-new-toolbars"></a>Pour créer des barres d’outils

1. Dans **affichage des ressources**, cliquez sur votre *.rc* de fichier et choisissez **ajouter une ressource**. Si vous avez une barre d’outils existante dans votre *.rc* fichier, vous pouvez cliquer sur le **barre d’outils** dossier et sélectionnez **insérer une barre d’outils**.

1. Dans le **ajouter une ressource** boîte de dialogue, sélectionnez **barre d’outils** dans le **Type de ressource** liste, puis choisissez **New**.

   Si un signe plus ( **+** ) apparaît en regard du **barre d’outils** type de ressource, cela signifie que les modèles de la barre d’outils sont disponibles. Sélectionnez le signe plus pour développer la liste des modèles, sélectionnez un modèle et choisissez **New**.

### <a name="to-convert-bitmaps-to-toolbar-resources"></a>Pour convertir des bitmaps en ressources de barre d’outils

1. Ouvrez une ressource bitmap existante dans le [Éditeur d’images](../windows/image-editor-for-icons.md). Si l’image bitmap n’est pas déjà dans votre *.rc* de fichiers, cliquez sur le *.rc* de fichier et choisissez **importation**, puis accédez à l’image bitmap que vous souhaitez ajouter à votre *.rc*  fichier et sélectionnez **Open**.

1. Accédez au menu **Image** > **barre d’outils Éditeur**.

   Le **nouvelle ressource de barre d’outils** boîte de dialogue s’affiche. Vous pouvez modifier la largeur et la hauteur des images d’icône pour faire correspondre l’image bitmap. L’image de la barre d’outils est alors affichée dans le **barre d’outils Éditeur**.

1. Pour terminer la conversion, modifiez la commande **ID** du bouton en utilisant la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Tapez le nouveau *ID* ou sélectionnez un **ID** dans la liste déroulante.

   > [!TIP]
   > Le **propriétés** fenêtre contient un bouton punaise dans la barre de titre et la sélection de cette option active ou désactive **Masquer automatiquement** pour la fenêtre. Pour faire défiler toutes les propriétés de bouton de barre d’outils sans rouvrir les fenêtres de propriétés individuelles, activer **Masquer automatiquement** désactivé afin que la **propriétés** fenêtre reste visible.

   Vous pouvez également modifier les ID de commande des boutons sur la nouvelle barre d’outils à l’aide de la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window).

### <a name="to-manage-toolbar-buttons"></a>Pour gérer des boutons de barre d’outils

#### <a name="to-create-a-new-toolbar-button"></a>Pour créer un nouveau bouton de barre d’outils

1. Dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources) développez le dossier des ressources (par exemple, *Project1.rc*).

1. Développez le **barre d’outils** dossier et sélectionnez une barre d’outils à modifier, puis effectuez l’une des opérations suivantes :

   - Affecter un ID au bouton vide à l’extrémité droite de la barre d’outils. Vous pouvez le faire en modifiant le **ID** propriété dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Par exemple, vous souhaiterez donner à un bouton de barre d’outils le même ID qu’une option de menu. Dans ce cas, utilisez la zone de liste déroulante pour sélectionner le **ID** de l’option de menu.

   - Sélectionnez le bouton vide à l’extrémité droite de la barre d’outils dans le **affichage de la barre d’outils** volet et commencez à dessiner. Un ID de commande du bouton par défaut est attribué (ID_BUTTON\<n >).

#### <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>Pour ajouter une image à une barre d’outils en tant que bouton

1. Dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources), ouvrez la barre d’outils en double-cliquant dessus.

1. Ensuite, ouvrez l’image que vous souhaitez ajouter à votre barre d’outils.

   > [!NOTE]
   > Si vous ouvrez l’image dans Visual Studio, il s’ouvre dans le **Éditeur d’images**. Vous pouvez également ouvrir l’image dans d’autres programmes graphiques.

1. Accédez au menu **modifier** > **copie**.

1. Basculez vers votre barre d’outils en sélectionnant son onglet en haut de la fenêtre source.

1. Accédez au menu **modifier** > **coller**.

   L’image s’affiche dans votre barre d’outils en tant que nouveau bouton.

#### <a name="to-move-a-toolbar-button"></a>Pour déplacer un bouton de barre d’outils

Dans le **affichage de la barre d’outils** volet, faites glisser le bouton que vous souhaitez déplacer vers son nouvel emplacement sur la barre d’outils.

- Pour copier des boutons d’une barre d’outils, maintenez la **Ctrl** clé puis, dans le **affichage de la barre d’outils** volet, faites glisser le bouton vers son nouvel emplacement dans la barre d’outils ou à un emplacement sur une autre barre d’outils.

- Pour supprimer un bouton de barre d’outils, cliquez sur le bouton de barre d’outils et faites-le glisser en dehors de la barre d’outils.

- Pour insérer ou supprimer l’espace entre les boutons sur une barre d’outils, soit les faire glisser vers l’extérieur ou vers l’autre sur la barre d’outils.

|Action|Étape|
|------|------|
|Pour insérer un espace avant un bouton qui n’est pas suivi d’un espace|Faites glisser le bouton à droite ou vers le bas jusqu'à ce qu’il chevauche le bouton suivant sur à mi-chemin.|
|Pour insérer un espace avant un bouton qui est suivi par un espace et pour conserver l’espace de fin|Faites glisser le bouton jusqu'à ce que le bord droit ou inférieur touche simplement le bouton suivant ou superpose à ce dernier.|
|Pour insérer un espace avant un bouton qui est suivi par un espace et fermer espace suivant|Faites glisser le bouton à droite ou vers le bas jusqu'à ce qu’il chevauche le bouton suivant sur à mi-chemin.|
|Pour supprimer un espace entre les boutons sur une barre d’outils|Faites glisser le bouton sur le côté « un » de l’espace vers le bouton de l’autre côté de l’espace jusqu'à ce qu’il chevauche le bouton suivant vers la moitié.|

> [!NOTE]
> Si aucun espace n’est sur le côté du bouton que vous faites glisser hors du et que vous faites glisser le bouton plus de la moitié du bouton adjacent, le **barre d’outils Éditeur** insère un espace sur le côté opposé du bouton que vous faites glisser.

#### <a name="to-change-the-properties-of-a-toolbar-button"></a>Pour modifier les propriétés d’un bouton de barre d’outils

1. Dans un projet C++, sélectionnez le bouton de barre d’outils.

1. Tapez le nouvel ID dans le **ID** propriété dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), ou utilisez la liste déroulante pour sélectionner un nouveau **ID**.

#### <a name="to-create-a-tool-tip-for-a-toolbar-button"></a>Pour créer une info-bulle pour un bouton de barre d’outils

1. Sélectionnez le bouton de barre d’outils.

1. Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), dans le **invite** champ, ajoutez une description du bouton de la barre d’état et après le message, ajoutez `\n` et l’info-bulle nom.

Par exemple, pour afficher l’info-bulle pour le **impression** situé dans **WordPad**:

1. Ouvrez **WordPad**.

1. Placez le pointeur de la souris sur le **impression** bouton de barre d’outils et notez le mot `Print` s’affiche sous le pointeur de la souris.

1. Examinez la barre d’état en bas de la **WordPad** fenêtre et notez qu’il affiche maintenant le texte `Prints the active document`.

`Print` est le nom de l’info-bulle outil et `Prints the active document` est la description du bouton de la barre d’état.

Si vous souhaitez que cet effet à l’aide de la **barre d’outils Éditeur**, définissez le **invite** propriété `Prints the active document\nPrint`.

## <a name="requirements"></a>Configuration requise

MFC ou ATL

## <a name="see-also"></a>Voir aussi

[Éditeurs de ressources](../windows/resource-editors.md)
[Menus et autres ressources](/windows/desktop/menurc/resources)<br/>
[propriétés d’un bouton de barre d’outils](../windows/toolbar-button-properties.md)<br/>

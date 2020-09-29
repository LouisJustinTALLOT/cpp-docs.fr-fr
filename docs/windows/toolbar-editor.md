---
title: Éditeur de barres d’outils (C++)
description: Utilisez l’éditeur de barres d’outils de Visual Studio pour créer des ressources de barre d’outils et convertir des bitmaps en ressources de barre d’outils.
ms.date: 09/26/2020
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
ms.openlocfilehash: 042bfafb1e55d45145306a8c388e1e3559fa9a33
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91413799"
---
# <a name="toolbar-editor-c"></a>Éditeur de barres d’outils (C++)

L' **éditeur de barres d'** outils vous permet de créer des ressources de barre d’outils et de convertir des bitmaps en ressources de barre d’outils. L' **éditeur de barres d’outils** utilise un affichage graphique. Il affiche une barre d’outils et des boutons qui ressemblent à la façon dont ils s’affichent dans une application finie.

La fenêtre de l' **éditeur de barres d’outils** affiche deux vues d’une image de bouton, identique à la fenêtre de l' **éditeur d’images** . Une barre de fractionnement sépare les deux volets. Pour modifier les tailles relatives des volets, vous pouvez faire glisser la barre de fractionnement d’un côté à l’autre. Le volet actif affiche une bordure de sélection et au-dessus des deux affichages de l’image est la barre d’outils objet.

![Éditeur de barres d’outils](../mfc/media/vctoolbareditor.gif "vcToolbarEditor")<br/>
**Éditeur de barres d’outils**

L' **éditeur de barres d’outils** est semblable à l' **éditeur d’images** dans fonctionnalité. Les éléments de menu, les outils graphiques et la grille bitmap entre les deux sont les mêmes. Il existe une commande de menu dans le menu **image** pour basculer entre l' **éditeur de barres d’outils** et l' **éditeur d’images**. Pour plus d’informations sur l’utilisation de la barre d’outils **graphiques** , la palette de **couleurs** ou le menu **image** , consultez [éditeur d’images](../windows/image-editor-for-icons.md).

Vous pouvez créer une nouvelle barre d’outils dans un projet C++ en convertissant une bitmap. Le graphique de la bitmap est converti en images de bouton pour une barre d’outils. En règle générale, la bitmap contient plusieurs images de bouton sur une seule bitmap, avec une image pour chaque bouton. Les images peuvent avoir n’importe quelle taille, car la valeur par défaut est de 16 pixels de largeur et la hauteur de l’image. Vous pouvez spécifier la taille des images de bouton dans la boîte de dialogue **nouvelle ressource de barre d’outils** . Pour spécifier des tailles, choisissez **éditeur de barres d’outils** dans le menu **image** , dans l' **éditeur d’images**.

La boîte de dialogue **nouvelle ressource de barre d’outils** vous permet de spécifier la largeur et la hauteur des boutons que vous ajoutez à une ressource de barre d’outils dans un projet C++. La valeur par défaut est 16 × 15 pixels.

Une bitmap utilisée pour créer une barre d’outils a une largeur maximale de 2048. Si vous définissez la **largeur du bouton** sur *512*, vous ne pouvez avoir que quatre boutons. Et, si vous définissez la largeur sur *513*, vous ne pouvez avoir que trois boutons.

La boîte **de dialogue nouvelle ressource de barre d’outils** présente les propriétés suivantes :

|Property|Description|
|---|---------------|
|**Largeur du bouton**|Offre un espace vous permettant d’entrer la largeur des boutons de la barre d’outils que vous convertissez d’une ressource bitmap en ressource de barre d’outils.|
|**Hauteur du bouton**|Offre un espace vous permettant d’entrer la hauteur des boutons de la barre d’outils que vous convertissez d’une ressource bitmap en ressource de barre d’outils.|

> [!NOTE]
> Les images sont rognées à la largeur et à la hauteur spécifiées, et les couleurs sont ajustées pour utiliser les couleurs de barre d’outils standard (16 couleurs).

Par défaut, une barre d’outils affiche un bouton nouveau ou vide à l’extrémité droite de la barre d’outils. Vous pouvez déplacer ce bouton avant de le modifier. Lorsque vous créez un nouveau bouton, un autre bouton vide apparaît à droite du bouton modifié. Le bouton vide n’est pas enregistré lorsque vous enregistrez une barre d’outils.

Un bouton de barre d’outils a les propriétés suivantes :

|Property|Description|
|--------------|-----------------|
|**Identifiant**|Définit l’ID du bouton. La liste déroulante répertorie les noms d' **ID** courants.|
|**Width**|Définit la largeur du bouton. 16 pixels recommandés.|
|**Height**|Définit la hauteur du bouton. La hauteur d’un bouton modifie la hauteur de tous les boutons de la barre d’outils. 15 pixels sont recommandés.|
|**Demander**|Définit le message affiché dans la barre d’État. L’ajout de *\n* et d’un nom ajoute une **info-bulle** à ce bouton de barre d’outils. Pour plus d’informations, consultez [pour créer une info-bulle pour un bouton de barre d’outils](#to-create-a-tool-tip-for-a-toolbar-button).|

**Width** et **Height** s’appliquent à tous les boutons. Une bitmap utilisée pour créer une barre d’outils a une largeur maximale de 2048. Cela signifie que si vous définissez la largeur du bouton sur *512*, vous ne pouvez avoir que quatre boutons. Si vous définissez la largeur sur *513*, vous ne pouvez avoir que trois boutons.

## <a name="how-to"></a>Procédure

L' **éditeur de barres d’outils** vous permet d’activer les éléments suivants :

### <a name="to-create-new-toolbars"></a>Pour créer des barres d’outils

1. Dans **affichage des ressources**, cliquez avec le bouton droit sur votre fichier *. RC* , puis choisissez **Ajouter une ressource**. Si vous avez une barre d’outils existante dans votre fichier *. RC* , vous pouvez cliquer avec le bouton droit sur le dossier de la **barre d'** outils et sélectionner **Insérer une barre d’outils**.

1. Dans la boîte de dialogue **Ajouter une ressource** , sélectionnez **barre d’outils** dans la liste **type de ressource** , puis choisissez **nouveau**.

   Si un signe plus ( **+** ) s’affiche en regard du type de ressource de **barre d’outils** , cela signifie que les modèles de barre d’outils sont disponibles. Sélectionnez le signe plus (+) pour développer la liste des modèles, sélectionnez un modèle, puis choisissez **nouveau**.

### <a name="to-convert-bitmaps-to-toolbar-resources"></a>Pour convertir des bitmaps en ressources de barre d’outils

1. Ouvrez une ressource bitmap existante dans l' [éditeur d’images](../windows/image-editor-for-icons.md). Si l’image bitmap n’est pas déjà dans votre fichier *. RC* , cliquez avec le bouton droit sur le fichier *. RC* , puis choisissez **Importer**. Ensuite, accédez à l’image bitmap que vous souhaitez ajouter à votre fichier *. RC* , puis sélectionnez **ouvrir**.

1. Accédez à l' **Image**  >  **éditeur de barre d’outils**image de menu.

   La boîte **de dialogue nouvelle ressource de barre d’outils** s’affiche. Vous pouvez modifier la largeur et la hauteur des images d’icône pour qu’elles correspondent à la bitmap. L’image de la barre d’outils est ensuite affichée dans l' **éditeur de barres d’outils**.

1. Pour terminer la conversion, modifiez l' **ID** de commande du bouton à l’aide de l' [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Tapez le nouvel *ID* ou sélectionnez un **ID** dans la liste déroulante.

   > [!TIP]
   > La fenêtre **Propriétés** contient un bouton Punaise dans la barre de titre et sélectionne cette option active ou désactive **Masquer automatiquement** pour la fenêtre. Pour parcourir toutes les propriétés du bouton de barre d’outils sans avoir à rouvrir les fenêtres de propriétés individuelles, désactivez **Masquer automatiquement** pour que la fenêtre **Propriétés** reste immobile.

   Vous pouvez également modifier les ID de commande des boutons sur la nouvelle barre d’outils à l’aide de l' [fenêtre Propriétés](/visualstudio/ide/reference/properties-window).

### <a name="to-manage-toolbar-buttons"></a>Pour gérer les boutons de barre d’outils

#### <a name="to-create-a-new-toolbar-button"></a>Pour créer un bouton de barre d’outils

1. Dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources) développez le dossier des ressources (par exemple, *Project1. RC*).

1. Développez le dossier de la **barre d’outils** et sélectionnez une barre d’outils à modifier, puis effectuez l’une des opérations suivantes :

   - Attribuez un ID au bouton vide à l’extrémité droite de la barre d’outils. Pour ce faire, vous pouvez modifier la propriété **ID** dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Par exemple, il se peut que vous souhaitiez attribuer à un bouton de barre d’outils le même ID qu’une option de menu. Dans ce cas, utilisez la zone de liste déroulante pour sélectionner l' **ID** de l’option de menu.

   - Sélectionnez le bouton vide à l’extrémité droite de la barre d’outils dans le volet **d’affichage de la barre d’outils** et commencez le dessin. Un ID de commande de bouton par défaut est affecté (ID_BUTTON \<n> ).

#### <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>Pour ajouter une image à une barre d’outils sous forme de bouton

1. Dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources), double-cliquez sur la barre d’outils pour l’ouvrir.

1. Ensuite, ouvrez l’image que vous souhaitez ajouter à votre barre d’outils.

   > [!NOTE]
   > Si vous ouvrez l’image dans Visual Studio, elle s’ouvre dans l' **éditeur d’images**. Vous pouvez également ouvrir l’image dans d’autres programmes graphiques.

1. Accédez au menu **modifier**la  >  **copie**.

1. Basculez vers votre barre d’outils en sélectionnant son onglet en haut de la fenêtre source.

1. Accédez au menu **Edition**  >  **coller**.

   L’image s’affiche dans la barre d’outils en tant que nouveau bouton.

#### <a name="to-move-a-toolbar-button"></a>Pour déplacer un bouton de barre d’outils

Dans le volet **d’affichage de la barre d’outils** , faites glisser le bouton que vous souhaitez déplacer vers son nouvel emplacement dans la barre d’outils.

- Pour copier des boutons d’une barre d’outils, maintenez la touche **CTRL** enfoncée. Dans le volet **d’affichage de la barre d’outils** , faites glisser le bouton vers son nouvel emplacement dans la barre d’outils. Ou faites-le glisser vers un emplacement sur une autre barre d’outils.

- Pour supprimer un bouton de barre d’outils, cliquez sur le bouton de barre d’outils et faites-le glisser en dehors de la barre d’outils.

- Pour insérer ou supprimer un espace entre les boutons d’une barre d’outils, faites-les glisser à partir de ou vers l’autre dans la barre d’outils.

|Action|Étape|
|------|------|
|Pour insérer un espace avant un bouton qui n’est pas suivi d’un espace|Faites glisser le bouton vers la droite ou vers le dessous jusqu’à ce qu’il chevauche le bouton suivant à mi-chemin.|
|Pour insérer un espace avant un bouton qui est suivi d’un espace et pour conserver l’espace de fin|Faites glisser le bouton jusqu’à ce que le bord droit ou inférieur touche simplement le bouton suivant ou le chevauche.|
|Pour insérer un espace avant un bouton qui est suivi d’un espace et pour fermer l’espace suivant|Faites glisser le bouton vers la droite ou vers le dessous jusqu’à ce qu’il chevauche le bouton suivant à mi-chemin.|
|Pour supprimer un espace entre les boutons d’une barre d’outils|Sélectionnez le bouton d’un côté de l’espace. Faites-le glisser vers le bouton situé à l’autre extrémité de l’espace jusqu’à ce qu’il chevauche le bouton suivant à mi-chemin.|

> [!NOTE]
> S’il n’y a pas d’espace sur le côté du bouton que vous faites glisser et que vous faites glisser le bouton à mi-chemin après le bouton adjacent, l' **éditeur de barre d’outils** insère un espace sur le côté opposé du bouton que vous faites glisser.

#### <a name="to-change-the-properties-of-a-toolbar-button"></a>Pour modifier les propriétés d’un bouton de barre d’outils

1. Dans un projet C++, sélectionnez le bouton de barre d’outils.

1. Tapez le nouvel ID dans la propriété **ID** de la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), ou utilisez la liste déroulante pour sélectionner un nouvel **ID**.

#### <a name="to-create-a-tool-tip-for-a-toolbar-button"></a>Pour créer une info-bulle pour un bouton de barre d’outils

1. Sélectionnez le bouton de barre d’outils.

1. Dans le champ **invite** de la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), ajoutez une description du bouton pour la barre d’État et après le message, ajoutez `\n` et le nom de l’info-bulle.

Par exemple, pour afficher l’info-bulle du bouton **Imprimer** dans **WordPad**:

1. Ouvrez **WordPad**.

1. Placez le pointeur de la souris sur le bouton **Imprimer** de la barre d’outils et notez que le mot `Print` est maintenant flottant sous le pointeur de la souris.

1. Examinez la barre d’État en bas de la fenêtre **WordPad** et Notez qu’elle affiche maintenant le texte `Prints the active document` .

`Print` est le nom de l’info-bulle et `Prints the active document` est la description du bouton pour la barre d’État.

Si vous souhaitez utiliser cet effet à l’aide de l' **éditeur de barres d’outils**, affectez à la propriété **prompt** la valeur `Prints the active document\nPrint` .

## <a name="requirements"></a>Spécifications

MFC ou ATL

## <a name="see-also"></a>Voir aussi

[Éditeurs de ressources](../windows/resource-editors.md)\
[Menus et autres ressources](/windows/win32/menurc/resources)

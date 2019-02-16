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
ms.openlocfilehash: 7ef08551960c9308a84b9838249a3d9ff4950d98
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320612"
---
# <a name="toolbar-editor-c"></a>Éditeur de la barre d’outils (C++)

Le **barre d’outils** éditeur vous permet de créer des ressources de barre d’outils C++ et convertir des bitmaps en ressources de barre d’outils. Le **barre d’outils** éditeur utilise un affichage graphique pour afficher une barre d’outils et les boutons qui ressemblent étroitement à la façon dont ils regarde dans une application finie.

Le **barre d’outils** fenêtre de l’éditeur affiche deux vues d’une image du bouton, identique à la fenêtre d’éditeur d’Image. Une barre de fractionnement sépare les deux volets. Vous pouvez faire glisser la barre de fractionnement pour modifier la taille des volets. Une bordure de sélection entoure le volet actif. Au-dessus des deux affichages de l’image figure la barre d’outils de sujet.

![Barre d’outils Éditeur](../mfc/media/vctoolbareditor.gif "vcToolbarEditor") éditeur de la barre d’outils

Le **barre d’outils** éditeur est similaire à la **Image** éditeur dans la fonctionnalité. Les éléments de menu, outils de graphique et grille de bitmap sont les mêmes que celles figurant dans le **Image** éditeur. Il existe une commande de menu le **Image** menu vous permet de basculer entre le **barre d’outils** éditeur et le **Image** éditeur. Pour plus d’informations sur l’utilisation de la **Graphics** barre d’outils, **couleurs** palette, ou **Image** menu, consultez [Éditeur d’images](../windows/image-editor-for-icons.md).

Vous pouvez créer une nouvelle barre d’outils dans un projet C++ en convertissant une image bitmap. Le graphique à partir de l’image bitmap convertit les images du bouton d’une barre d’outils. L’image bitmap contient généralement plusieurs images de bouton sur une seule bitmap, avec une seule image pour chaque bouton. Images peuvent être n’importe quelle taille que la valeur par défaut est 16 pixels de large et la hauteur de l’image. Vous pouvez spécifier la taille des images de bouton dans le **nouvelle ressource de barre d’outils** boîte de dialogue lorsque vous choisissez **barre d’outils Éditeur** à partir de la **Image** menu dans l’éditeur d’images.

Le **nouvelle ressource de barre d’outils** boîte de dialogue vous permet de spécifier la largeur et la hauteur des boutons que vous ajoutez à une ressource de barre d’outils dans un projet C++. La valeur par défaut est 16 x 15 pixels.

Une image bitmap qui sert à créer une barre d’outils a une largeur maximale de 2048. Par conséquent, si vous définissez la **la largeur du bouton** à 512, vous ne pouvez avoir quatre boutons. Si vous définissez la largeur à 513, peut uniquement avoir trois boutons.

La boîte de dialogue a les propriétés suivantes :

|Propriété|Description|
|---|---|
|**Largeur du bouton**|Fournit un espace vous permettant d’entrer la largeur pour les boutons de barre d’outils que vous voulez convertir à partir d’une ressource bitmap en une ressource de barre d’outils. Les images sont rognées à la largeur et la hauteur spécifiée, et les couleurs sont ajustées pour utiliser les couleurs de barre d’outils standard (16 couleurs).|
|**Hauteur du bouton**|Fournit un espace vous permettant d’entrer la hauteur pour les boutons de barre d’outils que vous voulez convertir à partir d’une ressource bitmap en une ressource de barre d’outils. Les images sont rognées à la largeur et la hauteur spécifiée, et les couleurs sont ajustées pour utiliser les couleurs de barre d’outils standard (16 couleurs).|

Par défaut, un nouveau bouton vide s’affiche à l’extrémité droite de la barre d’outils. Vous pouvez déplacer ce bouton avant de le modifier. Lorsque vous créez un nouveau bouton, un autre bouton vide s’affiche à droite du bouton modifié. Lorsque vous enregistrez une barre d’outils, le bouton vide n’est pas enregistré.

Les propriétés d’un bouton de barre d’outils sont :

|Propriété|Description|
|--------------|-----------------|
|**ID**|Définit l’ID du bouton. La liste déroulante fournit courantes **ID** noms.|
|**Width**|Définit la largeur du bouton. valeur recommandée : 16 pixels.|
|**Height**|Définit la hauteur du bouton. La hauteur d’un bouton change la hauteur de tous les boutons de la barre d’outils. valeur recommandée : 15 pixels.|
|**Invite**|Définit le message affiché dans la barre d’état. Ajout de \n et un nom ajoute une info-bulle à ce bouton de barre d’outils. Pour plus d’informations, consultez [création d’une info-bulle](../windows/creating-a-tool-tip-for-a-toolbar-button.md).|

**Largeur** et **hauteur** s’appliquent à tous les boutons. Une image bitmap qui sert à créer une barre d’outils a une largeur maximale de 2048. Par conséquent, si vous définissez la largeur du bouton à 512, vous ne pouvez avoir que quatre boutons et si vous définissez la largeur à 513, vous ne pouvez avoir trois boutons.

## <a name="how-to"></a>Procédure

Le **barre d’outils** éditeur vous permet de :

### <a name="to-create-new-toolbars"></a>Pour créer des barres d’outils

1. Dans **ressource** afficher, cliquez sur votre fichier .rc, puis choisissez **ajouter une ressource** dans le menu contextuel. (Si vous avez une barre d’outils existante dans votre fichier .rc, vous pouvez simplement cliquer sur le **barre d’outils** dossier et sélectionnez **insérer une barre d’outils** dans le menu contextuel.)

1. Dans le **ajouter une ressource** boîte de dialogue, sélectionnez **barre d’outils** dans le **Type de ressource** liste, puis choisissez **New**.

   Si un signe plus (**+**) apparaît en regard du **barre d’outils** type de ressource, cela signifie que les modèles de la barre d’outils sont disponibles. Sélectionnez le signe plus pour développer la liste des modèles, sélectionnez un modèle et choisissez **New**.

### <a name="to-convert-bitmaps-to-toolbar-resources"></a>Pour convertir des bitmaps en ressources de barre d’outils

1. Ouvrez une ressource bitmap existante dans le [Éditeur d’images](../windows/image-editor-for-icons.md). (Si la bitmap n’est pas déjà dans votre fichier .rc, cliquez sur le fichier .rc, choisissez **importation** dans le menu contextuel, accédez à l’image bitmap que vous souhaitez ajouter à votre fichier .rc, puis sélectionnez **Open**.)

1. À partir de la **Image** menu, choisissez **barre d’outils Éditeur**.

   Le **nouvelle ressource de barre d’outils** boîte de dialogue s’affiche. Vous pouvez modifier la largeur et la hauteur des images d’icône pour faire correspondre l’image bitmap. L’image de la barre d’outils s’affiche ensuite dans l’éditeur de la barre d’outils.

1. Pour terminer la conversion, modifiez la commande **ID** du bouton en utilisant la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Tapez le nouveau **ID** ou sélectionnez un **ID** dans la liste déroulante.

   > [!TIP]
   > Le **propriétés** fenêtre contient un bouton punaise dans la barre de titre. Cliquez sur ce bouton Active ou désactive **Masquer automatiquement** pour la fenêtre. Pour parcourir rapidement toutes les propriétés de bouton de barre d’outils sans rouvrir les fenêtres de propriétés individuelles, activer **Masquer automatiquement** désactivé afin que la **propriétés** fenêtre reste visible.

Vous pouvez également modifier les ID de commande des boutons sur la nouvelle barre d’outils à l’aide de la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window).

### <a name="to-create-move-and-edit-toolbar-buttons"></a>Pour créer, déplacer et modifier des boutons de barre d’outils

Vous pouvez facilement créer, déplacer, copier et modifier des boutons de barre d’outils :

#### <a name="to-create-a-new-toolbar-button"></a>Pour créer un nouveau bouton de barre d’outils

1. Dans [affichage des ressources](../windows/resource-view-window.md) développez le dossier des ressources (par exemple, *Project1.rc*).

1. Développez le **barre d’outils** dossier et sélectionnez une barre d’outils à modifier.

1. Affecter un ID au bouton vide à l’extrémité droite de la barre d’outils. Vous pouvez le faire en modifiant le **ID** propriété dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Par exemple, vous souhaiterez donner à un bouton de barre d’outils le même ID qu’une option de menu. Dans ce cas, utilisez la zone de liste déroulante pour sélectionner le **ID** de l’option de menu.

   ou

   Sélectionnez le bouton vide à l’extrémité droite de la barre d’outils (dans le **affichage de la barre d’outils** volet) et commencez à dessiner. Un ID de commande du bouton par défaut est attribué (ID_BUTTON\<n >).

Vous pouvez également copier et coller une image sur une barre d’outils en tant que nouveau bouton.

#### <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>Pour ajouter une image à une barre d’outils en tant que bouton

1. Dans [affichage des ressources](../windows/resource-view-window.md), ouvrez la barre d’outils en double-cliquant dessus.

1. Ensuite, ouvrez l’image que vous souhaitez ajouter à votre barre d’outils.

   > [!NOTE]
   > Si vous ouvrez l’image dans Visual Studio, il s’ouvre dans le **Image** éditeur. Vous pouvez également ouvrir l’image dans d’autres programmes graphiques.

1. À partir de la **modifier** menu, choisissez **copie**.

1. Basculez vers votre barre d’outils en sélectionnant son onglet en haut de la fenêtre source.

1. À partir de la **modifier** menu, choisissez **coller**.

   L’image s’affiche dans votre barre d’outils en tant que nouveau bouton.

#### <a name="to-move-a-toolbar-button"></a>Pour déplacer un bouton de barre d’outils

Dans le **affichage de la barre d’outils** volet, faites glisser le bouton que vous souhaitez déplacer vers son nouvel emplacement sur la barre d’outils.

#### <a name="to-copy-buttons-from-a-toolbar"></a>Pour copier des boutons d’une barre d’outils

1. Maintenez la **Ctrl** clé.

1. Dans le **affichage de la barre d’outils** volet, faites glisser le bouton vers son nouvel emplacement dans la barre d’outils ou à un emplacement sur une autre barre d’outils.

#### <a name="to-delete-a-toolbar-button"></a>Pour supprimer un bouton de barre d’outils

Sélectionnez le bouton de barre d’outils et faites-le glisser en dehors de la barre d’outils.

#### <a name="to-insert-or-remove-space-between-buttons-on-a-toolbar"></a>Pour insérer ou supprimer l’espace entre les boutons sur une barre d’outils

En règle générale, pour insérer un espace entre les boutons, faites-les glisser en dehors de l’autre sur la barre d’outils. Pour supprimer l’espace, faites-les glisser vers l’autre.

|Action|Étape|
|------|------|
|Pour insérer un espace avant un bouton qui n’est pas suivi d’un espace|Faites glisser le bouton à droite ou vers le bas jusqu'à ce qu’il chevauche le bouton suivant sur à mi-chemin.|
|Pour insérer un espace avant un bouton qui est suivi par un espace et pour conserver l’espace de fin|Faites glisser le bouton jusqu'à ce que le bord droit ou inférieur touche simplement le bouton suivant ou superpose à ce dernier.|
|Pour insérer un espace avant un bouton qui est suivi par un espace et fermer espace suivant|Faites glisser le bouton à droite ou vers le bas jusqu'à ce qu’il chevauche le bouton suivant sur à mi-chemin.|
|Pour supprimer un espace entre les boutons sur une barre d’outils|Faites glisser le bouton sur le côté « un » de l’espace vers le bouton de l’autre côté de l’espace jusqu'à ce qu’il chevauche le bouton suivant vers la moitié.|

> [!NOTE]
> S’il n’existe aucun espace sur le côté du bouton que vous faites glisser hors du, et que vous faites glisser le bouton plus de la moitié du bouton adjacent, le **barre d’outils** éditeur insère également un espace sur le côté opposé du bouton sur lequel vous êtes en faisant glisser.

#### <a name="to-change-the-properties-of-a-toolbar-button"></a>Pour modifier les propriétés d’un bouton de barre d’outils

1. Dans un projet C++, sélectionnez le bouton de barre d’outils.

1. Tapez le nouvel ID dans le **ID** propriété dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), ou utilisez la liste déroulante pour sélectionner un nouveau **ID**.

#### <a name="to-create-a-tool-tip-for-a-toolbar-button"></a>Pour créer une info-bulle pour un bouton de barre d’outils

1. Sélectionnez le bouton de barre d’outils.

1. Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), dans le **invite** champ de propriété, ajoutez une description du bouton de la barre d’état ; après le message, ajoutez `\n` et l’info-bulle nom.

Un exemple courant d’une info-bulle est le **impression** situé dans **WordPad**:

1. Ouvrez **WordPad**.

1. Placez le pointeur de la souris sur le **impression** bouton de barre d’outils.

1. Notez que le mot `Print` s’affiche sous le pointeur de la souris.

1. Examinez la barre d’état (en bas de la **WordPad** fenêtre)-il affiche le texte `Prints the active document`.

Le `Print` dans **étape 3** est « info-bulle nom » et le `Prints the active document` de **étape 4** est « description du bouton de la barre d’état. »

Si vous souhaitez que cet effet à l’aide de la **barre d’outils** éditeur, vous définissez le **invite** propriété `Prints the active document\nPrint`.

> [!NOTE]
> Vous pouvez modifier le texte d’invite à l’aide de la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window).

## <a name="requirements"></a>Spécifications

MFC ou ATL

## <a name="see-also"></a>Voir aussi

[Éditeurs de ressources](../windows/resource-editors.md)<br/>
[Menus et autres ressources](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)<br/>
[propriétés d’un bouton de barre d’outils](../windows/toolbar-button-properties.md)<br/>

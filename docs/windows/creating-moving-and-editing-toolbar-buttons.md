---
title: Création, déplacement et modification de boutons de barre d’outils (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.toolbar
helpviewer_keywords:
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
ms.assetid: d0f0c6c6-9d7e-42b5-a86a-7558127386e7
ms.openlocfilehash: 2a67123e444ad208eaae74a24b72288f2dbb3bdb
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742698"
---
# <a name="creating-moving-and-editing-toolbar-buttons-c"></a>Création, déplacement et modification de boutons de barre d’outils (C++)

Vous pouvez facilement créer, déplacer, copier et modifier des boutons de barre d’outils.

Par défaut, un nouveau bouton vide s’affiche à l’extrémité droite de la barre d’outils. Vous pouvez déplacer ce bouton avant de le modifier. Lorsque vous créez un nouveau bouton, un autre bouton vide s’affiche à droite du bouton modifié. Lorsque vous enregistrez une barre d’outils, le bouton vide n’est pas enregistré.

Les propriétés d’un bouton de barre d’outils sont :

|Propriété|Description|
|--------------|-----------------|
|**ID**|Définit l’ID du bouton. La liste déroulante fournit courantes **ID** noms.|
|**Width**|Définit la largeur du bouton. valeur recommandée : 16 pixels.|
|**Height**|Définit la hauteur du bouton. La hauteur d’un bouton change la hauteur de tous les boutons de la barre d’outils. valeur recommandée : 15 pixels.|
|**Invite**|Définit le message affiché dans la barre d’état. Ajout de \n et un nom ajoute une info-bulle à ce bouton de barre d’outils. Pour plus d’informations, consultez [création d’une info-bulle](../windows/creating-a-tool-tip-for-a-toolbar-button.md).|

**Largeur** et **hauteur** s’appliquent à tous les boutons. Une image bitmap qui sert à créer une barre d’outils a une largeur maximale de 2048. Par conséquent, si vous définissez la largeur du bouton à 512, vous ne pouvez avoir que quatre boutons et si vous définissez la largeur à 513, vous ne pouvez avoir trois boutons.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

Consultez les actions suivantes :

## <a name="to-create-a-new-toolbar-button"></a>Pour créer un nouveau bouton de barre d’outils

1. Dans [affichage des ressources](../windows/resource-view-window.md) développez le dossier des ressources (par exemple, *Project1.rc*).

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

1. Développez le **barre d’outils** dossier et sélectionnez une barre d’outils à modifier.

1. Affecter un ID au bouton vide à l’extrémité droite de la barre d’outils. Vous pouvez le faire en modifiant le **ID** propriété dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Par exemple, vous souhaiterez donner à un bouton de barre d’outils le même ID qu’une option de menu. Dans ce cas, utilisez la zone de liste déroulante pour sélectionner le **ID** de l’option de menu.

   ou

   Sélectionnez le bouton vide à l’extrémité droite de la barre d’outils (dans le **affichage de la barre d’outils** volet) et commencez à dessiner. Un ID de commande du bouton par défaut est attribué (ID_BUTTON\<n >).

Vous pouvez également copier et coller une image sur une barre d’outils en tant que nouveau bouton.

## <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>Pour ajouter une image à une barre d’outils en tant que bouton

1. Dans [affichage des ressources](../windows/resource-view-window.md), ouvrez la barre d’outils en double-cliquant dessus.

1. Ensuite, ouvrez l’image que vous souhaitez ajouter à votre barre d’outils.

   > [!NOTE]
   > Si vous ouvrez l’image dans Visual Studio, il s’ouvre dans le **Image** éditeur. Vous pouvez également ouvrir l’image dans d’autres programmes graphiques.

1. À partir de la **modifier** menu, choisissez **copie**.

1. Basculez vers votre barre d’outils en sélectionnant son onglet en haut de la fenêtre source.

1. À partir de la **modifier** menu, choisissez **coller**.

   L’image s’affiche dans votre barre d’outils en tant que nouveau bouton.

## <a name="to-move-a-toolbar-button"></a>Pour déplacer un bouton de barre d’outils

Dans le **affichage de la barre d’outils** volet, faites glisser le bouton que vous souhaitez déplacer vers son nouvel emplacement sur la barre d’outils.

## <a name="to-copy-buttons-from-a-toolbar"></a>Pour copier des boutons d’une barre d’outils

1. Maintenez la **Ctrl** clé.

1. Dans le **affichage de la barre d’outils** volet, faites glisser le bouton vers son nouvel emplacement dans la barre d’outils ou à un emplacement sur une autre barre d’outils.

## <a name="to-delete-a-toolbar-button"></a>Pour supprimer un bouton de barre d’outils

Sélectionnez le bouton de barre d’outils et faites-le glisser en dehors de la barre d’outils.

## <a name="to-insert-or-remove-space-between-buttons-on-a-toolbar"></a>Pour insérer ou supprimer l’espace entre les boutons sur une barre d’outils

En règle générale, pour insérer un espace entre les boutons, faites-les glisser en dehors de l’autre sur la barre d’outils. Pour supprimer l’espace, faites-les glisser vers l’autre.

### <a name="to-insert-a-space-before-a-button-that-isnt-followed-by-a-space"></a>Pour insérer un espace avant un bouton qui n’est pas suivi d’un espace

Faites glisser le bouton à droite ou vers le bas jusqu'à ce qu’il chevauche le bouton suivant sur à mi-chemin.

### <a name="to-insert-a-space-before-a-button-that-is-followed-by-a-space-and-to-keep-the-trailing-space"></a>Pour insérer un espace avant un bouton qui est suivi par un espace et pour conserver l’espace de fin

Faites glisser le bouton jusqu'à ce que le bord droit ou inférieur touche simplement le bouton suivant ou superpose à ce dernier.

### <a name="to-insert-a-space-before-a-button-that-is-followed-by-a-space-and-close-up-that-following-space"></a>Pour insérer un espace avant un bouton qui est suivi par un espace et fermer espace suivant

Faites glisser le bouton à droite ou vers le bas jusqu'à ce qu’il chevauche le bouton suivant sur à mi-chemin.

### <a name="to-remove-a-space-between-buttons-on-a-toolbar"></a>Pour supprimer un espace entre les boutons sur une barre d’outils

Faites glisser le bouton sur le côté « un » de l’espace vers le bouton de l’autre côté de l’espace jusqu'à ce qu’il chevauche le bouton suivant vers la moitié.

   S’il n’existe aucun espace sur le côté du bouton que vous faites glisser hors du, et que vous faites glisser le bouton plus de la moitié du bouton adjacent, le **barre d’outils** éditeur insère également un espace sur le côté opposé du bouton sur lequel vous êtes en faisant glisser.

## <a name="to-change-the-properties-of-a-toolbar-button"></a>Pour modifier les propriétés d’un bouton de barre d’outils

1. Dans un projet C++, sélectionnez le bouton de barre d’outils.

1. Tapez le nouvel ID dans le **ID** propriété dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), ou utilisez la liste déroulante pour sélectionner un nouveau **ID**.

## <a name="requirements"></a>Spécifications

MFC ou ATL

## <a name="see-also"></a>Voir aussi

[Éditeur de barres d’outils](../windows/toolbar-editor.md)

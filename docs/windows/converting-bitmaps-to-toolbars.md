---
title: Conversion de Bitmaps en barres d’outils (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.newtoolbarresource
helpviewer_keywords:
- bitmaps [C++], converting to toolbars
- Toolbar editor [C++], converting bitmaps
- toolbars [C++], converting bitmaps
- New Toolbar Resource dialog box [C++]
ms.assetid: 971c181b-40f5-44be-843d-677a7c235667
ms.openlocfilehash: 31b684ff72e970a6b09748b3925564b0b372d339
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702698"
---
# <a name="converting-bitmaps-to-toolbars-c"></a>Conversion de Bitmaps en barres d’outils (C++)

Vous pouvez créer une nouvelle barre d’outils dans un projet C++ en convertissant une image bitmap. Le graphique à partir de l’image bitmap convertit les images du bouton d’une barre d’outils. L’image bitmap contient généralement plusieurs images de bouton sur une seule bitmap, avec une seule image pour chaque bouton. Images peuvent être n’importe quelle taille ; la valeur par défaut est 16 pixels de large et la hauteur de l’image. Vous pouvez spécifier la taille des images de bouton dans le **nouvelle ressource de barre d’outils** boîte de dialogue lorsque vous choisissez **barre d’outils Éditeur** à partir de la **Image** menu dans l’éditeur d’images.

Le **nouvelle ressource de barre d’outils** boîte de dialogue vous permet de spécifier la largeur et la hauteur des boutons que vous ajoutez à une ressource de barre d’outils dans un projet C++. La valeur par défaut est 16 x 15 pixels.

Une image bitmap qui sert à créer une barre d’outils a une largeur maximale de 2048. Par conséquent, si vous définissez la **la largeur du bouton** à 512, vous ne pouvez avoir quatre boutons. Si vous définissez la largeur à 513, peut uniquement avoir trois boutons.

La boîte de dialogue a les propriétés suivantes :

|Propriété|Description|
|---|---|
|**Largeur du bouton**|Fournit un espace vous permettant d’entrer la largeur pour les boutons de barre d’outils que vous voulez convertir à partir d’une ressource bitmap en une ressource de barre d’outils. Les images sont rognées à la largeur et la hauteur spécifiée, et les couleurs sont ajustées pour utiliser les couleurs de barre d’outils standard (16 couleurs).|
|**Hauteur du bouton**|Fournit un espace vous permettant d’entrer la hauteur pour les boutons de barre d’outils que vous voulez convertir à partir d’une ressource bitmap en une ressource de barre d’outils. Les images sont rognées à la largeur et la hauteur spécifiée, et les couleurs sont ajustées pour utiliser les couleurs de barre d’outils standard (16 couleurs).|

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-convert-bitmaps-to-a-toolbar"></a>Pour convertir des bitmaps en une barre d’outils

1. Ouvrez une ressource bitmap existante dans le [Éditeur d’images](../windows/image-editor-for-icons.md). (Si la bitmap n’est pas déjà dans votre fichier .rc, cliquez sur le fichier .rc, choisissez **importation** dans le menu contextuel, accédez à l’image bitmap que vous souhaitez ajouter à votre fichier .rc, puis sélectionnez **Open**.)

1. À partir de la **Image** menu, choisissez **barre d’outils Éditeur**.

   Le **nouvelle ressource de barre d’outils** boîte de dialogue s’affiche. Vous pouvez modifier la largeur et la hauteur des images d’icône pour faire correspondre l’image bitmap. L’image de la barre d’outils s’affiche ensuite dans l’éditeur de la barre d’outils.

1. Pour terminer la conversion, modifiez la commande **ID** du bouton en utilisant la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Tapez le nouveau **ID** ou sélectionnez un **ID** dans la liste déroulante.

   > [!TIP]
   > Le **propriétés** fenêtre contient un bouton punaise dans la barre de titre. Cliquez sur ce bouton Active ou désactive **Masquer automatiquement** pour la fenêtre. Pour parcourir rapidement toutes les propriétés de bouton de barre d’outils sans rouvrir les fenêtres de propriétés individuelles, activer **Masquer automatiquement** désactivé afin que la **propriétés** fenêtre reste visible.

Vous pouvez également modifier les ID de commande des boutons sur la nouvelle barre d’outils à l’aide de la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Pour plus d’informations sur la modification de la nouvelle barre d’outils, consultez [création, déplacement et modification de boutons de barre d’outils](../windows/creating-moving-and-editing-toolbar-buttons.md).

## <a name="requirements"></a>Spécifications

MFC ou ATL

## <a name="see-also"></a>Voir aussi

[Création de nouvelles barres d’outils](../windows/creating-new-toolbars.md)<br/>
[Éditeur de barres d’outils](../windows/toolbar-editor.md)<br/>
[propriétés d’un bouton de barre d’outils](../windows/toolbar-button-properties.md)<br/>

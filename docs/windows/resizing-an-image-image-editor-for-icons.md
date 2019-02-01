---
title: Redimensionnement d'une image (Éditeur d'images pour les icônes)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.image.editing
helpviewer_keywords:
- Image editor [C++], resizing images
- graphics [C++], resizing
- images [C++], resizing
- resizing images
- size [C++], images
- images [C++], cropping
- images [C++], extending
- Image editor [C++], cropping or extending images
- Image editor [C++], shrinking and stretching images
- images [C++], stretching
- images [C++], shrinking
- bitmaps [C++], shrinking
- bitmaps [C++], stretching
ms.assetid: d83a02c4-4dfe-4586-a0df-51a50c2ba71d
ms.openlocfilehash: d88a4cccff5b9b7b6303329782b7367cb953b13d
ms.sourcegitcommit: 5270117dbecc4c49bca0cf10b927bae3c9930038
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484966"
---
# <a name="resizing-an-image-image-editor-for-icons"></a>Redimensionnement d'une image (Éditeur d'images pour les icônes)

Le comportement de la **Image** éditeur lors du redimensionnement d’une image varie selon que vous avez [sélectionné](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) l’image entière ou une partie.

Lorsque la sélection contient uniquement une partie de l’image, le **Image** éditeur réduit la sélection en supprimant des lignes ou des colonnes de pixels et en remplissant les régions libérées avec la couleur d’arrière-plan actuelle. Il permet également d’étendre la sélection en dupliquant des lignes ou des colonnes de pixels.

Lorsque la sélection inclut l’image entière, le **Image** éditeur soit réduit et étire l’image, ou les cultures et l’étend.

Il existe deux mécanismes pour redimensionner une image : les poignées de redimensionnement et la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Vous faites glisser les poignées de redimensionnement pour modifier la taille de tout ou partie d’une image. Les poignées de dimensionnement que vous pouvez faire glisser sont pleines. Vous ne pouvez pas faire glisser les poignées qui sont vides. Utilisez le **propriétés** fenêtre pour redimensionner l’intégralité de l’image uniquement, pas une partie sélectionnée.

![Dimensionnement des handles sur une image bitmap](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")<br/>
Poignées de redimensionnement

> [!NOTE]
> Si vous avez le **grille mosaïque** option sélectionnée dans le [boîte de dialogue Paramètres de la grille](../windows/grid-settings-dialog-box-image-editor-for-icons.md), puis redimensionnement s’aligne sur la ligne de grille mosaïque suivante. Si seul le **grille de pixels** option est sélectionnée (paramètre par défaut), redimensionnement s’aligne sur le pixel suivant.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-resize-an-entire-image-using-the-properties-window"></a>Pour redimensionner l’intégralité d’une image à l’aide de la fenêtre Propriétés

1. Ouvrez l’image dont vous souhaitez modifier les propriétés.

1. Dans le **largeur** et **hauteur** zones dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), tapez les dimensions que vous souhaitez.

   Si vous augmentez la taille de l’image, le **Image** éditeur étend l’image vers la droite, vers le bas, ou les deux et remplit la nouvelle région avec la couleur d’arrière-plan actuelle. L’image n’est pas étiré.

   Si vous réduisez la taille de l’image, le **Image** éditeur rogne l’image sur le bord droit ou inférieur, ou les deux.

   > [!NOTE]
   > Vous pouvez utiliser la **largeur** et **hauteur** propriétés pour redimensionner l’image entière en ne pas pour une sélection partielle.

## <a name="to-crop-or-extend-an-entire-image"></a>Pour rogner ou étendre l’intégralité d’une image

1. Sélectionnez l’image entière.

   Si la partie de l’image est actuellement sélectionnée et que vous souhaitez sélectionner l’image entière, sélectionnez n’importe où sur l’image en dehors de la bordure de sélection actuel.

1. Faites glisser une poignée de redimensionnement jusqu'à ce que l’image est la bonne taille.

Normalement, le **Image** éditeur rogne ou agrandit une image lors du redimensionnement en déplaçant une poignée de redimensionnement. Si vous maintenez le **MAJ** enfoncée quand vous déplacez une poignée de redimensionnement, la **Image** éditeur réduit ou étire l’image.

## <a name="to-shrink-or-stretch-an-entire-image"></a>Pour réduire ou étirer l’intégralité d’une image

1. Sélectionnez l’image entière.

   Si une partie de l’image est actuellement sélectionnée et que vous souhaitez sélectionner l’image entière, sélectionnez n’importe où sur l’image en dehors de la bordure de sélection actuel.

1. Maintenez la **MAJ** de clé et faites glisser une poignée de redimensionnement jusqu'à ce que l’image est la bonne taille.

## <a name="to-shrink-or-stretch-part-of-an-image"></a>Pour réduire ou étirer une partie d’une image

1. Sélectionnez la partie de l’image que vous voulez redimensionner. Pour plus d’informations, consultez [sélection d’une zone de l’Image](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md).

1. Faites glisser l’une des poignées de redimensionnement jusqu'à ce que la sélection est la bonne taille.

## <a name="requirements"></a>Spécifications

Aucun.

## <a name="see-also"></a>Voir aussi

[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Modification de ressources graphiques](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)
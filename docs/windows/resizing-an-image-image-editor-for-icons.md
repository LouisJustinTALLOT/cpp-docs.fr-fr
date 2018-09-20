---
title: Redimensionnement d’une Image (Éditeur d’images pour les icônes) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.editing
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], resizing images
- graphics [C++], resizing
- images [C++], resizing
- resizing images
ms.assetid: d83a02c4-4dfe-4586-a0df-51a50c2ba71d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6e81ca5418782b993f406f33b0b207bc8acb5ba0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393657"
---
# <a name="resizing-an-image-image-editor-for-icons"></a>Redimensionnement d'une image (Éditeur d'images pour les icônes)

Le comportement de la **Image** éditeur lors du redimensionnement d’une image varie selon que vous avez [sélectionné](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) l’image entière ou une partie.

Lorsque la sélection contient uniquement une partie de l’image, le **Image** éditeur réduit la sélection en supprimant des lignes ou des colonnes de pixels et en remplissant les régions libérées avec la couleur d’arrière-plan actuelle, ou qu’il couvre la sélection par duplication des lignes ou des colonnes de pixels.

Lorsque la sélection inclut l’image entière, le **Image** éditeur soit réduit et étire l’image, ou les cultures et l’étend.

Il existe deux mécanismes pour redimensionner une image : les poignées de redimensionnement et la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Vous pouvez faire glisser les poignées de redimensionnement pour modifier la taille de tout ou partie d’une image. Les poignées de dimensionnement que vous pouvez faire glisser sont pleines. Vous ne pouvez pas faire glisser les poignées qui sont vides. Vous pouvez utiliser la **propriétés** fenêtre pour redimensionner l’intégralité de l’image uniquement, pas une partie sélectionnée.

![Dimensionnement des handles sur une image bitmap](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")  
Poignées de redimensionnement

> [!NOTE]
> Si vous avez le **grille mosaïque** option sélectionnée dans le [boîte de dialogue Paramètres de la grille](../windows/grid-settings-dialog-box-image-editor-for-icons.md), puis redimensionnement s’aligne sur la ligne de grille mosaïque suivante. Si seul le **grille de pixels** option est sélectionnée (paramètre par défaut), redimensionnement s’aligne sur le pixel suivant.

- [Redimensionner l’intégralité d’une Image](../windows/resizing-an-entire-image-image-editor-for-icons.md)

- [Rognage ou extension de l’intégralité d’une Image](cropping-or-extending-an-entire-image-image-editor-for-icons.md)

- [Réduction ou étirement de l’intégralité d’une Image](../windows/shrinking-or-stretching-an-entire-image-image-editor-for-icons.md)

- [Réduction ou étirement d’une partie d’une Image](../windows/shrinking-or-stretching-part-of-an-image-image-editor-for-icons.md)

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Aucun.

## <a name="see-also"></a>Voir aussi

[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Modification de ressources graphiques](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)
---
title: Éditeur d’images pour les icônes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.cursor.F1
- vc.editors.icon.F1
- vc.editors.cursor
- vc.editors.bitmap.F1
dev_langs:
- C++
helpviewer_keywords:
- editors, images
- resource editors [C++], graphics
- Image editor [C++]
- resource editors [C++], Image editor
ms.assetid: 586d2b8b-0348-4883-a85d-1ff0ddbf14dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fe7cad7fccabd7acc8af7ecf1f3711d5b0d636ce
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379188"
---
# <a name="image-editor-for-icons"></a>Éditeur d'images pour les icônes

L'Éditeur d'images se compose d'un ensemble d'outils permettant de créer et de modifier des images, ainsi que de fonctionnalités permettant de créer des bitmaps de barre d'outils. En plus des bitmaps, des icônes et des curseurs, vous pouvez modifier des images au format GIF ou JPEG en utilisant les commandes du menu **Image** et les outils de la barre d'outils **Éditeur d'images** .

Avec l'Éditeur d'images, vous pouvez :

- [Modifier des ressources graphiques](../windows/editing-graphical-resources-image-editor-for-icons.md)

- [Utiliser des couleurs](../windows/working-with-color-image-editor-for-icons.md)

- [Utiliser des icônes et des curseurs : ressources d'images pour périphériques d'affichage](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)

- [Utiliser des touches accélérateur pour les commandes de l'Éditeur d'images](../windows/accelerator-keys-image-editor-for-icons.md)

Le **Éditeur d’images** fenêtre affiche deux vues d’une image, avec une barre sépare les deux volets de fractionnement. Vous pouvez faire glisser la barre de fractionnement pour modifier la taille des volets. Une bordure de sélection entoure le volet actif.

Le **Éditeur d’images** fenêtre peut être ajustée pour s’ajuster à vos besoins et préférences. Vous pouvez [modifier le facteur de zoom](../windows/changing-the-magnification-factor-image-editor-for-icons.md) et [afficher ou masquer la grille de pixels](../windows/displaying-or-hiding-the-pixel-grid-image-editor-for-icons.md).

> [!NOTE]
> À l’aide de la **Éditeur d’images**, vous pouvez afficher des images 32 bits, mais vous ne pouvez pas les modifier.

## <a name="visual-studio-image-library"></a>Bibliothèque d'images Visual Studio

Vous pouvez télécharger gratuitement le **bibliothèque d’images Visual Studio** qui contient de nombreuses animations, bitmaps et icônes que vous pouvez utiliser dans vos applications. Pour plus d'informations sur le téléchargement de cette bibliothèque, consultez [Bibliothèque d'images Visual Studio](/visualstudio/designers/the-visual-studio-image-library).

## <a name="managed-resources"></a>Ressources managées

Vous pouvez utiliser la **Image** éditeur et le [éditeur binaire](binary-editor.md) pour travailler avec des fichiers de ressources dans les projets managés. Toutes les ressources managées que vous souhaitez modifier doivent être liées. Les éditeurs de ressources Visual Studio ne prennent pas en charge la modification des ressources incorporées.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Aucun.

## <a name="see-also"></a>Voir aussi

[Éditeurs de ressources](../windows/resource-editors.md)<br/>
[Icônes](https://msdn.microsoft.com/library/windows/desktop/ms646973.aspx)
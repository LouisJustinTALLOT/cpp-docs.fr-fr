---
title: 'Icônes et curseurs : ressources Image pour les périphériques d’affichage (Éditeur d’images C++ pour les icônes) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.icon
dev_langs:
- C++
helpviewer_keywords:
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
ms.assetid: 8f0809a8-0cf0-4da9-b23d-51f28bf15f5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 03c3b64cfbf93260c1195fa028d05bb8085c9b09
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313583"
---
# <a name="icons-and-cursors-image-resources-for-display-devices-c-image-editor-for-icons"></a>Icônes et curseurs : ressources Image pour les périphériques d’affichage (Éditeur d’images C++ pour les icônes)

Les icônes et curseurs sont des ressources graphiques qui peuvent contenir plusieurs images de différentes tailles et modèles de couleurs pour différents types de périphériques d’affichage. De plus, un curseur a une « zone réactive », l’emplacement utilisé par Windows pour suivre sa position. Icônes et curseurs sont créés et modifiés à l’aide du **Image** éditeur, comme les bitmaps et autres images.

Lorsque vous créez une nouvelle icône ou curseur, la **Image** éditeur crée d’abord une image d’un type standard. Cette image est remplie initialement avec la couleur d’écran (transparente). Si l’image est un curseur, la zone réactive est initialement le coin supérieur gauche (coordonnées 0,0).

Par défaut, le **Image** éditeur prend en charge la création d’images supplémentaires pour les périphériques répertoriés dans le tableau suivant. Vous pouvez créer des images pour d’autres périphériques en tapant les paramètres de hauteur, largeur et nombre de couleurs dans la boîte de dialogue [Image personnalisée](custom-image-dialog-box-image-editor-for-icons.md).

> [!NOTE]
> À l’aide de la **Éditeur d’images**, vous pouvez afficher des images 32 bits, mais vous ne pouvez pas les modifier.

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

- [Création d’une image de périphérique (icône ou curseur)](../windows/creating-a-device-image-image-editor-for-icons.md)

- [Ajout d'une image pour un autre périphérique d'affichage](../windows/adding-an-image-for-a-different-display-device-image-editor-for-icons.md)

- [Copie d'une image de périphérique](../windows/copying-a-device-image-image-editor-for-icons.md)

- [Suppression d'une image de périphérique](../windows/deleting-a-device-image-image-editor-for-icons.md)

- [Création de régions transparentes ou inversées dans des images de périphérique](../windows/creating-transparent-or-inverse-regions-in-device-images.md)

- [Création d'une icône ou d'un curseur 256 couleurs](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md)

- [Définition de la zone réactive d'un curseur](../windows/setting-a-cursor-s-hot-spot-image-editor-for-icons.md)

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Aucun.

## <a name="see-also"></a>Voir aussi

[Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)  
[Icônes](https://msdn.microsoft.com/library/windows/desktop/ms646973)  
[Curseurs](https://msdn.microsoft.com/library/windows/desktop/ms646970)
---
title: Utilisation des couleurs (Éditeur d'images pour les icônes)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.image.color
helpviewer_keywords:
- images [C++], background colors
- Image editor [C++], Colors Palette
- colors [C++], image
- Colors Palette, Image editor
- palettes, Image editor colors
- foreground colors [C++], Image editor
- colors [C++]
ms.assetid: d34ff96f-241d-494f-abdd-13811ada8cd3
ms.openlocfilehash: 7103332d0b7c0f4756da9526290cabb79544617d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610702"
---
# <a name="working-with-color-image-editor-for-icons"></a>Utilisation des couleurs (Éditeur d'images pour les icônes)

Le **Éditeur d’images** contient de nombreuses fonctionnalités qui permettent de gérer et personnaliser les couleurs. Vous pouvez définir une couleur de premier plan ou d’arrière-plan, couleur de remplissage des zones délimités ou sélectionnez une couleur dans une image à utiliser comme la couleur de premier plan ou d’arrière-plan actuelle. Vous pouvez utiliser les outils sur le [barre d’outils Éditeur d’images](../windows/toolbar-image-editor-for-icons.md) ainsi que de la palette de couleurs dans le [fenêtre couleurs](../windows/colors-window-image-editor-for-icons.md) pour créer des images.

Toutes les couleurs pour les images monochromes et 16 couleurs sont affichées dans le **couleurs** palette dans la **couleurs** fenêtre. En plus de 16 couleurs standard, vous pouvez créer vos propres couleurs personnalisées. La modification des couleurs dans la palette, change immédiatement la couleur correspondante dans l’image.

Lorsque vous travaillez avec l’icône de 256 couleurs et images de curseur, la **couleurs** propriété dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) est utilisé. Pour plus d’informations, consultez [création d’une icône de 256 couleurs ou d’un curseur](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md).

> [!NOTE]
> À l’aide de la **Éditeur d’images**, vous pouvez afficher des images 32 bits, mais vous ne pouvez pas les modifier.

Couleurs vraies images peuvent également être créées. Toutefois, les échantillons de couleurs n’apparaissent pas dans la palette de la **couleurs** fenêtre ; ils apparaissent uniquement dans la zone d’indicateur de couleur de premier plan ou d’arrière-plan. Les couleurs vraies sont créées à l’aide de la [boîte de dialogue Sélecteur de couleurs personnalisées](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md). Pour plus d’informations, consultez [personnalisation ou modification des couleurs](../windows/customizing-or-changing-colors-image-editor-for-icons.md).

Vous pouvez enregistrer des palettes de couleurs personnalisées sur le disque et les recharger en fonction des besoins. La palette de couleurs que vous avez utilisé le plus récemment est enregistrée dans le Registre et chargée automatiquement la prochaine fois que vous démarrez Visual Studio.

- [Sélection de premier plan ou des couleurs d’arrière-plan](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)

- [Remplissage d’une zone délimitée d’une Image avec une couleur](../windows/filling-a-bounded-area-of-an-image-with-a-color-image-editor-for-icons.md)

- [Sélection d’une couleur à partir d’une Image à utiliser ailleurs](../windows/picking-up-a-color-from-an-image-to-use-elsewhere-image-editor-for-icons.md)

- [Choix d’un arrière-plan Transparent ou Opaque](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)

- [Inversion des couleurs dans une sélection](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md)

- [Personnalisation ou modification des couleurs](../windows/customizing-or-changing-colors-image-editor-for-icons.md)

- [L’enregistrement et chargement de différentes Palettes de couleurs](../windows/saving-and-loading-different-color-palettes-image-editor-for-icons.md)

- [Fenêtre couleurs](../windows/colors-window-image-editor-for-icons.md)

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Aucun.

## <a name="see-also"></a>Voir aussi

[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)

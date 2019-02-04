---
title: Utilisation de la palette 256 couleurs (Éditeur d'images pour les icônes)
ms.date: 11/04/2016
helpviewer_keywords:
- 256-color palette
- cursors [C++], color
- colors [C++], icons
- colors [C++], cursors
- icons, color
- colors [C++], icons and cursors
- color palettes, 256-color
- palettes, 256-color
ms.assetid: 2738089b-4fd3-4c45-96ae-6a15e4c6b780
ms.openlocfilehash: 4e2f2c9ce58799756137bb47db42e52c97a43d39
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702893"
---
# <a name="using-the-256-color-palette-image-editor-for-icons"></a>Utilisation de la palette 256 couleurs (Éditeur d'images pour les icônes)

À l’aide de la **Image** éditeur, icônes et curseurs peuvent être de grande taille (64 x 64) avec une palette de 256 couleurs. Après avoir créé la ressource, un style d’image de périphérique est sélectionné.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-create-a-256-color-icon-or-cursor"></a>Pour créer une icône de 256 couleurs ou d’un curseur

1. Dans [affichage des ressources](../windows/resource-view-window.md), avec le bouton droit de votre fichier .rc, puis choisissez **insérer la ressource** dans le menu contextuel. (Si vous disposez déjà d’une ressource image dans votre fichier .rc, par exemple un curseur, vous pouvez cliquer sur le **curseur** dossier et sélectionnez **insérer Cursor** dans le menu contextuel.)

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

1. Dans le [boîte de dialogue Ajouter une ressource](../windows/add-resource-dialog-box.md), sélectionnez **icône** ou **curseur** et choisissez **New**.

1. Sur le **Image** menu, sélectionnez **nouvelle Image de périphérique**.

1. Sélectionnez le style de l’image de 256 couleurs souhaité.

## <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>Pour choisir une couleur de la palette 256 couleurs pour les grandes icônes

Pour dessiner avec une sélection à partir de la palette 256 couleurs, vous devez sélectionner les couleurs à partir de la **couleurs** palette dans la [fenêtre couleurs](../windows/colors-window-image-editor-for-icons.md).

1. Sélectionnez la grande icône ou curseur, ou créez une nouvelle grande icône ou curseur.

1. Choisir une couleur parmi les 256 couleurs affichées dans le **couleurs** palette dans la **couleurs** fenêtre.

   La couleur sélectionnée devient la couleur actuelle dans le **couleurs** palette dans la **couleurs** fenêtre.

   > [!NOTE]
   > La palette d’origine utilisée pour les images de 256 couleurs correspond à la palette retournée par la `CreateHalftonePalette` API de Windows. Toutes les icônes pour le shell Windows doivent utiliser cette palette pour empêcher le scintillement pendant la réalisation de la palette.

## <a name="requirements"></a>Spécifications

Aucun.

## <a name="see-also"></a>Voir aussi

[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Icônes et curseurs : Ressources d’images pour périphériques d’affichage](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)

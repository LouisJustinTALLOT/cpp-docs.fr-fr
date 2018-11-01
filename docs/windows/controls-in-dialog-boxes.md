---
title: Contrôles dans les boîtes de dialogue (C++) | Microsoft Docs
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], dialog boxes
- dialog box controls [C++], about dialog box controls
- dialog box controls
ms.assetid: e216c4f9-2fd4-429d-889a-8ebce7bad177
ms.openlocfilehash: 3f559a82d7c73dd8050f23e0b3af34f0bcb410c8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644880"
---
# <a name="controls-in-dialog-box-ces"></a>Contrôle, dans la boîte de dialogue (C++), es

Vous pouvez ajouter des contrôles à une boîte de dialogue à l’aide de la [onglet de boîte de dialogue Éditeur](../windows/dialog-editor-tab-toolbox.md) dans le [fenêtre Boîte à outils](/visualstudio/ide/reference/toolbox), ce qui vous permet de choisir le contrôle souhaité et faites-le glisser vers la boîte de dialogue. Par défaut, la fenêtre de boîte à outils est définie sur Masquer automatiquement. Il s’affiche sous forme d’onglet dans la marge gauche de votre solution lorsque l’éditeur de boîtes de dialogue est ouverte. Toutefois, vous pouvez épingler la **boîte à outils** fenêtre dans sa position en cliquant sur le **Masquer automatiquement** bouton dans le coin supérieur droit de la fenêtre. Pour plus d’informations sur la façon de contrôler le comportement de cette fenêtre, consultez [gestion des fenêtres](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Le moyen le plus rapide pour ajouter des contrôles à une boîte de dialogue, repositionner des contrôles existants ou déplacer des contrôles à partir d’une boîte de dialogue à l’autre consiste à utiliser la méthode glisser-déplacer. La position du contrôle est décrite dans une ligne en pointillés jusqu'à ce qu’il sera déposé dans la boîte de dialogue. Lorsque vous ajoutez un contrôle à une boîte de dialogue avec la méthode glisser-déplacer, le contrôle est donné à une hauteur standard appropriée pour ce type de contrôle.

Lorsque vous ajoutez un contrôle à une boîte de dialogue ou repositionnez, son emplacement final peut être déterminé par les guides ou les marges, ou si vous disposez de la grille de disposition sous tension.

Une fois que vous avez ajouté un contrôle à la boîte de dialogue, vous pouvez modifier les propriétés telles que sa légende dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Vous pouvez sélectionner plusieurs contrôles et modifier leurs propriétés à la fois.

- [Ajout, modification ou suppression de contrôles](adding-editing-or-deleting-controls.md)

- [Sélection de contrôles](../windows/selecting-controls.md)

- [Dimensionnement de contrôles individuels](../windows/sizing-individual-controls.md)

- [Définition de la même largeur, hauteur ou taille pour des contrôles](../windows/making-controls-the-same-width-height-or-size.md)

- [Définition de la taille d’une zone de liste déroulante et de sa liste déroulante](setting-the-size-of-the-combo-box-and-its-drop-down-list.md)

- [Ajout de valeurs à un contrôle Combo Box](../windows/adding-values-to-a-combo-box-control.md)

- [Définition de la largeur d’une barre de défilement horizontale](../windows/setting-the-width-of-a-horizontal-scroll-bar.md)

- [L’organisation des contrôles sur les boîtes de dialogue](../windows/arrangement-of-controls-on-dialog-boxes.md)

- [Contrôles personnalisés dans l’Éditeur de boîtes de dialogue](custom-controls-in-the-dialog-editor.md)

- [Définition des mnémoniques (Touches d’accès rapide)](../windows/defining-mnemonics-access-keys.md)

- [Spécification de l’emplacement et de la taille d’une boîte de dialogue](../windows/specifying-the-location-and-size-of-a-dialog-box.md)

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Ajout de gestionnaires d’événements pour les contrôles de boîte de dialogue](../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[Contrôles de boîtes de dialogue et types de variables](../ide/dialog-box-controls-and-variable-types.md)<br/>
[Éditeur de boîtes de dialogue](../windows/dialog-editor.md)
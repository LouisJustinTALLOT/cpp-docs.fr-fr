---
title: Dimensionnement de contrôles
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.combo
helpviewer_keywords:
- Size to Content command
- size, controls
- text, autosizing controls to fit text
- controls [C++], sizing
- Make Same Size command
- combo boxes, sizing
- list controls [C++], scroll bar width
- CListBox::SetHorizontalExtent
- controls [C++], scroll bar
- scroll bars [C++], displaying in controls
- horizontal scroll bar width
- CListBox class, scroll bar width
- scroll bars [C++], width
ms.assetid: 14ccba02-7171-463a-a121-7018cf1e2e5a
ms.openlocfilehash: a6381dcf1aeb9f73ac3b656229d9332df2a6a519
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742711"
---
# <a name="sizing-controls"></a>Dimensionnement de contrôles

Utilisez les poignées de redimensionnement pour redimensionner un contrôle. Lorsque le pointeur est positionné sur une poignée de redimensionnement, il change de forme pour indiquer les sens dans lequel le contrôle peut être redimensionné. Poignées de redimensionnement active sont correctes ; Si une poignée de redimensionnement est vide, le contrôle ne peut pas être redimensionné le long de cet axe.

Vous pouvez également modifier la taille d’un contrôle par le contrôle à des guides ou les marges d’alignement, ou en déplaçant un accroché guide en dehors d’un autre et contrôle.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-size-an-individual-control"></a>Pour dimensionner un contrôle individuel

1. Sélectionnez le contrôle.

1. Faites glisser les poignées de redimensionnement pour modifier la taille du contrôle :

   - Poignées de redimensionnement en haut et côtés modifier la taille horizontale ou verticale.

   - Poignées de redimensionnement dans les angles modifier la taille horizontale et verticale.

   > [!TIP]
   > Vous pouvez redimensionner le contrôle d’unité une boîte de dialogue (DLU) à la fois en maintenant enfoncée la **MAJ** clés et à l’aide la **flèche droite** et **bas** clés.

## <a name="to-automatically-size-a-control-to-fit-the-text-within-it"></a>Pour dimensionner automatiquement un contrôle pour s’adapter au texte qu’il contient

Choisissez **ajuster au contenu** à partir de la **Format** menu.

\- ou -

Cliquez sur le contrôle et choisissez **ajuster au contenu** dans le menu contextuel.

## <a name="to-make-controls-the-same-width-height-or-size"></a>Pour rendre les contrôles la même largeur, hauteur ou taille

Vous pouvez redimensionner un groupe de contrôles en fonction de la taille du contrôle dominant.

1. [Sélectionnez les contrôles](../windows/selecting-multiple-controls.md) vous voulez redimensionner.

   Le contrôle sélectionné en premier dans la série est le contrôle dominant. La taille finale des contrôles dans le groupe dépend de la taille du contrôle dominant. Pour plus d’informations sur la sélection du contrôle dominant, consultez [spécification du contrôle Dominant](../windows/specifying-the-dominant-control.md).

1. À partir de la **Format** menu, choisissez **Uniformiser la taille**, puis choisissez une des commandes suivantes :

   - **Both**

   - **Height**

   - **Width**

## <a name="to-set-the-size-of-the-combo-box-and-its-drop-down-list"></a>Pour définir la taille de la liste déroulante de zone et sa liste déroulante

Vous pouvez dimensionner une zone de liste déroulante lorsque vous l’ajoutez à la boîte de dialogue. Vous pouvez également spécifier la taille de la zone de liste déroulante. Pour plus d’informations, consultez [Ajout de valeurs à un contrôle Combo Box](../windows/adding-values-to-a-combo-box-control.md).

### <a name="to-size-a-combo-box"></a>Pour dimensionner une zone de liste déroulante

1. Sélectionnez le contrôle de zone de liste déroulante dans votre boîte de dialogue.

   Initialement, seuls les poignées de redimensionnement de gauche et droite sont actifs.

1. Utilisez les poignées de redimensionnement pour définir la largeur de la zone de liste déroulante.

Vous pouvez également définir la taille verticale de la partie de la liste déroulante de la zone de liste déroulante.

### <a name="to-set-the-size-of-the-combo-box-drop-down-list"></a>Pour définir la taille de la liste déroulante zone de liste déroulante

1. Sélectionnez le bouton de flèche de déroulement à droite de la zone de liste déroulante.

   ![Flèche sur une zone de liste déroulante dans un projet MFC](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   Le contour du contrôle change pour afficher la taille de la zone de liste déroulante avec la zone de liste déroulante étendue.

1. Utilisez la poignée de redimensionnement inférieure pour modifier la taille initiale de la zone de liste déroulante.

   ![Liste déroulante&#45;redimensionnement de la zone dans un projet MFC](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

1. Sélectionnez la flèche déroulante à nouveau pour fermer la partie de la liste déroulante de la zone de liste déroulante.

## <a name="to-set-the-width-of-a-horizontal-scroll-bar-and-make-it-appear"></a>Pour définir la largeur d’une barre de défilement horizontale et faire apparaître

Lorsque vous ajoutez une zone de liste avec une barre de défilement horizontale à une boîte de dialogue à l’aide des classes MFC, la barre de défilement ne s’affichent automatiquement dans votre application.

Définissez une largeur maximale pour l’élément le plus large en appelant [CListBox::SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent) dans votre code.

   Sans cette valeur est définie, la barre de défilement ne s’affichent, même lorsque les éléments dans la zone de liste sont plus larges que la zone.
> [!NOTE]
> La barre de défilement horizontale nécessite MFC.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

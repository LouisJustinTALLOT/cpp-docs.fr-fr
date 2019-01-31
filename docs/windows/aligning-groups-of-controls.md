---
title: Aligner les contrôles
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], aligning
- controls [C++], positioning
- Space Evenly command
- dialog box controls [C++], placement
- Center in Dialog command
- Arrange Buttons command
- buttons, arranging push buttons in dialog boxes
- push buttons
ms.assetid: a4f49a73-4a17-44b3-8568-aa35f646b5cf
ms.openlocfilehash: abfae0f0146fa736a6427eb1180805717ce8a78e
ms.sourcegitcommit: 5270117dbecc4c49bca0cf10b927bae3c9930038
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484979"
---
# <a name="align-controls"></a>Aligner les contrôles

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

Les procédures suivantes vous montrent comment aligner les contrôles :

## <a name="to-align-groups-of-controls"></a>Pour aligner des groupes de contrôles

1. [Sélectionnez les contrôles](../windows/selecting-multiple-controls.md) à aligner. Veillez à sélectionner le contrôle que vous souhaitez d’abord être le contrôle dominant ou définissez-le comme contrôle dominant avant d’exécuter l’alignement ou de dimensionnement de commande.

   La position finale du groupe de contrôles dépend de la position du contrôle dominant. Pour plus d’informations sur la sélection du contrôle dominant, consultez [spécification du contrôle Dominant](../windows/specifying-the-dominant-control.md).

1. À partir de la **Format** menu, choisissez **Align**, puis choisissez un des alignements suivants :

   - `Lefts`: aligne les contrôles sélectionnés sur leurs côtés gauches.

   - `Centers`: aligne les contrôles sélectionnés sur leur centre horizontalement.

   - `Rights`: aligne les contrôles sélectionnés sur leurs côtés.

   - `Tops`: aligne les contrôles sélectionnés sur leurs bords supérieurs.

   - `Middles`: aligne les contrôles sélectionnés verticalement sur leur milieu.

   - `Bottoms`: aligne les contrôles sélectionnés sur le bord inférieur.

## <a name="to-even-the-spacing-between-controls"></a>De même, l’espacement entre les contrôles

Le **boîte de dialogue** éditeur vous permet aux contrôles d’espace uniformément entre les contrôles extérieur sélectionnés.

1. Sélectionnez les contrôles que vous souhaitez réorganiser.

1. À partir de la **Format** menu, choisissez **Espace uniformément**, puis choisissez un des espacements suivants :

   - `Across`: espace les contrôles uniformément entre le plus à gauche et le plus à droite contrôle sélectionné.

   - `Down`: espace les contrôles uniformément entre le premier et le plus bas contrôle sélectionné.

## <a name="to-center-controls-in-a-dialog-box"></a>Pour centrer les contrôles dans une boîte de dialogue

1. Sélectionnez l’ou les contrôles que vous souhaitez réorganiser.

1. À partir de la **Format** menu, choisissez **Centrer dans la boîte de dialogue**, puis choisissez une des options suivantes :

   - `Vertical`: centre les contrôles verticalement dans la boîte de dialogue.

   - `Horizontal`: centre les contrôles horizontalement dans la boîte de dialogue.

## <a name="to-arrange-push-buttons-along-the-right-or-bottom-of-a-dialog-box"></a>Pour réorganiser les boutons de commande à droite ou en bas d’une boîte de dialogue

1. Sélectionnez un ou plusieurs boutons de commande.

1. À partir de la **Format** menu, choisissez **réorganiser les boutons**, puis choisissez une des options suivantes :

   - `Right`: aligne le bord droit de la boîte de dialogue de boutons.

   - `Bottom`: aligne le bord inférieur de la boîte de dialogue de boutons.

       Si vous sélectionnez un contrôle autre qu’un bouton de commande, sa position n’est pas affectée.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Organisation des contrôles dans les boîtes de dialogue](../windows/arrangement-of-controls-on-dialog-boxes.md)<br/>
[Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
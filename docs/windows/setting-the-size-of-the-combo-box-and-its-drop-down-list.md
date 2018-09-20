---
title: Définition de la taille de la zone de liste déroulante et de sa liste déroulante | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.combo
dev_langs:
- C++
helpviewer_keywords:
- combo boxes, sizing
- controls [C++], sizing
ms.assetid: 51fb53cf-9ddf-4a20-962e-8553938e55ee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8bd2a81c10855dfe1d409b34612956616018dab7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413449"
---
# <a name="setting-the-size-of-the-combo-box-and-its-drop-down-list"></a>Définition de la taille d’une zone de liste déroulante et de sa liste déroulante

Vous pouvez dimensionner une zone de liste déroulante lorsque vous l’ajoutez à la boîte de dialogue. Vous pouvez également spécifier la taille de la zone de liste déroulante.

### <a name="to-size-a-combo-box"></a>Pour dimensionner une zone de liste déroulante

1. Sélectionnez le contrôle de zone de liste déroulante dans votre boîte de dialogue.

   Initialement, seuls les poignées de redimensionnement de gauche et droite sont actifs.

2. Utilisez les poignées de redimensionnement pour définir la largeur de la zone de liste déroulante.

Vous pouvez également définir la taille verticale de la partie de la liste déroulante de la zone de liste déroulante.

#### <a name="to-set-the-size-of-the-combo-box-drop-down-list"></a>Pour définir la taille de la liste déroulante zone de liste déroulante

1. Cliquez sur le bouton de flèche de déroulement à droite de la zone de liste déroulante.

   ![Flèche sur une zone de liste déroulante dans un projet MFC](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   Le contour du contrôle change pour afficher la taille de la zone de liste déroulante avec la zone de liste déroulante étendue.

2. Utilisez la poignée de redimensionnement inférieure pour modifier la taille initiale de la zone de liste déroulante.

   ![Liste déroulante&#45;redimensionnement de la zone dans un projet MFC](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

3. Cliquez sur la flèche déroulante pour fermer la partie de la liste déroulante de la zone de liste déroulante.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Ajout de valeurs à un contrôle Combo Box](../windows/adding-values-to-a-combo-box-control.md)<br/>
[Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
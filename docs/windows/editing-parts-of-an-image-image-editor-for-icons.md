---
title: Modification de parties d’une Image (Éditeur d’images pour les icônes) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], editing images
- Clipboard [C++], pasting
- images [C++], editing
- images [C++], deleting selected parts
- images [C++], copying selected parts
- images [C++], moving selected parts
- images [C++], dragging and replicating selected parts
- images [C++], pasting into
- graphics [C++], editing
ms.assetid: ff4f5fef-71a4-4fd8-825e-049399fed391
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9340180049d85b1b5385d49c7b358c3fd791ce9d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391473"
---
# <a name="editing-parts-of-an-image-image-editor-for-icons"></a>Modification de parties d'une image (Éditeur d'images pour les icônes)

Vous pouvez effectuer les opérations de modification standard — couper, copier, effacer et déplacement — sur un [sélection](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md), si la sélection est l’image entière ou uniquement une partie de celui-ci. Étant donné que le **Image** éditeur utilise le **Presse-papiers de Windows**, vous pouvez transférer des images entre le **Image** éditeur et autres applications pour Windows.

En outre, vous pouvez redimensionner la sélection, si elle inclut l’image entière ou seulement une partie.

### <a name="to-cut-the-current-selection-and-move-it-to-the-clipboard"></a>Pour couper la sélection actuelle et déplacez-le vers le Presse-papiers

1. Cliquez sur **couper** sur le **modifier** menu.

### <a name="to-copy-the-selection"></a>Pour copier la sélection

1. Placez le pointeur à l’intérieur de la bordure de sélection ou n’importe où sur celle-ci, sauf les poignées de redimensionnement.

2. Maintenez la **Ctrl** enfoncée quand vous faites glisser la sélection vers un nouvel emplacement. La zone de la sélection d’origine est inchangée.

3. Pour copier la sélection dans l’image à son emplacement actuel, cliquez à l’extérieur du curseur de sélection.

### <a name="to-paste-the-clipboard-contents-into-an-image"></a>Pour coller le contenu du Presse-papiers dans une image

1. À partir de la **modifier** menu, choisissez **coller**.

   Le contenu du Presse-papiers, entouré de la bordure de sélection, s’affichent dans le coin supérieur gauche du volet.

2. Placez le pointeur de la bordure de sélection et faites glisser l’image à l’emplacement souhaité sur l’image.

3. Pour ancrer l’image à son nouvel emplacement, cliquez en dehors de la bordure de sélection.

### <a name="to-delete-the-current-selection-without-moving-it-to-the-clipboard"></a>Pour supprimer la sélection actuelle sans le déplacer dans le Presse-papiers

1. À partir de la **modifier** menu, choisissez **supprimer**.

   La zone d’origine de la sélection est remplie avec la couleur d’arrière-plan actuelle.

   > [!NOTE]
   > Vous pouvez accéder à la **couper**, **copie**, **coller**, et **supprimer** commandes en cliquant avec le bouton droit dans le **affichagedesressources** fenêtre.

### <a name="to-move-the-selection"></a>Pour déplacer la sélection

1. Placez le pointeur à l’intérieur de la bordure de sélection ou n’importe où sur celle-ci, sauf les poignées de redimensionnement.

2. Faites glisser la sélection vers son nouvel emplacement.

3. Pour ancrer la sélection dans l’image à son nouvel emplacement, cliquez en dehors de la bordure de sélection.

Pour plus d’informations sur le dessin avec une sélection, consultez [création d’un pinceau personnalisé](../windows/creating-a-custom-brush-image-editor-for-icons.md).

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Aucun.

## <a name="see-also"></a>Voir aussi

[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Modification de ressources graphiques](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)
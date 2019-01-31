---
title: Sélection de contrôles
ms.date: 11/04/2016
helpviewer_keywords:
- Dialog Editor [C++], selecting controls
- dominant controls
- dialog box controls [C++], selecting in editor
- controls [C++], selecting
- size, controls
- controls [C++], dominant
- controls [C++], removing from groups
- Dialog Editor [C++], dominant control
ms.assetid: 27f05450-4550-4229-9f4c-2c9e06365596
ms.author: Michael.Blome
ms.topic: tutorial
ms.service: cpp
author: mikeblome
ms.openlocfilehash: 008c99ae4b2cba5ff8f8b9ab069bb1b8085b7524
ms.sourcegitcommit: b488462a6e035131121e6f32d8f3b108cc798b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55293635"
---
# <a name="selecting-controls"></a>Sélection de contrôles

Sélectionner des contrôles à la taille, aligner, déplacer, copier, ou supprimez-les, puis terminez l’opération que vous souhaitez. Dans la plupart des cas, vous devez sélectionner plusieurs contrôles à utiliser les outils de dimensionnement et d’alignement sur le [barre d’outils Éditeur de boîte de dialogue](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

Lorsqu’un contrôle est sélectionné, elle comporte une bordure ombrée autour d’elle avec solide (actif) ou vides (inactives) « poignées de dimensionnement » petits carrés qui apparaissent dans la bordure de sélection. Lorsque plusieurs contrôles sont sélectionnés, le contrôle dominant doté de poignées de redimensionnement solide et tous les autres contrôles sélectionnés ont des poignées de redimensionnement creux.

Lorsque vous êtes de dimensionnement ou aligner plusieurs contrôles, la **boîte de dialogue** éditeur utilise le « contrôle dominant » pour déterminer comment les autres contrôles sont dimensionnés ou alignés. Par défaut, le contrôle dominant est le premier contrôle sélectionné.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-select-multiple-controls"></a>Pour sélectionner plusieurs contrôles

1. Dans le [fenêtre Boîte à outils](/visualstudio/ide/reference/toolbox), sélectionnez le **pointeur** outil.

1. Faites glisser le pointeur pour dessiner une zone de sélection autour des contrôles que vous souhaitez sélectionner dans votre boîte de dialogue.

   Lorsque vous relâchez le bouton de la souris, tous les contrôles à l’intérieur ou à l’intersection de la zone de sélection sont sélectionnés.

   \- ou -

   Maintenez la **MAJ** la clé, sélectionnez les contrôles que vous souhaitez inclure dans la sélection.

   \- ou -

   Maintenez la **Ctrl** la clé, sélectionnez les contrôles que vous souhaitez inclure dans la sélection.

## <a name="to-remove-a-control-from-a-group-of-selected-controls-or-to-add-a-control-to-a-group-of-selected-controls"></a>Pour supprimer un contrôle d’un groupe de contrôles sélectionnés ou pour ajouter un contrôle à un groupe de contrôles sélectionnés

1. Avec un groupe de contrôles sélectionnés, maintenez la **MAJ** la clé, sélectionnez le contrôle que vous souhaitez supprimer ou ajouter à la sélection existante.

   > [!NOTE]
   > Maintenant enfoncé le **Ctrl** clé et la sélection d’un contrôle au sein d’une sélection rendra qui contrôlent le contrôle dominant dans cette sélection.

## <a name="to-specify-the-dominant-control"></a>Pour spécifier le contrôle dominant

1. Maintenez la **Ctrl** clé et cliquez sur le contrôle que vous souhaitez utiliser pour influencer la taille ou l’emplacement d’autres contrôles *premier*.

> [!NOTE]
> Les poignées de redimensionnement du contrôle dominant sont pleines tandis que celles des contrôles secondaires sont vides. Le dimensionnement ou l’alignement est basé sur le contrôle dominant.

## <a name="to-change-the-dominant-control"></a>Pour modifier le contrôle dominant

1. Effacer la sélection actuelle, cliquez en dehors de tous les contrôles actuellement sélectionnés.

1. Répétez la procédure précédente, en sélectionnant un autre contrôle en premier.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
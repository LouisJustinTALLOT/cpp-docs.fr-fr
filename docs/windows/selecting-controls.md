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
ms.assetid: 27f05450-4550-4229-9f4c-2c9e06365596
ms.openlocfilehash: ccef63ae6388f376c4be96a34f2857fcedde0ea9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637097"
---
# <a name="selecting-controls"></a>Sélection de contrôles

Sélectionner des contrôles à la taille, aligner, déplacer, copier, ou les supprimer, puis effectuez l’opération que vous souhaitez. Dans la plupart des cas, vous devez sélectionner plusieurs contrôles à utiliser les outils de dimensionnement et d’alignement sur le [barre d’outils Éditeur de boîte de dialogue](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

Lorsqu’un contrôle est sélectionné, elle comporte une bordure ombrée autour d’elle avec solide (actif) ou vides (inactives) « poignées de dimensionnement » petits carrés qui apparaissent dans la bordure de sélection. Lorsque plusieurs contrôles sont sélectionnés, le contrôle dominant a des poignées de redimensionnement solide ; tous les autres contrôles sélectionnés ont des poignées de redimensionnement creux.

Lorsque vous êtes de dimensionnement ou aligner plusieurs contrôles, la **boîte de dialogue** éditeur utilise le « contrôle dominant » pour déterminer comment les autres contrôles sont dimensionnés ou alignés. Par défaut, le contrôle dominant est le premier contrôle sélectionné.

- [Sélection de plusieurs contrôles](../windows/selecting-multiple-controls.md)

- [Spécification du contrôle dominant](../windows/specifying-the-dominant-control.md)

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
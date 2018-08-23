---
title: Alignement des contrôles sur un repère | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLUs (dialog units)
- controls [C++], aligning
- Dialog editor, snap to guides
- guides, tick mark interval
- dialog box controls, placement
- guides, aligning controls
- dialog units (DLUs)
- snap to guides (Dialog editor)
- controls [C++], sizing
- tick mark interval in Dialog editor
- controls [C++], snap to guides/grid
ms.assetid: 17db84ba-5288-4478-be57-afa748aa6447
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 55cf669d2c84bc0a603354a672706e32656a7c3c
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603926"
---
# <a name="aligning-controls-on-a-guide"></a>Alignement des contrôles sur un repère

Les poignées de redimensionnement de contrôles alignent sur les repères lorsque les contrôles sont déplacés et les repères d’alignement aux contrôles (s’il n’y a aucun contrôle précédemment aligné sur le guide). Lorsqu’un repère est déplacé, les contrôles qui dépendent, sont également déplacent. Les contrôles alignés sur plusieurs repères sont redimensionnés lorsqu’un des guides est déplacé.

Les graduations dans les règles qui déterminent l’espacement des guides et des contrôles sont définies par les unités de boîte de dialogue (DLU). Une DLU est basée sur la taille de la police de la boîte de dialogue, normalement 8 points MS Shell Dlg. Une DLU horizontale est la largeur moyenne de la police de la boîte de dialogue divisée en quatre parties. Une DLU verticale est la hauteur moyenne de la police divisée par huit.

### <a name="to-size-a-group-of-controls-with-guides"></a>Pour dimensionner un groupe de contrôles avec les repères

1. À un repère d’alignement côté « un » de contrôle (ou des contrôles).

2. Faites glisser un guide pour l’autre côté du contrôle (ou des contrôles).

   Si nécessaire, avec plusieurs contrôles, taille de chacun d’eux à s’aligner sur le second guide.

3. Déplacez des repères de dimensionner le contrôle (ou les contrôles).

### <a name="to-change-the-intervals-of-the-tick-marks"></a>Pour modifier les intervalles entre les graduations

1. À partir de la **Format** menu, choisissez **Guide paramètres**.

2. Dans le [repère, boîte de dialogue Paramètres](../windows/guide-settings-dialog-box.md), dans le **espacement de la grille** champ, spécifiez une nouvelle largeur et hauteur DLU.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[États de l’Éditeur de boîtes de dialogue (repères et grilles)](../windows/dialog-editor-states-guides-and-grids.md)  
[Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)
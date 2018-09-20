---
title: Organisation des contrôles dans les boîtes de dialogue (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], positioning
- dialog box controls [C++], placement
- Dialog Editor [C++], arranging controls
ms.assetid: 832491cf-98af-42e5-a854-2cb135fd45c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 24c318f6028db1f2c64b2d2d334648fe4d47619f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390784"
---
# <a name="arrangement-of-controls-on-dialog-box-ces"></a>Organisation des contrôles de boîte de dialogue zone es de (C++)

Le **boîte de dialogue** éditeur fournit des outils de disposition qui alignent et dimensionnent un contrôle automatiquement. Pour la plupart des tâches, vous pouvez utiliser la [barre d’outils Éditeur de boîte de dialogue](../windows/showing-or-hiding-the-dialog-editor-toolbar.md). Tous les **boîte de dialogue Éditeur** des commandes de barre d’outils sont également disponibles sur le **Format** menu et la plupart ont [touches de raccourci](../windows/accelerator-keys-for-the-dialog-editor.md).

De nombreuses commandes de disposition pour les boîtes de dialogue sont disponibles uniquement lorsque plus d’un contrôle est sélectionné. Vous pouvez sélectionner un ou plusieurs contrôles, et lorsque plus d’un contrôle est sélectionné, le premier que vous sélectionnez est par défaut le contrôle « principal ». Pour plus d’informations sur la sélection des contrôles et le contrôle dominant, consultez [sélection de contrôles](../windows/selecting-controls.md).

L’emplacement, la hauteur et la largeur du contrôle actuel sont affichés dans le coin inférieur droit de la barre d’état. Lorsque la boîte de dialogue est activée, la barre d’état affiche la position de la boîte de dialogue sous la forme dans son ensemble et sa hauteur et sa largeur.

- [États de l’Éditeur de boîtes de dialogue (repères et grilles)](../windows/dialog-editor-states-guides-and-grids.md)

- [Regroupement de cases d’option dans une boîte de dialogue](../windows/grouping-radio-buttons-on-a-dialog-box.md)

- [Alignement de groupes de contrôles](../windows/aligning-groups-of-controls.md)

- [Répartition de l’espacement entre les contrôles](../windows/evening-the-spacing-between-controls.md)

- [Centrage des contrôles dans une boîte de dialogue](../windows/centering-controls-in-a-dialog-box.md)

- [Organisation de boutons de commande à droite ou en bas d’une boîte de dialogue](../windows/arranging-push-buttons-along-the-right-or-bottom-of-a-dialog-box.md)

- [Modification de l’ordre de tabulation des contrôles](../windows/changing-the-tab-order-of-controls.md)

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
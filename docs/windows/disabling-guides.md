---
title: Désactivation des repères | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- guides, disabling snapping
- Dialog editor, snap to guides
- snap to guides (Dialog editor)
- controls [C++], snap to guides/grid
ms.assetid: 51efa07b-8684-474e-a0b4-191ec5d91d1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9dd35bad3d7cf5a83ba25a6937ea606af81407c8
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598919"
---
# <a name="disabling-guides"></a>Désactivation des repères

Vous pouvez utiliser les touches spéciales conjointement avec la souris pour désactiver l’alignement sur les guides. À l’aide de la **Alt** clé désactive les effets d’alignement du guide sélectionnée. Déplacement d’un repère avec le **MAJ** clé empêche le déplacement avec le guide de contrôles alignés.

### <a name="to-disable-the-snapping-effect-of-the-guides"></a>Pour désactiver l’alignement sur les repères

1. Faites glisser le contrôle tout en maintenant enfoncée la **Alt** clé.

### <a name="to-move-guides-without-moving-the-snapped-controls"></a>Pour déplacer des repères sans déplacer les contrôles alignés

1. Faites glisser le repère tout en maintenant enfoncée la **MAJ** clé.

### <a name="to-turn-off-the-guides"></a>Pour désactiver les repères

1. À partir de la **Format** menu, choisissez **Guide paramètres**.

2. Dans le [repère, boîte de dialogue Paramètres](../windows/guide-settings-dialog-box.md), sous **repères de disposition**, sélectionnez **aucun**.

   > [!NOTE]
   > Vous pouvez également double-cliquer sur la règle pour accéder à la **Guide paramètres** boîte de dialogue.

\- ou -

- Sur le **Format** menu, cliquez sur **activer/désactiver les repères**.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[États de l’Éditeur de boîtes de dialogue (repères et grilles)](../windows/dialog-editor-states-guides-and-grids.md)  
[Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)
---
title: Boîte de dialogue Outil texte (Éditeur d’images pour les icônes) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.texttool
dev_langs:
- C++
helpviewer_keywords:
- text, adding to an image
- Text Tool dialog box
ms.assetid: a6036ef4-1871-40db-8239-6ddbe8f422f5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 86de06ded585c027af6ebf31dec964222d088198
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613178"
---
# <a name="text-tool-dialog-box-image-editor-for-icons"></a>Boîte de dialogue Outil texte (Éditeur d'images pour les icônes)

Utilisez le **outil texte** boîte de dialogue pour ajouter du texte à une ressource curseur, bitmap ou icône.

Pour accéder à cette boîte de dialogue, ouvrez le [Éditeur d’images](../windows/window-panes-image-editor-for-icons.md). Sélectionnez **outils** à partir de la **Image** menu, puis sélectionnez le **outil texte** commande.

### <a name="font-button"></a>Bouton de police

Ouvre le [boîte de dialogue Police de l’outil texte](../windows/text-tool-font-dialog-box-image-editor-for-icons.md), dans laquelle vous pouvez modifier la police, le style ou la taille de la police du curseur. Modifications sont appliquées au texte affiché dans le **texte** zone.

### <a name="text-area"></a>Zone de texte

Affiche le texte qui apparaît dans le cadre de la ressource. Initialement, cette zone est vide.

> [!NOTE]
> Si **arrière-plan Transparent** est défini, seul le texte sera placé dans l’image. Si **arrière-plan Opaque** est défini, un rectangle englobant, rempli avec les [couleur d’arrière-plan](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md), seront placés derrière le texte. Pour plus d’informations, consultez [choix Opaque et arrière-plans transparents](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).

Vous pouvez avec le bouton droit sur le **outil texte** boîte de dialogue pour accéder à un menu de raccourci par défaut qui contient une liste de commandes Windows standard.

## <a name="requirements"></a>Configuration requise

Aucun.

## <a name="see-also"></a>Voir aussi

[Modification de ressources graphiques](../windows/editing-graphical-resources-image-editor-for-icons.md)
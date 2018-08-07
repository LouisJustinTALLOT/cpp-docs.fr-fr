---
title: Modification de la grille de disposition | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], layout grid
- snap to layout grid
- grids, turning on or off
- layout grid in Dialog Editor
- grids, changing size
ms.assetid: ec31f595-7542-485b-806f-efbaeccc1b3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9817c1f24490d333f1596292f3b9ea1aa3ba40ae
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606934"
---
# <a name="modifying-the-layout-grid"></a>Modification de la présentation grille
Lorsque vous placez ou réorganiser les contrôles dans une boîte de dialogue, vous pouvez utiliser la grille de disposition pour un positionnement plus précis. Lorsque la grille est activée, les contrôles apparaissent comme « aligne » sur les lignes en pointillés de la grille comme si elle était aimantée. Vous pouvez activer cette fonctionnalité « Aligner sur la grille » et de désactiver et modifier la taille des disposition des cellules de grille.  
  
### <a name="to-turn-the-layout-grid-on-or-off"></a>Pour activer ou désactiver le la grille de disposition  
  
1.  À partir de la **Format** menu, choisissez **Guide paramètres**.  
  
2.  Dans le [repère, boîte de dialogue Paramètres](../windows/guide-settings-dialog-box.md), activez ou désactivez le **grille** bouton.  
  
     Vous pouvez toujours contrôler la grille dans les fenêtres individuelles de l’éditeur de boîte de dialogue à l’aide de la **bascule grille** bouton sur le [barre d’outils Éditeur de boîte de dialogue](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).  
  
### <a name="to-change-the-size-of-the-layout-grid"></a>Pour modifier la taille de la grille de disposition  
  
1.  À partir de la **Format** menu, choisissez **Guide paramètres**.  
  
2.  Dans le [repère, boîte de dialogue Paramètres](../windows/guide-settings-dialog-box.md), tapez la hauteur et largeur dans DLU pour les cellules dans la grille. La largeur ou hauteur minimale est 4 DLU. Pour plus d’informations sur DLU, consultez [organisation des contrôles sur les boîtes de dialogue](../windows/arrangement-of-controls-on-dialog-boxes.md).  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Configuration requise  
  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [États d’éditeur de la boîte de dialogue (repères et grilles)](../windows/dialog-editor-states-guides-and-grids.md)   
 [Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)
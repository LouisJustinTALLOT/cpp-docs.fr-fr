---
title: Sélection de contrôles | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Dialog editor, selecting controls
- dominant controls
- dialog box controls, selecting in editor
- controls [C++], selecting
- size, controls
- controls [C++], dominant
ms.assetid: 27f05450-4550-4229-9f4c-2c9e06365596
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5c8a7a57b263fc3db1fa7f021c1a6f4e09c0f8f7
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605667"
---
# <a name="selecting-controls"></a>Sélection de contrôles
Sélectionner des contrôles à la taille, aligner, déplacer, copier, ou les supprimer, puis effectuez l’opération que vous souhaitez. Dans la plupart des cas, vous devez sélectionner plusieurs contrôles à utiliser les outils de dimensionnement et d’alignement sur le [barre d’outils Éditeur de boîte de dialogue](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).  
  
 Lorsqu’un contrôle est sélectionné, elle comporte une bordure ombrée autour d’elle avec solide (actif) ou vides (inactives) « poignées de dimensionnement » petits carrés qui apparaissent dans la bordure de sélection. Lorsque plusieurs contrôles sont sélectionnés, le contrôle dominant a des poignées de redimensionnement solide ; tous les autres contrôles sélectionnés ont des poignées de redimensionnement creux.  
  
 Lorsque vous dimensionnez ou aligner plusieurs contrôles, l’éditeur de boîtes de dialogue utilise le « contrôle dominant » pour déterminer comment les autres contrôles sont dimensionnés ou alignés. Par défaut, le contrôle dominant est le premier contrôle sélectionné.  
  
-   [Sélection de plusieurs contrôles](../windows/selecting-multiple-controls.md)  
  
-   [Spécification du contrôle dominant](../windows/specifying-the-dominant-control.md)  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Configuration requise  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)   
 [Contrôles](../mfc/controls-mfc.md)
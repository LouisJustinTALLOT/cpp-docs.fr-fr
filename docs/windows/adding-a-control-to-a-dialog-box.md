---
title: Ajout d’un contrôle à une boîte de dialogue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.dialog
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes, adding controls to
- dialog box controls, adding to dialog boxes
- controls [C++], adding to dialog boxes
ms.assetid: b2a26d19-093f-49ca-93da-fef00dfbb381
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 17c3756dc62fd8872adb8a0fb1b89112ed9771f9
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42608609"
---
# <a name="adding-a-control-to-a-dialog-box"></a>Ajout d'un contrôle dans une boîte de dialogue

### <a name="to-add-a-control-to-a-dialog-box"></a>Pour ajouter un contrôle à une boîte de dialogue

1. Assurez-vous que la fenêtre avec onglet de la boîte de dialogue représente le document actif dans le cadre de l’éditeur. Si une boîte de dialogue n’est pas le document actif, vous ne voyez pas l’ **onglet de l’Éditeur de boîtes de dialogue** dans la **Boîte à outils**.

2. Sous l’ [onglet de l’Éditeur de boîtes de dialogue](../windows/dialog-editor-tab-toolbox.md) de la [fenêtre Boîte à outils](/visualstudio/ide/reference/toolbox), sélectionnez le contrôle souhaité, puis :

   - Cliquez sur la boîte de dialogue à l’emplacement où vous souhaitez placer le contrôle. Le contrôle s’affiche à l’emplacement où vous avez cliqué. Pour plus d’informations, consultez [Ajout de plusieurs contrôles](../windows/adding-multiple-controls.md).

       \- ou -

   - Faites glisser le contrôle à partir de la **boîte à outils** fenêtre à l’emplacement sur votre boîte de dialogue. Pour plus d’informations, consultez [Dimensionnement d’un contrôle pendant son ajout](../windows/sizing-a-control-while-you-add-it.md).

       \- ou -

   - Double-cliquez sur le contrôle dans le **boîte à outils** fenêtre (il apparaît dans votre boîte de dialogue), puis repositionnez le contrôle à l’emplacement de votre choix.

Pour plus d’informations sur les types de contrôles disponibles sur le **boîte à outils** fenêtre, consultez [onglet Éditeur de la boîte de dialogue, fenêtre Boîte à outils](../windows/dialog-editor-tab-toolbox.md).

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)  
[Ajout de gestionnaires d’événements pour les contrôles de boîte de dialogue](../windows/adding-event-handlers-for-dialog-box-controls.md)  
[Contrôles de boîtes de dialogue et types de variables](../ide/dialog-box-controls-and-variable-types.md)
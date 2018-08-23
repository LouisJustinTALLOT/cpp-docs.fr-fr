---
title: Dimensionnement d’un contrôle pendant son ajout | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog box controls, size
- controls [C++], sizing
ms.assetid: 06b1dd2b-0ba1-4e1f-adc3-cb73679f765e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f1693ecdf60109732eaf13f41665590ee806a951
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598760"
---
# <a name="sizing-a-control-while-you-add-it"></a>Dimensionnement d'un contrôle pendant son ajout

### <a name="to-size-a-control-while-you-add-it"></a>Pour dimensionner un contrôle pendant son ajout

1. Sélectionnez un contrôle dans le [fenêtre Boîte à outils](/visualstudio/ide/reference/toolbox).

2. Placez votre curseur (qui apparaît comme forme de croix) à l’emplacement souhaité pour le coin supérieur gauche du nouveau contrôle doivent se trouver sur votre boîte de dialogue.

3. Cliquez et maintenez le bouton de la souris pour ancrer le coin supérieur gauche de votre contrôle sur la boîte de dialogue, puis faites glisser le curseur vers la droite et vers le bas jusqu'à ce que le contrôle est la taille voulue.

   > [!NOTE]
   > Vous pouvez ancrer n’importe lequel des quatre coins du contrôle que vous dessinez. Cette procédure utilisé le coin supérieur gauche comme exemple.

4. Relâchez le bouton de la souris. Le contrôle est placé dans la boîte de dialogue dans la taille spécifiée.

   > [!TIP]
   > Vous pouvez redimensionner le contrôle après le déposant sur la boîte de dialogue en déplaçant les poignées de redimensionnement sur la bordure du contrôle. Pour plus d’informations, consultez [dimensionnement de contrôles individuels](../windows/sizing-individual-controls.md).

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)  
[Ajout de gestionnaires d’événements pour les contrôles de boîte de dialogue](../windows/adding-event-handlers-for-dialog-box-controls.md)  
[Contrôles de boîtes de dialogue et types de variables](../ide/dialog-box-controls-and-variable-types.md)
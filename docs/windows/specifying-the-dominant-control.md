---
title: Spécification du contrôle Dominant | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dominant controls
- Dialog editor, dominant control
- controls [C++], dominant
ms.assetid: 42b523a7-192a-417b-9512-d4af795e002f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 93e8d1dff23d77d861a52d4f1531203ebd05987b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593294"
---
# <a name="specifying-the-dominant-control"></a>Spécification du contrôle dominant

Tout d’abord, le contrôle sélectionné est le contrôle dominant.

### <a name="to-specify-the-dominant-control"></a>Pour spécifier le contrôle dominant

1. Maintenez la **Ctrl** clé et cliquez sur le contrôle que vous souhaitez utiliser pour influencer la taille ou l’emplacement d’autres contrôles *premier*.

   **Remarque** les poignées de redimensionnement du contrôle dominant sont pleines tandis que celles des contrôles secondaires sont vides. Le dimensionnement ou l’alignement est basé sur le contrôle dominant.

### <a name="to-change-the-dominant-control"></a>Pour modifier le contrôle dominant

1. Effacer la sélection actuelle, cliquez en dehors de tous les contrôles actuellement sélectionnés.

2. Répétez la procédure précédente, en sélectionnant un autre contrôle en premier.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Sélection de plusieurs contrôles](../windows/selecting-multiple-controls.md)  
[Sélection de contrôles](../windows/selecting-controls.md)  
[Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)
---
title: En spécifiant l’emplacement et la taille d’une boîte de dialogue (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [C++], size
- dialog boxes [C++], positioning
ms.assetid: 2b7c495e-6595-4cfb-9664-80b2826d0851
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e825dc7b20c0ce75ca1f55fb9ad0310571316a1c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435816"
---
# <a name="specifying-the-location-and-size-of-a-dialog-box-c"></a>En spécifiant l’emplacement et la taille d’une boîte de dialogue (C++)

L’emplacement et la taille d’une boîte de dialogue C++, ainsi que l’emplacement et la taille des contrôles qu’il contient, sont mesurés en unités de boîte de dialogue. Les valeurs pour les contrôles individuels et de la boîte de dialogue s’affichent dans le coin inférieur droit de l’état de Visual Studio barre lorsque vous les sélectionnez.

Il existe trois propriétés que vous pouvez définir dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) pour spécifier où une boîte de dialogue s’affiche à l’écran. Le **Center** propriété est la valeur booléenne ; si vous définissez la valeur sur **True**, la boîte de dialogue s’affiche toujours dans le centre de l’écran. Si vous le définissez sur **False**, vous pouvez ensuite définir le **XPos** et **YPos** propriétés à définir explicitement l’emplacement à l’écran la boîte de dialogue s’affiche. Les propriétés de position sont des valeurs de décalage à partir de l’angle supérieur gauche de la zone d’affichage, qui est définie comme `{X=0, Y=0}`. La position est également basée sur le **Absolute Align** propriété : si **True**, les coordonnées sont exprimées par rapport à l’écran ; si **False**, les coordonnées sont exprimées par rapport à la boîte de dialogue fenêtre propriétaire.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
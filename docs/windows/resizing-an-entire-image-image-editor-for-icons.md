---
title: Redimensionner l’intégralité d’une Image (Éditeur d’images pour les icônes) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], resizing images
- size [C++], images
- images [C++], resizing
- resizing images
ms.assetid: 10782937-7eb4-4340-bdec-618ee7d7904b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5465ccacf6fb051e787cf390c82108cb9344d203
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613107"
---
# <a name="resizing-an-entire-image-image-editor-for-icons"></a>Redimensionnement de l'intégralité d'une image (Éditeur d'images pour les icônes)

### <a name="to-resize-an-entire-image-using-the-properties-window"></a>Pour redimensionner l’intégralité d’une image à l’aide de la fenêtre Propriétés

1. Ouvrez l’image dont vous souhaitez modifier les propriétés.

2. Dans le **largeur** et **hauteur** zones dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), tapez les dimensions que vous souhaitez.

   Si vous augmentez la taille de l’image, le **Image** éditeur étend l’image vers la droite, vers le bas, ou les deux et remplit la nouvelle région avec la couleur d’arrière-plan actuelle. L’image n’est pas étiré.

   Si vous réduisez la taille de l’image, le **Image** éditeur rogne l’image sur le bord droit ou inférieur, ou les deux.

   > [!NOTE]
   > Vous pouvez utiliser la **largeur** et **hauteur** propriétés pour redimensionner l’image entière en ne pas pour une sélection partielle.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Aucun.

## <a name="see-also"></a>Voir aussi

[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)  
[Redimensionnement d’une Image](../windows/resizing-an-image-image-editor-for-icons.md)
---
title: Rendre des contrôles la même largeur, hauteur ou taille | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Make Same Size command
- controls [C++], sizing
ms.assetid: 94b50613-67e2-497b-a2b6-6d98dccfd345
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5077d2dcd426182495cc7a414aca7ca411d1fa60
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605374"
---
# <a name="making-controls-the-same-width-height-or-size"></a>Définition de la même largeur, hauteur ou taille pour des contrôles

Vous pouvez redimensionner un groupe de contrôles en fonction de la taille du contrôle dominant. Vous pouvez également [redimensionner un contrôle basé sur les dimensions de son texte de légende](../windows/sizing-individual-controls.md).

### <a name="to-make-controls-the-same-width-height-or-size"></a>Pour rendre les contrôles la même largeur, hauteur ou taille

1. [Sélectionnez les contrôles](../windows/selecting-multiple-controls.md) vous voulez redimensionner.

   Le contrôle sélectionné en premier dans la série est le contrôle dominant. La taille finale des contrôles dans le groupe dépend de la taille du contrôle dominant. Pour plus d’informations sur la sélection du contrôle dominant, consultez [spécification du contrôle Dominant](../windows/specifying-the-dominant-control.md).

2. À partir de la **Format** menu, choisissez **Uniformiser la taille**, puis choisissez une des commandes suivantes :

   - **Les deux**

   - **Hauteur**

   - **Largeur**

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)  
[Contrôles](../mfc/controls-mfc.md)
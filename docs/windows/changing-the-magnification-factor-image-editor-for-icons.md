---
title: Modification du facteur d’agrandissement (Éditeur d’images pour les icônes) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- images [C++], magnification in Image editor
- magnification, Image editor
- Image editor [C++], magnification
ms.assetid: d1b0c9e0-fe54-4b2a-b75e-ffa0fa7c8cd9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d7c7f95179f91577725821dd9348cd4b26b99ff3
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606760"
---
# <a name="changing-the-magnification-factor-image-editor-for-icons"></a>Modification du facteur d'agrandissement (Éditeur d'images pour les icônes)

Par défaut, l’éditeur d’images affiche la vue dans le volet de gauche en taille réelle et la vue dans le volet droit en taille réelle de 6 heures. Le facteur d’agrandissement (indiqué dans la barre d’état en bas de l’espace de travail) est le rapport entre la taille réelle de l’image et la taille affichée. Le facteur par défaut est 6 et la plage est comprise entre 1 et 10.

### <a name="to-change-the-magnification-factor"></a>Pour modifier le facteur d’agrandissement

1. Sélectionnez le **Éditeur d’images** volet dont vous souhaitez modifier le facteur d’agrandissement.

2. Sur le [barre d’outils Éditeur d’images](../windows/toolbar-image-editor-for-icons.md), cliquez sur la flèche à droite de la [outil Loupe](../windows/toolbar-image-editor-for-icons.md) et sélectionnez le facteur d’agrandissement dans le sous-menu : **1 X**, **2 X**, **6 X**, ou **8 X**.

   > [!NOTE]
   > Pour sélectionner un facteur d’agrandissement autre que ceux répertoriés dans le **Magnify** outil, utilisez les touches accélérateur.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Aucun.

## <a name="see-also"></a>Voir aussi

[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)  
[Volets de fenêtre](../windows/window-panes-image-editor-for-icons.md)
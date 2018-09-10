---
title: Création d’une icône de 256 couleurs ou d’un curseur (Éditeur d’images pour les icônes) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- 256-color palette
- cursors [C++], color
- colors [C++], icons
- colors [C++], cursors
- icons, color
ms.assetid: 2738089b-4fd3-4c45-96ae-6a15e4c6b780
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 930a73f478b02d5aa7a16f262f98131dccba9f76
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315924"
---
# <a name="creating-a-256-color-icon-or-cursor-image-editor-for-icons"></a>Création d'une icône ou d'un curseur 256 couleurs (Éditeur d'images pour les icônes)

À l’aide de la **Image** éditeur, icônes et curseurs peuvent être de grande taille (64 x 64) avec une palette de 256 couleurs. Après avoir créé la ressource, un style d’image de périphérique est sélectionné.

### <a name="to-create-a-256-color-icon-or-cursor"></a>Pour créer une icône de 256 couleurs ou d’un curseur

1. Dans [affichage des ressources](../windows/resource-view-window.md), avec le bouton droit de votre fichier .rc, puis choisissez **insérer la ressource** dans le menu contextuel. (Si vous disposez déjà d’une ressource image dans votre fichier .rc, par exemple un curseur, vous pouvez simplement cliquer sur le **curseur** dossier et sélectionnez **insérer Cursor** dans le menu contextuel.)

   > [!NOTE] 
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

2. Dans le [boîte de dialogue Ajouter une ressource](../windows/add-resource-dialog-box.md), sélectionnez **icône** ou **curseur** et cliquez sur **New**.

3. Sur le **Image** menu, cliquez sur **nouvelle Image de périphérique**.

4. Sélectionnez le style de l’image de 256 couleurs souhaité.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Aucun.

## <a name="see-also"></a>Voir aussi

[À l’aide de la Palette 256 couleurs](../windows/using-the-256-color-palette-image-editor-for-icons.md)  
[Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)  
[Icônes et curseurs : ressources Image pour les périphériques d’affichage](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)
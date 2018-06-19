---
title: Création d’une Image de périphérique (Éditeur d’images pour les icônes) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.icon
dev_langs:
- C++
helpviewer_keywords:
- cursors [C++], creating
- icons [C++], creating
- display devices
- display devices, creating image
- images [C++], creating for display devices
- icons [C++], inserting
ms.assetid: 5a536928-32df-4ace-beb1-1521ce3b871f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d8fc1ce4bd5a6e125ece7461d100950f255dee44
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873223"
---
# <a name="creating-a-device-image-image-editor-for-icons"></a>Création d'une image de périphérique (Éditeur d'images pour les icônes)
Lorsque vous créez une nouvelle icône ou curseur ressource, l’Image de l’éditeur crée d’abord une image dans un style spécifique (32 x 32, 16 couleurs pour les icônes et 32 x 32, Monochrome pour les curseurs). Vous pouvez ensuite ajouter des images de différentes tailles et des styles à l’icône d’origine et modifier chaque image supplémentaire, si nécessaire, pour les périphériques d’affichage différent. Vous pouvez également modifier une image en effectuant une opération de couper-coller à partir d’un type d’image existant ou d’une bitmap créée dans un programme graphique.  
  
 Lorsque vous ouvrez la ressource icône ou curseur dans le [Éditeur d’images](../windows/image-editor-for-icons.md), l’image de la plupart des étroitement le périphérique d’affichage actuel est ouverte par défaut.  
  
### <a name="to-create-a-new-icon-or-cursor"></a>Pour créer une nouvelle icône ou curseur  
  
1.  Dans [affichage des ressources](../windows/resource-view-window.md), avec le bouton droit de votre fichier .rc, puis choisissez **insérer la ressource** dans le menu contextuel. (Si vous disposez déjà d’une ressource image dans votre fichier .rc, par exemple un curseur, vous pouvez simplement cliquer sur le **curseur** et sélectionnez **insérer Cursor** dans le menu contextuel.)  
  
    > [!NOTE]
    >  Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Dans le [boîte de dialogue Ajouter une ressource](../windows/add-resource-dialog-box.md), sélectionnez **icône** ou **curseur** et cliquez sur **nouveau**. Pour les icônes, cela crée une ressource icône 16 couleurs, 32 x 32. Pour les curseurs, 32 x 32, Monochrome (2 couleurs) image est créée.  
  
     Si un signe plus (**+**) s’affiche en regard du type de ressource d’image dans le **insérer la ressource** boîte de dialogue, cela signifie que les modèles de la barre d’outils sont disponibles. Cliquez sur le signe plus pour développer la liste des modèles, sélectionnez un modèle, puis cliquez sur **nouveau**.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 **Spécifications**  
  
 Aucun  
  
## <a name="see-also"></a>Voir aussi  
 [Icônes et curseurs : ressources Image pour les périphériques d’affichage](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)   
 [Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Icônes et curseurs : ressources Image pour les périphériques d’affichage](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)

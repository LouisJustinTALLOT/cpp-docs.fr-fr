---
title: Modification de parties d’une Image (Éditeur d’images pour les icônes) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], editing images
- Clipboard [C++], pasting
- images [C++], editing
- images [C++], deleting selected parts
- images [C++], copying selected parts
- images [C++], moving selected parts
- images [C++], dragging and replicating selected parts
- images [C++], pasting into
- graphics [C++], editing
ms.assetid: ff4f5fef-71a4-4fd8-825e-049399fed391
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b33a591a2f38062b5eaf81b0f56ab73a36f4c90c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876850"
---
# <a name="editing-parts-of-an-image-image-editor-for-icons"></a>Modification de parties d'une image (Éditeur d'images pour les icônes)
Vous pouvez effectuer les opérations de modification standard — couper, copier, effacer et déplacement : sur un [sélection](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md), indique si la sélection est l’image entière ou une partie de celui-ci. Étant donné que l’éditeur d’images utilise le Presse-papiers Windows, vous pouvez transférer des images entre l’éditeur d’images et d’autres applications pour Windows.  
  
 En outre, vous pouvez redimensionner la sélection, qu’il s’agisse de l’image entière ou une partie.  
  
### <a name="to-cut-the-current-selection-and-move-it-to-the-clipboard"></a>Pour couper la sélection actuelle et les déplacer vers le Presse-papiers  
  
1.  Cliquez sur **couper** sur la **modifier** menu.  
  
### <a name="to-copy-the-selection"></a>Pour copier la sélection  
  
1.  Placez le pointeur à l’intérieur de la bordure de sélection ou n’importe où sur sauf les poignées de redimensionnement.  
  
2.  Maintenez la **CTRL** clé lorsque vous faites glisser la sélection vers un nouvel emplacement. La zone de la sélection d’origine est inchangée.  
  
3.  Pour copier la sélection dans l’image à son emplacement actuel, cliquez en dehors du curseur de sélection.  
  
### <a name="to-paste-the-clipboard-contents-into-an-image"></a>Pour coller le contenu du Presse-papiers dans une image  
  
1.  À partir de la **modifier** menu, choisissez **coller**.  
  
     Le contenu du Presse-papiers, entouré par la bordure de sélection, s’affichent dans le coin supérieur gauche du volet.  
  
2.  Placez le pointeur à l’intérieur de la bordure de sélection et faites glisser l’image à l’emplacement souhaité sur l’image.  
  
3.  Pour ancrer l’image à son nouvel emplacement, cliquez en dehors de la bordure de sélection.  
  
### <a name="to-delete-the-current-selection-without-moving-it-to-the-clipboard"></a>Pour supprimer la sélection actuelle sans le déplacer dans le Presse-papiers  
  
1.  À partir de la **modifier** menu, choisissez **supprimer**.  
  
     La zone d’origine de la sélection est remplie avec la couleur d’arrière-plan actuelle.  
  
    > [!NOTE]
    >  Vous pouvez accéder à couper, copier, coller et supprimer des commandes en cliquant avec le bouton droit dans la fenêtre Affichage des ressources.  
  
### <a name="to-move-the-selection"></a>Pour déplacer la sélection  
  
1.  Placez le pointeur à l’intérieur de la bordure de sélection ou n’importe où sur sauf les poignées de redimensionnement.  
  
2.  Faites glisser la sélection vers son nouvel emplacement.  
  
3.  Pour ancrer la sélection dans l’image à son nouvel emplacement, cliquez en dehors de la bordure de sélection.  
  
 Pour plus d’informations sur le dessin avec une sélection, consultez [création d’un pinceau personnalisé](../windows/creating-a-custom-brush-image-editor-for-icons.md).  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Spécifications  
  
 Aucun  
  
## <a name="see-also"></a>Voir aussi  
 [Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Modification de ressources graphiques](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)


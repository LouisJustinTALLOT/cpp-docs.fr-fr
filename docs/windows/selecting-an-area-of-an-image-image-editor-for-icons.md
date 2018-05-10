---
title: Sélection d’une zone d’une Image (Éditeur d’images pour les icônes) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.editing
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], image selection
- Image editor [C++], selecting images
- images [C++], selecting
- cursors [C++], selecting areas of
ms.assetid: 8b6ce4ad-eba1-4ece-86ba-cea92c3edff2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 07cb7528e25604e873f6da92193a97cf79700799
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
---
# <a name="selecting-an-area-of-an-image-image-editor-for-icons"></a>Sélection d'une zone d'une image (Éditeur d'images pour les icônes)
Vous pouvez utiliser les outils de sélection pour définir une zone d’une image que vous souhaitez couper, copier, effacer, redimensionner, inverser ou déplacer. Avec la **sélection d’un Rectangle** outil, vous pouvez définir et sélectionner une zone rectangulaire de l’image. Avec la **Sélection irrégulière** outil que vous pouvez dessiner un contour à main levée de la zone que vous souhaitez sélectionner pour l’opérations couper, copier ou autre opération.  
  
> [!NOTE]
>  Consultez le **sélection d’un Rectangle** et **Sélection irrégulière** outils décrits dans [barre d’outils Éditeur d’images](../windows/toolbar-image-editor-for-icons.md) ou d’afficher les info-bulles associées à chaque bouton de la **Éditeur d’images** barre d’outils.  
  
 Vous pouvez également créer un pinceau personnalisé à partir d’une sélection. Pour plus d’informations, consultez [création d’un pinceau personnalisé](../windows/creating-a-custom-brush-image-editor-for-icons.md).  
  
### <a name="to-select-an-area-of-an-image"></a>Pour sélectionner une zone d’une image  
  
1.  Sur le **Éditeur d’images** barre d’outils (ou à partir de la **Image** menu, **outils** commande), cliquez sur l’outil Sélection.  
  
2.  Déplacer le point d’insertion vers un coin de la zone d’image que vous souhaitez sélectionner. Croix s’affiche lorsque le point d’insertion se trouve sur l’image.  
  
3.  Faites glisser le point d’insertion vers le coin opposé de la zone que vous souhaitez sélectionner. Un rectangle montre les pixels qui seront sélectionnés. Tous les pixels du rectangle, y compris celles figurant sous le rectangle, sont inclus dans la sélection.  
  
4.  Relâchez le bouton de la souris. La bordure de sélection délimite la zone sélectionnée.  
  
### <a name="to-select-an-entire-image"></a>Pour sélectionner l’intégralité d’une image  
  
1.  Cliquez sur l’image en dehors de la sélection actuelle. La bordure de sélection met le focus et englobe l’image entière à nouveau.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Spécifications  
  
 Aucun  
  
## <a name="see-also"></a>Voir aussi  
 [Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Modification de ressources graphiques](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)


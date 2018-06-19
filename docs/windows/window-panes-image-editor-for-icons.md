---
title: Volets de fenêtre (Éditeur d’images pour les icônes) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
dev_langs:
- C++
helpviewer_keywords:
- graphics editor [C++]
- Image editor [C++], panes
ms.assetid: d66ea5b3-e2e2-4fc4-aa99-f50022cc690e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e899729e70db089c1c55f00aa9c4196a22c67060
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892837"
---
# <a name="window-panes-image-editor-for-icons"></a>Volets de fenêtre (Éditeur d'images pour les icônes)
En règle générale, la fenêtre de l’éditeur d’images affiche une image dans les deux volets séparés par une barre de fractionnement. Une vue est la taille réelle et l’autre est agrandie (facteur d’agrandissement de la valeur par défaut est 6). Les vues dans ces deux volets sont mis à jour automatiquement : modifications que vous apportez dans un volet sont immédiatement répercutées dans l’autre. Les deux volets facilitent vous permet de travailler sur une vue agrandie de votre image, dans laquelle vous pouvez distinguer les pixels et, en même temps, observez l’effet de votre travail sur l’affichage de la taille réelle de l’image.  
  
 Le volet gauche utilise autant de place que si nécessaire (la moitié de la fenêtre Image) pour afficher la vue de facteur de zoom de 1:1 (la valeur par défaut) de votre image. Le volet de droite affiche l’image agrandie (facteur d’agrandissement 6:1 par défaut). Vous pouvez [modifier le grossissement](../windows/changing-the-magnification-factor-image-editor-for-icons.md) dans chaque volet en utilisant le **loupe** outil sur le [barre d’outils Éditeur d’images](../windows/toolbar-image-editor-for-icons.md) ou en utilisant les touches accélérateur.  
  
 Vous pouvez agrandir le volet de la fenêtre de l’éditeur d’images de plus petit et utiliser les deux volets pour afficher différentes parties d’une image de grande taille. Cliquez dans le volet pour le sélectionner.  
  
 Vous pouvez modifier les tailles relatives des volets en plaçant le pointeur sur la barre de fractionnement et de déplacement de la barre de fractionnement vers la droite ou la gauche. La barre de fractionnement peut déplacer à côté, si vous souhaitez travailler sur un seul volet.  
  
 Si le volet de l’éditeur d’Image est agrandi ou supérieure à 4, vous pouvez [afficher une grille de pixels](../windows/displaying-or-hiding-the-pixel-grid-image-editor-for-icons.md) qui délimite les pixels individuels dans l’image.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Spécifications  
 Aucun  
  
## <a name="see-also"></a>Voir aussi  
 [Touches accélérateur](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)


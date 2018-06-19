---
title: 'Comment : copier des ressources | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.resvw.resource.copying
- vs.resvw.resource.copying
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], moving between files
- resources [Visual Studio], copying
- resource files, copying or moving resources between
- resource files, tiling
- .rc files, copying resources between
- rc files, copying resources between
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4b173be24e9f177a3156f740fcb07240c30fec75
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879846"
---
# <a name="how-to-copy-resources"></a>Comment : copier des ressources
Vous pouvez copier des ressources à partir d’un fichier vers un autre sans les modifier ou vous pouvez [modifier la langue ou la condition d’une ressource lors de la copie](../windows/how-to-change-the-language-or-condition-of-a-resource-while-copying.md).  
  
 Vous pouvez facilement copier les ressources à partir d’une ressource existante ou d’un fichier exécutable à votre fichier de ressources actuel. Pour ce faire, vous ouvrez les deux fichiers contenant des ressources en même temps et faites glisser des éléments à partir d’un fichier vers un autre, ou copiez et collez entre les deux fichiers. Cette méthode fonctionne pour les fichiers de ressources (.rc) de script et les fichiers de ressources (.rct) de modèle, ainsi que les fichiers exécutables (.exe).  
  
> [!NOTE]
>  Visual C++ inclut des exemples de fichiers de ressources que vous pouvez utiliser dans votre application. Pour plus d’informations, consultez [CLIPART : ressources communes](http://msdn.microsoft.com/en-us/9bac2891-b6b3-49ec-a287-cec850c707e0).  
  
 Vous pouvez utiliser la méthode glisser-déplacer entre les fichiers .rc qui sont ouverts [en dehors du projet](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).  
  
### <a name="to-copy-resources-between-files-using-the-drag-and-drop-method"></a>Pour copier des ressources entre les fichiers à l’aide de la méthode glisser-déplacer  
  
1.  Ouvrez les deux fichiers de ressources autonomes (pour plus d’informations, consultez [affichage des ressources dans un fichier à l’extérieur d’un projet .rc](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Par exemple, ouvrez Source1.rc et Source2.rc.  
  
2.  Dans le premier fichier .rc, cliquez sur la ressource que vous souhaitez copier. Par exemple, dans Source1.rc, cliquez sur IDD_DIALOG1.  
  
3.  Maintenez la touche CTRL enfoncée et faites glisser la ressource pour le second fichier .rc. Par exemple, faites glisser IDD_DIALOG1 de Source1.rc vers Source2.rc.  
  
    > [!NOTE]
    >  En faisant glisser la ressource sans maintenir la touche CTRL enfoncée déplace la ressource au lieu de les copier.  
  
### <a name="to-copy-resources-using-copy-and-paste"></a>Pour copier des ressources à l’aide de copier et coller  
  
1.  Ouvrez les deux fichiers de ressources autonomes (pour plus d’informations, consultez [affichage des ressources dans un fichier à l’extérieur d’un projet .rc](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Par exemple, Source1.rc et Source2.rc.  
  
2.  Dans le fichier source à partir duquel vous voulez copier une ressource (par exemple, Source1.rc), une ressource avec le bouton droit et choisissez **copie** dans le menu contextuel.  
  
3.  Cliquez sur le fichier de ressources dans lequel vous voulez coller la ressource (par exemple, Source2.rc). Choisissez **coller** dans le menu contextuel.  
  
    > [!NOTE]
    >  Ne peut pas faire glisser et déplacer, copier, Couper ou de coller entre les fichiers de ressources dans le projet (affichage des ressources) et des fichiers .rc autonomes (ceux qui sont ouverts dans des fenêtres de document). Vous pouvez le faire dans les versions précédentes du produit.  
  
    > [!NOTE]
    >  Pour éviter les conflits avec les noms de symboles ou les valeurs dans le fichier existant, Visual C++ peut modifier valeur du symbole de la ressource transférée ou le nom et valeur lorsque vous le copiez dans le nouveau fichier.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Spécifications  
  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : ouvrir un fichier de Script de ressources en dehors d’un projet (autonome)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)   
 [Fichiers de ressources](../windows/resource-files-visual-studio.md)   
 [Éditeurs de ressources](../windows/resource-editors.md)
---
title: "Enregistrement de Bitmaps au format GIF ou JPEG (Éditeur d’images pour les icônes) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.image.editing
dev_langs:
- C++
helpviewer_keywords:
- .gif files, saving bitmaps as
- jpg files, saving bitmaps as
- jpeg files, saving bitmaps as
- .jpg files, saving bitmaps as
- Image editor [C++], converting image formats
- gif files, saving bitmaps as
- bitmaps [C++], converting formats
- .jpeg files, saving bitmaps as
- graphics [C++], converting formats
- images [C++], converting formats
ms.assetid: 115df69f-10fb-4e6f-906b-853c1e4a54af
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f3fe626357283dde8d8f283c6d0aa406ec6c1db0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="saving-bitmaps-as-gifs-or-jpegs-image-editor-for-icons"></a>Enregistrement de bitmaps au format GIF ou JPEG (Éditeur d'images pour les icônes)
Lorsque vous créez une image bitmap, l’image est créée dans le format bitmap (.bmp). Vous pouvez, toutefois, enregistrez l’image au format GIF ou JPEG ou dans d’autres formats graphiques.  
  
> [!NOTE]
>  Ce processus ne s’applique pas aux icônes et curseurs.  
  
### <a name="to-create-and-save-a-bitmap-as-a-gif-or-jpeg"></a>Pour créer et enregistrer une image bitmap en tant que .gif ou .jpeg  
  
1.  À partir de la **fichier** menu, choisissez **ouvrir**, puis cliquez sur **fichier**.  
  
2.  Dans le **boîte de dialogue Nouveau fichier**, cliquez sur le **Visual C++** dossier, puis sélectionnez **fichier Bitmap (.bmp)** dans les **modèles** , puis cliquez sur  **Ouvrez**.  
  
     La bitmap s’ouvre dans le **Image** éditeur.  
  
3.  Apportez les modifications nécessaires à la bitmap.  
  
4.  Lorsque la bitmap est ouverte dans le **Image** éditeur, cliquez sur **enregistrer *nom de fichier*.bmp sous** sur la **fichier** menu.  
  
5.  Dans le **enregistrer le fichier sous** boîte de dialogue, tapez le nom que vous souhaitez attribuer au fichier et l’extension correspondant au format de fichier souhaité dans le **nom de fichier** boîte. Par exemple, monfichier.gif.  
  
     **Remarque** vous devez créer ou ouvrir l’image bitmap en dehors de votre projet afin d’enregistrer dans un autre format de fichier. Si vous créez ou ouvrez dans votre projet, le **enregistrer en tant que** n’est pas disponible. Pour plus d’informations, consultez [affichage des ressources dans un fichier de Script de ressources en dehors d’un projet (autonome)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).  
  
6.  Cliquez sur **Enregistrer**.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="see-also"></a>Voir aussi  
 [Modification de ressources graphiques](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)


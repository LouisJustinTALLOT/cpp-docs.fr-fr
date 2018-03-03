---
title: "Création d’une icône ou une autre Image (Éditeur d’images pour les icônes) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.bitmap
dev_langs:
- C++
helpviewer_keywords:
- bitmaps [C++]
- images [C++], creating
- resource toolbars
- resources [Visual Studio], creating images
- bitmaps [C++], creating
- graphics [C++], creating
- Image editor [C++], creating images
ms.assetid: 66db3fb2-cfc1-48a2-9bdd-53f61eb7ee30
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ae1cc8525b0c93cff5564c2185d80480a632718b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="creating-an-icon-or-other-image-image-editor-for-icons"></a>Création d'une icône ou d'une autre image (Éditeur d'images pour les icônes)
Vous pouvez créer une nouvelle image (bitmap, icône, curseur ou barre d’outils), puis utiliser l’éditeur d’images pour personnaliser son apparence. Vous pouvez également créer une nouvelle bitmap à motifs d’après un [modèle](../windows/how-to-use-resource-templates.md).  
  
### <a name="to-add-a-new-image-resource-to-an-unmanaged-c-project"></a>Pour ajouter une nouvelle ressource image à un projet C++ non managé  
  
1.  Dans [affichage des ressources](../windows/resource-view-window.md), avec le bouton droit de votre fichier .rc, puis choisissez **insérer la ressource** dans le menu contextuel. (Si vous disposez déjà d’une ressource image dans votre fichier .rc, par exemple un curseur, vous pouvez simplement cliquer sur le **curseur** et sélectionnez **insérer Cursor** dans le menu contextuel.)  
  
    > [!NOTE]
    >  **Remarque** Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Dans le [boîte de dialogue Ajouter une ressource](../windows/add-resource-dialog-box.md), sélectionnez le type de ressource image que vous souhaitez créer (**Bitmap**, par exemple) puis cliquez sur **nouveau**.  
  
     Si un signe plus (**+**) s’affiche en regard du type de ressource d’image dans le **insérer la ressource** boîte de dialogue, cela signifie que les modèles de la barre d’outils sont disponibles. Cliquez sur le signe plus pour développer la liste des modèles, sélectionnez un modèle, puis cliquez sur **nouveau**.  
  
### <a name="to-add-a-new-image-resource-to-a-project-in-a-net-programming-language"></a>Pour ajouter une nouvelle ressource image à un projet dans un langage de programmation .NET  
  
1.  Dans **l’Explorateur de solutions**, cliquez sur le dossier du projet (par exemple, **WindowsApplication1**).  
  
2.  Dans le menu contextuel, cliquez sur **ajouter**, puis choisissez **ajouter un nouvel élément**.  
  
3.  Dans le **catégories** volet, développez le **des éléments de projet Local** dossier, puis choisissez **ressources**.  
  
4.  Dans le **modèles** volet, choisissez le type de ressource que vous souhaitez ajouter à votre projet.  
  
     La ressource est ajoutée à votre projet dans l’Explorateur de solutions et de la ressource s’ouvre dans le [Éditeur d’images](../windows/image-editor-for-icons.md). Vous pouvez maintenant utiliser tous les outils disponibles dans l’éditeur d’images pour modifier votre image. Pour plus d’informations sur l’ajout d’images à un projet managé, consultez [chargement d’une image au moment du Design](/dotnet/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms).  
  
    > [!NOTE]
    >  Toutes les ressources managées que vous souhaitez modifier doivent être liées. Les éditeurs de ressources Visual Studio ne prennent pas en charge la modification des ressources incorporées. Pour plus d’informations, consultez [création de fichiers de ressources](/dotnet/framework/resources/creating-resource-files-for-desktop-apps) dans les *Guide du développeur .NET Framework*.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Configuration requise  
  
 Aucun.  
  
## <a name="see-also"></a>Voir aussi  
 [Icônes et curseurs : ressources Image pour les périphériques d’affichage](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)   
 [Conversion de Bitmaps en barres d’outils](../windows/converting-bitmaps-to-toolbars.md)   
 [Création de nouvelles barres d’outils](../windows/creating-new-toolbars.md)   
 [Modification de ressources graphiques](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Éditeur d’images pour les icônes](../windows/image-editor-for-icons.md)


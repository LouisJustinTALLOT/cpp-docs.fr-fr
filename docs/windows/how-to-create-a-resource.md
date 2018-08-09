---
title: 'Comment : créer une ressource | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- toolbars [C++], resources
- resource toolbars
- resources [Visual Studio], creating
ms.assetid: aad44914-9145-45a3-a7d8-9de89b366716
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b44156ae26d77247a909e45061b00a6a1d892d79
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016926"
---
# <a name="how-to-create-a-resource"></a>Comment : créer une ressource
> [!NOTE]
>  **Affichage des ressources** n’est pas pris en charge dans les éditions Express.  
  
### <a name="to-create-a-new-resource-in-resource-view"></a>Pour créer une ressource dans l’affichage des ressources  
  
1.  Avec le focus sur votre fichier .rc dans [affichage des ressources](../windows/resource-view-window.md), cliquez sur le **modifier** menu et choisissez **ajouter une ressource** (ou cliquez sur le fichier .rc dans **affichagedesressources** et choisissez **ajouter une ressource** dans le menu contextuel).  
  
     > [!NOTE] 
     > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Dans la [boîte de dialogue Ajouter une ressource](../windows/add-resource-dialog-box.md), choisissez le type de ressource que vous souhaitez ajouter à votre projet.  
  
### <a name="to-create-a-new-resource-in-solution-explorer"></a>Pour créer une ressource dans l’Explorateur de solutions  
  
1.  Dans l' **Explorateur de solutions**, cliquez avec le bouton droit sur le dossier du projet, choisissez **Ajouter**, puis cliquez sur **Ajouter une ressource** dans le menu contextuel.  
  
     Si vous n'avez pas déjà un fichier .rc dans votre projet, cette étape permet d'en créer un. Vous pouvez ensuite répéter cette étape pour ajouter des types de ressource spécifiques au nouveau fichier .rc.  
  
2.  Dans la [boîte de dialogue Ajouter une ressource](../windows/add-resource-dialog-box.md), choisissez le type de ressource que vous souhaitez ajouter à votre projet.  
  
### <a name="to-create-a-new-resource-in-class-view"></a>Pour créer une ressource dans l’affichage de classes  
  
1.  Dans [affichage de classes](http://msdn.microsoft.com/8d7430a9-3e33-454c-a9e1-a85e3d2db925), avec le bouton droit de votre classe et choisissez **ajouter**, puis cliquez sur **ajouter une ressource** dans le menu contextuel.  
  
2.  Dans la [boîte de dialogue Ajouter une ressource](../windows/add-resource-dialog-box.md), choisissez le type de ressource que vous souhaitez ajouter à votre projet.  
  
### <a name="to-create-a-new-resource-from-the-project-menu"></a>Pour créer une ressource à partir du menu Projet  
  
1.  Dans le menu **Projet** , choisissez **Ajouter une ressource**.  
  
 Lorsque vous créez une nouvelle ressource, Visual C++ lui assigne un nom unique, par exemple, `IDD_Dialog1`. Vous pouvez personnaliser cet ID de ressource en modifiant les propriétés de la ressource dans l'éditeur de ressources associé ou dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window).  
  
 Vous pouvez créer une ressource en tant que ressource par défaut (une ressource qui n'est pas basée sur un modèle) ou en tant que ressource inspirée d'un [modèle](../windows/how-to-use-resource-templates.md).  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*.

## <a name="requirements"></a>Configuration requise    
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers de ressources](../windows/resource-files-visual-studio.md)   
 [Éditeurs de ressources](../windows/resource-editors.md)   
 [Ajouter une ressource, boîte de dialogue](../windows/add-resource-dialog-box.md)
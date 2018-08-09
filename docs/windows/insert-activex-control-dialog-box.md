---
title: Boîte de dialogue de contrôle ActiveX insérer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.insertActiveXControls
dev_langs:
- C++
helpviewer_keywords:
- Insert ActiveX Control dialog box
- ActiveX controls [C++], adding to dialog boxes
ms.assetid: 06638ea3-0726-40da-a989-9b89292d0e3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0201619d463d677eae312d70a543a19887dbdb40
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011788"
---
# <a name="insert-activex-control-dialog-box"></a>Insérer un contrôle ActiveX (boîte de dialogue)
Cette boîte de dialogue vous permet de [insérer des contrôles ActiveX dans votre boîte de dialogue](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md) tout en utilisant le [éditeur de boîte de dialogue](../windows/dialog-editor.md).  
  
### <a name="activex-control"></a>Contrôle ActiveX 
 Affiche une liste de contrôles Active X. Insertion d’un contrôle à partir de cette boîte de dialogue ne génère pas une classe wrapper. Si vous avez besoin d’une classe wrapper, utilisez [affichage de classes](http://msdn.microsoft.com/8d7430a9-3e33-454c-a9e1-a85e3d2db925) pour en créer une (pour plus d’informations, consultez [Ajout d’une classe](../ide/adding-a-class-visual-cpp.md)). Si un contrôle ActiveX n’apparaît pas dans cette boîte de dialogue, essayez d’installer le contrôle selon les instructions du fournisseur.  
  
### <a name="path"></a>Chemin d’accès  
 Affiche le fichier dans lequel le contrôle ActiveX est trouvé.  
  
 Vous pouvez placer des contrôles dans le **boîte à outils** fenêtre pour pouvoir accéder facilement. Pour plus d’informations, consultez [boîte de dialogue Personnaliser la boîte à outils](http://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb).  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Configuration requise  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de boîte de dialogue, onglet de boîte à outils](../windows/dialog-editor-tab-toolbox.md)   
 [Fichiers de ressources](../windows/resource-files-visual-studio.md)   
 [Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)
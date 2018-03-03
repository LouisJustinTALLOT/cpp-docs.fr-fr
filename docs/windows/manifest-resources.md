---
title: Ressources de manifeste | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- manifest resources
- resources [Visual Studio], manifest
ms.assetid: 8615334c-22a0-44c0-93e0-5924528c9917
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 56a41a7901e41f4c76fbb9fcbf5930ec97c3b866
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="manifest-resources"></a>Ressources de manifeste
Les ressources de manifeste sont des fichiers XML qui décrivent les dépendances qu'une application utilise. Par exemple, dans Visual Studio, le fichier manifeste généré par l'Assistant MFC définit la DLL de contrôle commun Windows que l'application doit utiliser, version 5.0 ou 6.0 :  
  
```  
<description>Your app description here</description>   
<dependency>   
    <dependentAssembly>   
        <assemblyIdentity   
            type="win32"   
            name="Microsoft.Windows.Common-Controls"   
            version="6.0.0.0"   
            processorArchitecture="X86"   
            publicKeyToken="6595b64144ccf1df"   
            language="*"   
        />   
    </dependentAssembly>   
</dependency>   
```  
  
 Pour une application Windows XP ou Windows Vista, la ressource de manifeste indique non seulement que l’application utilise la toute dernière version des contrôles communs Windows (v6.0, comme indiqué ci-dessus) mais qu’elle prend également en charge le nouveau [contrôle Syslink](http://msdn.microsoft.com/library/windows/desktop/bb760706).  
  
 Pour afficher les informations de version et de type contenues dans une ressource de manifeste, vous pouvez ouvrir le fichier dans une visionneuse XML ou dans l' [Éditeur de texte](http://msdn.microsoft.com/en-us/508e1f18-99d5-48ad-b5ad-d011b21c6ab1)Visual Studio. Pour plus d'informations, voir [Ouverture d'une ressource de manifeste dans l'éditeur de texte Visual Studio](../windows/how-to-open-a-manifest-resource.md).  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, l’affichage de ressources statiques et l’assignation de chaînes de ressources à des propriétés, consultez  [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
## <a name="limitations"></a>Limitations  
 Vous ne pouvez avoir qu'une seule ressource de manifeste par module.  
  
## <a name="requirements"></a>Configuration requise  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles](../mfc/controls-mfc.md)   
 [Utilisation des fichiers de ressources](../windows/working-with-resource-files.md)
---
title: -/NODEFAULTLIB (ignorer les bibliothèques) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.OVERWRITEAllDefaultLibraries
- VC.Project.VCLinkerTool.OVERWRITEDefaultLibraryNames
- /nodefaultlib
dev_langs:
- C++
helpviewer_keywords:
- default libraries, removing
- -NODEFAULTLIB linker option
- libraries, ignore
- NODEFAULTLIB linker option
- /NODEFAULTLIB linker option
- ignore libraries linker option
ms.assetid: 7270b673-6711-468e-97a7-c2925ac2be6e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 51caac10218d5f4d1787b2256875001ac32dc2b9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375712"
---
# <a name="nodefaultlib-ignore-libraries"></a>/NODEFAULTLIB (Ignorer les bibliothèques)
```  
/NODEFAULTLIB[:library]   
```  
  
## <a name="remarks"></a>Notes  
 où :  
  
 *Bibliothèque*  
 Une bibliothèque que vous souhaitez que l’éditeur de liens doivent être ignorées lors de la résolution des références externes.  
  
## <a name="remarks"></a>Notes  
 L’option /NODEFAULTLIB indique à l’éditeur de liens pour supprimer une ou plusieurs bibliothèques par défaut dans la liste des bibliothèques qu’elle parcourt lors de la résolution des références externes.  
  
 Pour créer un fichier .obj qui ne contient pas de références aux bibliothèques par défaut, utilisez [/Zl (Omettre nom de bibliothèque par défaut)](../../build/reference/zl-omit-default-library-name.md).  
  
 Par défaut, /NODEFAULTLIB supprime toutes les bibliothèques par défaut de la liste des bibliothèques qu’elle parcourt lors de la résolution des références externes. Le paramètre facultatif *bibliothèque* paramètre vous permet de supprimer une ou plusieurs bibliothèques spécifiées de la liste des bibliothèques qu’elle parcourt lors de la résolution des références externes. Spécifiez une option /NODEFAULTLIB pour chaque bibliothèque que vous souhaitez exclure.  
  
 L’éditeur de liens résout les références aux définitions externes en recherchant d’abord dans les bibliothèques que vous le spécifiez explicitement, puis par défaut bibliothèques spécifié avec l’option /DEFAULTLIB, puis dans les bibliothèques par défaut nommées dans les fichiers .obj.  
  
 / NODEFAULTLIB :*bibliothèque* substitue [/DEFAULTLIB :](../../build/reference/defaultlib-specify-default-library.md)*bibliothèque* lors de la même *bibliothèque* nom est spécifié dans les deux.  
  
 Si vous utilisez/NODEFAULTLIB, par exemple, pour générer votre programme sans la bibliothèque Runtime C, vous devrez peut-être également utiliser [/ENTRY](../../build/reference/entry-entry-point-symbol.md) pour spécifier le point d’entrée (fonction) de votre programme. Pour plus d’informations, consultez [Fonctionnalités de la bibliothèque CRT](../../c-runtime-library/crt-library-features.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le **l’éditeur de liens** dossier.  
  
3.  Cliquez sur le **entrée**page de propriétés.  
  
4.  Sélectionnez le **ignorer toutes les bibliothèques par défaut** propriété ou spécifier une liste des bibliothèques que vous souhaitez ignorer dans le **bibliothèque spécifique ignorée** propriété. Le **ligne de commande** page de propriétés affichera l’effet des modifications que vous apportez à ces propriétés.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreDefaultLibraryNames%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreAllDefaultLibraries%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)
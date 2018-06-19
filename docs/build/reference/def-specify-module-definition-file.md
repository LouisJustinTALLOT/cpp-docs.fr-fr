---
title: -DEF (spécifier un fichier de définition de Module) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ModuleDefinitionFile
- /def
dev_langs:
- C++
helpviewer_keywords:
- module definition files, specifying
- DEF linker option
- -DEF linker option
- module definition files
- /DEF linker option
ms.assetid: 6497fa68-65f0-48ca-8f66-b87166fc631a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f0c712b81fbb755edd132c6f97efc906ba4f5ff9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371149"
---
# <a name="def-specify-module-definition-file"></a>/DEF (Spécifier le fichier de définition de module)
```  
/DEF:filename  
```  
  
## <a name="remarks"></a>Notes  
 où :  
  
 *filename*  
 Le nom d’un fichier de définition de module (.def) à passer à l’éditeur de liens.  
  
## <a name="remarks"></a>Notes  
 L’option /DEF passe un fichier de définition de module (.def) à l’éditeur de liens. Un seul fichier .def peut être spécifié au lien. Pour plus d’informations sur les fichiers .def, consultez [les fichiers de définition de Module](../../build/reference/module-definition-dot-def-files.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le **l’éditeur de liens** dossier.  
  
3.  Cliquez sur le **entrée** page de propriétés.  
  
4.  Modifier la **fichier de définition de Module** propriété.  
  
 Pour spécifier un fichier .def dans l’environnement de développement, vous devez ajouter au projet, ainsi que d’autres fichiers et puis spécifiez le fichier à l’option /DEF.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ModuleDefinitionFile%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)
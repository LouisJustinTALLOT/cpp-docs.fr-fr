---
title: -STUB (nom du fichier Stub MS-DOS) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /stub
- VC.Project.VCLinkerTool.DosStub
dev_langs:
- C++
helpviewer_keywords:
- Win32 [C++], attaching MS-DOS stub program
- STUB linker option
- MS-DOS stub file name linker option
- /STUB linker option
- Windows API [C++], attaching MS-DOS stub program
- -STUB linker option
ms.assetid: 65221ffe-4f9a-4a14-ac69-3cfb79b40b5f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4302040f7d18dcffc07ddd054c34b62c22e400d2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379014"
---
# <a name="stub-ms-dos-stub-file-name"></a>/STUB (Nom du fichier stub MS-DOS)
```  
/STUB:filename  
```  
  
## <a name="remarks"></a>Notes  
 où :  
  
 *filename*  
 Une application MS-DOS.  
  
## <a name="remarks"></a>Notes  
 L’option /STUB attache un programme stub MS-DOS à un programme Win32.  
  
 Un programme stub est appelé si le fichier est exécuté sous MS-DOS. Il affiche généralement un message approprié. Toutefois, toute application MS-DOS valide peut être un programme stub.  
  
 Spécifiez un *nom de fichier* pour le programme stub après le signe deux-points ( :) sur la ligne de commande. Les vérifications de l’éditeur de liens *nom de fichier* et émet un message d’erreur si le fichier n’est pas un fichier exécutable. Le programme doit être un fichier .exe ; un fichier .com n’est pas valide pour un programme stub.  
  
 Si cette option n’est pas utilisée, l’éditeur de liens attache un programme stub par défaut qui émet le message suivant :  
  
```  
This program cannot be run in MS-DOS mode.  
```  
  
 Lors de la génération d’un pilote de périphérique virtuel, *nom de fichier* permet à l’utilisateur de spécifier un nom de fichier qui contient une structure IMAGE_DOS_HEADER (définie dans WINNT. (H) à utiliser dans le VXD, plutôt que dans l’en-tête par défaut.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le **l’éditeur de liens** dossier.  
  
3.  Cliquez sur la page de propriétés **Ligne de commande** .  
  
4.  Tapez l’option dans le **des Options supplémentaires** boîte.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)
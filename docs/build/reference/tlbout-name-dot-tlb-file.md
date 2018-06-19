---
title: -TLBOUT (nom. Fichier TLB) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.TypeLibraryFile
- /tlbout
dev_langs:
- C++
helpviewer_keywords:
- tlb files, renaming
- TLBOUT linker option
- /TLBOUT linker option
- .tlb files, renaming
- -TLBOUT linker option
ms.assetid: 0df6d078-2e48-46c9-a1a5-02674d85dce8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1cc4103c387fe7a3dae68b642c10e326b361c54a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376850"
---
# <a name="tlbout-name-tlb-file"></a>/TLBOUT (Nommer le fichier .TLB)
```  
/TLBOUT:[path\]filename  
```  
  
## <a name="remarks"></a>Notes  
 où :  
  
 *path*  
 Une spécification de chemin d’accès absolu ou relatif pour où le fichier .tlb doit être créé.  
  
 *filename*  
 Spécifie le nom du fichier .tlb créé par le compilateur MIDL. Aucune extension de fichier n’est supposée ; Spécifiez *nom de fichier*.tlb si vous souhaitez une extension .tlb.  
  
## <a name="remarks"></a>Notes  
 L’option /TLBOUT Spécifie le nom et l’extension du fichier .tlb.  
  
 Le compilateur MIDL est appelé par l’éditeur de liens Visual C++ lors de la liaison des projets qui ont le [module](../../windows/module-cpp.md) attribut.  
  
 Si /TLBOUT n’est pas spécifié, le fichier .tlb obtiendra son nom de [/IDLOUT](../../build/reference/idlout-name-midl-output-files.md) *nom de fichier*. Si /IDLOUT n’est pas spécifié, le fichier .tlb s’appellera vc70.tlb.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le **l’éditeur de liens** dossier.  
  
3.  Cliquez sur le **IDL incorporé** page de propriétés.  
  
4.  Modifier la **bibliothèque de types** propriété.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
1.  Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryFile%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)   
 [/IGNOREIDL (ne pas traiter les attributs dans MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [/MIDL (spécifier les Options de ligne de commande MIDL)](../../build/reference/midl-specify-midl-command-line-options.md)   
 [Générer un programmes par attributs](../../windows/building-an-attributed-program.md)
---
title: -/IDLOUT (nommer les fichiers de sortie MIDL) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /idlout
- VC.Project.VCLinkerTool.MergedIDLBaseFileName
dev_langs:
- C++
helpviewer_keywords:
- MIDL, output file names
- .idl files, path
- MIDL
- /IDLOUT linker option
- IDL files, path
- -IDLOUT linker option
- IDLOUT linker option
ms.assetid: 10d00a6a-85b4-4de1-8732-e422c6931509
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d7eeb7af3d19a57b6948f867df87b8d04d0397b0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376060"
---
# <a name="idlout-name-midl-output-files"></a>/IDLOUT (Nommer les fichiers de sortie MIDL)
```  
/IDLOUT:[path\]filename  
```  
  
## <a name="parameters"></a>Paramètres  
 *path*  
 Une spécification de chemin d’accès absolu ou relatif. En spécifiant un chemin d’accès, vous affectez uniquement l’emplacement d’un fichier .idl ; tous les autres fichiers sont placés dans le répertoire du projet.  
  
 *filename*  
 Spécifie le nom du fichier .idl créé par le compilateur MIDL. Aucune extension de fichier n’est supposée ; Spécifiez *nom de fichier*.idl si vous souhaitez une extension .idl.  
  
## <a name="remarks"></a>Notes  
 L’option /IDLOUT spécifie le nom et l’extension du fichier .idl.  
  
 Le compilateur MIDL est appelé par l’éditeur de liens Visual C++ lors de la liaison des projets qui ont le [module](../../windows/module-cpp.md) attribut.  
  
 L’option /IDLOUT spécifie également les noms de fichiers des autres fichiers de sortie associés au compilateur MIDL :  
  
-   *nom de fichier*.tlb  
  
-   *nom de fichier*_p.c  
  
-   *nom de fichier*_i.c  
  
-   *nom de fichier*.h  
  
 *nom de fichier* est le paramètre que vous passez à /IDLOUT. Si [/TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md) est spécifié, le fichier .tlb obtiendra son nom de /TLBOUT *nom de fichier*.  
  
 Si vous spécifiiez /TLBOUT, l’éditeur de liens crée vc70.tlb, vc70.idl, vc70_p.c, vc70_i.c et vc70.h.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le **l’éditeur de liens** dossier.  
  
3.  Cliquez sur le **IDL incorporé** page de propriétés.  
  
4.  Modifier la **nom de fichier de Base IDL fusionné** propriété.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergedIDLBaseFileName%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)   
 [/IGNOREIDL (ne pas traiter les attributs dans MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [/MIDL (spécifier les Options de ligne de commande MIDL)](../../build/reference/midl-specify-midl-command-line-options.md)   
 [Générer un programmes par attributs](../../windows/building-an-attributed-program.md)
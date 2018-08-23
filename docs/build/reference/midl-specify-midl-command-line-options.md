---
title: -MIDL (spécifier les Options de ligne de commande MIDL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /midl
- VC.Project.VCLinkerTool.MidlCommandFile
dev_langs:
- C++
helpviewer_keywords:
- -MIDL linker option
- MIDL
- /MIDL linker option
- MIDL linker option
- MIDL, command line options
ms.assetid: 22dc259e-b34c-4ed3-a380-4beb734482c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b3f20fddd657d1e5e57caf65ecc8e2c52afbf12
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2018
ms.locfileid: "42571948"
---
# <a name="midl-specify-midl-command-line-options"></a>/MIDL (Spécification d'options de ligne de commande MIDL)
```  
/MIDL:@file  
```  
  
## <a name="remarks"></a>Notes  
 où :  
  
 `file`  
 Le nom du fichier qui contient [options de ligne de commande MIDL](http://msdn.microsoft.com/library/windows/desktop/aa366839).  
  
## <a name="remarks"></a>Notes  
 Toutes les options pour la conversion d’un fichier IDL dans un fichier TLB doivent être indiquées dans `file`; Options de ligne de commande MIDL ne peut pas être spécifiées sur la ligne de commande de l’éditeur de liens. Si /MIDL n’est pas spécifié, le compilateur MIDL sera appelé avec uniquement le nom de fichier IDL et aucune autre option.  
  
 Le fichier doit contenir une option de ligne de commande MIDL par ligne.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le **l’éditeur de liens** dossier.  
  
3.  Cliquez sur le **IDL incorporé** page de propriétés.  
  
4.  Modifier le **commandes MIDL** propriété.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)   
 [/IDLOUT (nommer les fichiers de sortie MIDL)](../../build/reference/idlout-name-midl-output-files.md)   
 [/IGNOREIDL (ne pas traiter les attributs dans MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [/TLBOUT (nommer. Fichier TLB)](../../build/reference/tlbout-name-dot-tlb-file.md)   
 [Générer un programmes par attributs](../../windows/building-an-attributed-program.md)
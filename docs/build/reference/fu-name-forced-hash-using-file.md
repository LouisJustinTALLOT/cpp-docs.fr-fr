---
title: '-FU (nom forcé #using fichier) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.ForcedUsingFiles
- /FU
- VC.Project.VCNMakeTool.ForcedUsingAssemblies
dev_langs:
- C++
helpviewer_keywords:
- -FU compiler option [C++]
- FU compiler option [C++]
- /FU compiler option [C++]
ms.assetid: 698f8603-457f-435a-baff-5ac9243d6ca1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c9a27d8c689b198bde47047969d38cf14b41c46
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375673"
---
# <a name="fu-name-forced-using-file"></a>/FU (Nom du fichier #using imposé)
Une option du compilateur que vous pouvez utiliser comme alternative au passage d’un nom de fichier à [#using, Directive](../../preprocessor/hash-using-directive-cpp.md) dans le code source.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/FU file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Spécifie le fichier de métadonnées à référencer dans cette compilation.  
  
## <a name="remarks"></a>Notes  
 Le commutateur /FU prend simplement un nom de fichier. Pour spécifier plusieurs fichiers, utilisez /FU à chacun d’eux.  
  
 Si vous utilisez [!INCLUDE[cppcli](../../build/reference/includes/cppcli_md.md)] et font référence à des métadonnées à utiliser le [Friend Assemblies](../../dotnet/friend-assemblies-cpp.md) fonctionnalité, vous ne pouvez pas utiliser **/FU**. Vous devez référencer les métadonnées dans le code à l’aide de `#using`: avec la `[as friend]` attribut. Assemblys friend ne sont pas pris en charge dans [!INCLUDE[cppwrt](../../build/reference/includes/cppwrt_md.md)] ([!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)]).  
  
 Pour plus d’informations sur la création d’un assembly ou un module pour le common language runtime (CLR), consultez [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md). Pour plus d’informations sur la génération [!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)], consultez [génération d’applications et bibliothèques](../../cppcx/building-apps-and-libraries-c-cx.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Sélectionnez le **C/C++** dossier.  
  
3.  Sélectionnez le **avancé** page de propriétés.  
  
4.  Modifier la **Force #using** propriété.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedUsingFiles%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichier de sortie (/ F) Options](../../build/reference/output-file-f-options.md)   
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)
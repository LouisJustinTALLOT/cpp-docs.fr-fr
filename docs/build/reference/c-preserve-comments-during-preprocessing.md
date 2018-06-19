---
title: -C (conserver les commentaires pendant le prétraitement) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.KeepComments
- /c
- VC.Project.VCCLWCECompilerTool.KeepComments
dev_langs:
- C++
helpviewer_keywords:
- comments, not stripping during preprocessing
- preserve comments during preprocessing
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 944567ca-16bc-4728-befe-d414a7787f26
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 350addc63807a338eb451c14e52340ef67998f18
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371253"
---
# <a name="c-preserve-comments-during-preprocessing"></a>/C (Conserver les commentaires pendant le prétraitement)
Conserve les commentaires pendant le prétraitement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/C  
```  
  
## <a name="remarks"></a>Notes  
 Cette option du compilateur requiert le **/E**, **/P**, ou **/EP** option.  
  
 L’exemple de code suivant affiche le commentaire de code source.  
  
```  
// C_compiler_option.cpp  
// compile with: /E /C /c  
int i;   // a variable  
```  
  
 Cet exemple génère la sortie suivante.  
  
```  
#line 1 "C_compiler_option.cpp"  
int i;   // a variable  
```  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le dossier **C/C++** .  
  
3.  Cliquez sur le **préprocesseur** page de propriétés.  
  
4.  Modifier la **Commentaires conservés** propriété.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.KeepComments%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des Options du compilateur](../../build/reference/setting-compiler-options.md)   
 [/E (Prétraiter dans stdout)](../../build/reference/e-preprocess-to-stdout.md)   
 [/P (Prétraiter jusqu'à un fichier)](../../build/reference/p-preprocess-to-a-file.md)   
 [/EP (Prétraiter dans stdout sans directive #line)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)
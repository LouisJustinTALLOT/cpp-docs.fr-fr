---
title: '-EP (Prétraiter dans stdout sans directive #line) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ep
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFileNoLines
dev_langs:
- C++
helpviewer_keywords:
- copy preprocessor output to stdout
- preprocessor output, copy to stdout
- -EP compiler option [C++]
- EP compiler option [C++]
- /EP compiler option [C++]
ms.assetid: 6ec411ae-e33d-4ef5-956e-0054635eabea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 38047fecbbd1bbaa87db3766b046efa8b446d93a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375381"
---
# <a name="ep-preprocess-to-stdout-without-line-directives"></a>/EP (Prétraiter dans stdout sans directive #line)
Prétraite des fichiers sources C et C++ et copie les fichiers prétraités vers le périphérique de sortie standard.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/EP  
```  
  
## <a name="remarks"></a>Notes  
 Dans le processus, toutes les directives du préprocesseur sont exécutées, les expansions de macros sont effectuées et commentaires sont supprimés. Pour conserver les commentaires dans la sortie prétraitée, utilisez le [/C (conserver les commentaires lors du prétraitement)](../../build/reference/c-preserve-comments-during-preprocessing.md) option avec **/EP**.  
  
 Le **/EP** option supprime la compilation. Vous devez renvoyer le fichier prétraité pour la compilation. **/EP** supprime également les fichiers de sortie à partir de la **/FA**, **/Fa**, et **/Fm** options. Pour plus d’informations, consultez [/FA, /Fa (Listing File)](../../build/reference/fa-fa-listing-file.md) et [/Fm (nom de fichier de mappage)](../../build/reference/fm-name-mapfile.md).  
  
 Erreurs générées pendant les phases ultérieures du traitement désignent les numéros de ligne du fichier prétraité plutôt que le fichier source d’origine. Si vous souhaitez que les numéros de ligne pour faire référence au fichier source d’origine, utilisez [/E (Prétraiter dans stdout)](../../build/reference/e-preprocess-to-stdout.md) à la place. Le **/E** option ajoute `#line` directives pour la sortie à cet effet.  
  
 Pour envoyer la sortie prétraitée, avec `#line` directives, vers un fichier, utilisent le [/P (Prétraiter dans un fichier)](../../build/reference/p-preprocess-to-a-file.md) option à la place.  
  
 Pour envoyer la sortie prétraitée dans stdout, avec `#line` directives, utilisez **/P** et **/EP** ensemble.  
  
 Vous ne pouvez pas utiliser des en-têtes précompilés avec le **/EP** option.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le dossier **C/C++** .  
  
3.  Cliquez sur le **préprocesseur** page de propriétés.  
  
4.  Modifier la **génération du fichier prétraité** propriété.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.  
  
## <a name="example"></a>Exemple  
 La ligne de commande suivante prétraite le fichier `ADD.C`, conserve les commentaires et affiche le résultat sur le périphérique de sortie standard :  
  
```  
CL /EP /C ADD.C  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)
---
title: -P (Prétraiter jusqu'à un fichier) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFile
- /p
- VC.Project.VCCLWCECompilerTool.GeneratePreprocessedFile
dev_langs:
- C++
helpviewer_keywords:
- /P compiler option [C++]
- -P compiler option [C++]
- P compiler option [C++]
- output files, preprocessor
- preprocessing output files
ms.assetid: 123ee54f-8219-4a6f-9876-4227023d83fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 26e9d2d63c7244990a047749f15273b45229c7bd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377142"
---
# <a name="p-preprocess-to-a-file"></a>/P (Prétraiter jusqu'à un fichier)
Prétraite des fichiers sources C et C++ et écrit la sortie prétraitée dans un fichier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/P  
```  
  
## <a name="remarks"></a>Notes  
 Le fichier a le même nom que le fichier source et une extension .i. Dans le processus, toutes les directives du préprocesseur sont exécutées, les expansions de macros sont effectuées et commentaires sont supprimés. Pour conserver les commentaires dans la sortie prétraitée, utilisez le [/C (conserver les commentaires lors du prétraitement)](../../build/reference/c-preserve-comments-during-preprocessing.md) option avec **/P**.  
  
 **/P** ajoute `#line` directives pour la sortie, au début et à la fin de chaque fichier inclus et autour des lignes supprimées par les directives de préprocesseur pour une compilation conditionnelle. Ces directives renumérotent les lignes du fichier prétraité. Par conséquent, erreurs générées pendant les phases ultérieures du traitement désignent les numéros de ligne du fichier source d’origine plutôt que les lignes du fichier prétraité. Pour supprimer la génération de `#line` directives, utilisez [/EP (Prétraiter dans stdout sans directive #line)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) ainsi que **/P**.  
  
 Le **/P** option supprime la compilation. Elle ne produit pas un fichier .obj, même si vous utilisez [/Fo (nom de fichier objet)](../../build/reference/fo-object-file-name.md). Vous devez renvoyer le fichier prétraité pour la compilation. **/P** supprime également les fichiers de sortie à partir de la **/FA**, **/Fa**, et **/Fm** options. Pour plus d’informations, consultez [/FA, /Fa (Listing File)](../../build/reference/fa-fa-listing-file.md) et [/Fm (nom de fichier de mappage)](../../build/reference/fm-name-mapfile.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le dossier **C/C++** .  
  
3.  Cliquez sur le **préprocesseur** page de propriétés.  
  
4.  Modifier la **génération du fichier prétraité** propriété.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.  
  
## <a name="example"></a>Exemple  
 La ligne de commande suivante prétraite `ADD.C`, conserve les commentaires, ajoute `#line` directives et écrit le résultat dans un fichier, `ADD.I`:  
  
```  
CL /P /C ADD.C  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des Options du compilateur](../../build/reference/setting-compiler-options.md)   
 [/Fi (Prétraiter le nom du fichier de sortie)](../../build/reference/fi-preprocess-output-file-name.md)
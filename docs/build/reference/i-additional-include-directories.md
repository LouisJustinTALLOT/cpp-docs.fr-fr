---
title: -I (autres répertoires Include) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AdditionalIncludeDirectories
- VC.Project.VCCLCompilerTool.AdditionalIncludeDirectories
- /I
- VC.Project.VCNMakeTool.IncludeSearchPath
dev_langs:
- C++
helpviewer_keywords:
- /I compiler option [C++]
- Additional Include Directories compiler option
- I compiler option [C++]
- -I compiler option [C++]
- set include directories
- include directories, compiler option [C++]
ms.assetid: 3e9add2a-5ed8-4d15-ad79-5b411e313a49
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 435714d72eeabe74f0cd85509d74dff5d541b019
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373125"
---
# <a name="i-additional-include-directories"></a>/I (Autres répertoires Include)
Ajoute un répertoire à la liste des répertoires de recherche des fichiers include.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/I[ ]directory  
```  
  
## <a name="arguments"></a>Arguments  
 `directory`  
 Le répertoire à ajouter à la liste des répertoires de recherche des fichiers include.  
  
## <a name="remarks"></a>Notes  
 Pour ajouter plusieurs répertoires, utilisez cette option plusieurs fois. Répertoires de recherche sont effectuées uniquement jusqu'à ce que le fichier include spécifié se trouve.  
  
 Vous pouvez utiliser cette option avec l’ignorer ([/X (ignorer Standard chemins d’accès Include)](../../build/reference/x-ignore-standard-include-paths.md)) option.  
  
 Le compilateur recherche des répertoires dans l’ordre suivant :  
  
1.  Répertoires contenant le fichier source.  
  
2.  Les répertoires spécifiés avec le **/I** option, dans l’ordre où CL les trouve.  
  
3.  Les répertoires spécifiés dans le **INCLUDE** variable d’environnement.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le dossier **C/C++** .  
  
3.  Cliquez sur le **général** page de propriétés.  
  
4.  Modifier la **autres répertoires Include** propriété.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalIncludeDirectories%2A>.  
  
## <a name="example"></a>Exemple  
 La commande suivante recherche les fichiers include demandés par MAIN.c dans l’ordre suivant : premier dans le répertoire contenant MAIN.c, puis dans le répertoire \INCLUDE, puis, dans le répertoire \MY\INCLUDE et enfin, dans les répertoires attribué à inclure variable d’environnement.  
  
```  
CL /I \INCLUDE /I\MY\INCLUDE MAIN.C  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)
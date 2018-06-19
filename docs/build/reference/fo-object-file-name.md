---
title: -Fo (nom de fichier objet) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Fo
- VC.Project.VCCLCompilerTool.ObjectFile
- VC.Project.VCCLWCECompilerTool.ObjectFile
dev_langs:
- C++
helpviewer_keywords:
- Fo compiler option [C++]
- object files, naming
- /Fo compiler option [C++]
- -Fo compiler option [C++]
ms.assetid: 0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ea552b149270b8e644140a4dd51f220648ef376e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374006"
---
# <a name="fo-object-file-name"></a>/Fo (Nom de fichier objet)
Spécifie un nom de fichier objet (.obj) ou un répertoire à utiliser à la place de la valeur par défaut.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Fopathname  
```  
  
## <a name="remarks"></a>Notes  
 Si vous n’utilisez pas cette option, le fichier objet utilise le nom de base du fichier source et l’extension .obj. Vous pouvez utiliser n’importe quel nom et l’extension que vous souhaitez, mais la convention recommandée consiste à utiliser. obj.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le dossier **C/C++** .  
  
3.  Cliquez sur la page de propriétés des **Fichiers de sortie** .  
  
4.  Modifier la **nom de fichier objet** propriété.  Dans l’environnement de développement, le fichier objet doit avoir une extension. obj.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ObjectFile%2A>.  
  
## <a name="example"></a>Exemple  
 La ligne de commande suivante crée un fichier objet nommé THIS.obj dans un répertoire existant, \OBJECT, sur le lecteur B.  
  
```  
CL /FoB:\OBJECT\ THIS.C  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fichier de sortie (/ F) Options](../../build/reference/output-file-f-options.md)   
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des Options du compilateur](../../build/reference/setting-compiler-options.md)   
 [Spécification du nom de chemin](../../build/reference/specifying-the-pathname.md)
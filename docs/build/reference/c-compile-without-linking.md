---
title: -c (compiler sans liaison) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /c
dev_langs:
- C++
helpviewer_keywords:
- suppress link
- cl.exe compiler, compiling without linking
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 8017fc3d-e5dd-4668-a1f7-3120daa95d20
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 86bd1ddcb6d44cfa433d4119f90eb02695089aa4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32370434"
---
# <a name="c-compile-without-linking"></a>/c (Compiler sans liaison)
Empêche l’appel automatique à LINK.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/c  
```  
  
## <a name="remarks"></a>Notes  
 La compilation avec **/c** crée des fichiers .obj uniquement. Vous devez appeler explicitement des lien avec les fichiers appropriés et les options permettant d’effectuer la phase de liaison de la build.  
  
 Tout projet interne créé dans l’environnement de développement utilise les **/c** option par défaut.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
-   Cette option n’est pas disponible dans l’environnement de développement.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Pour définir cette option du compilateur par programmation, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileOnly%2A>.  
  
## <a name="example"></a>Exemple  
 La ligne de commande suivante crée les fichiers objets FIRST.obj et SECOND.obj. THIRD.obj est ignoré.  
  
```  
CL /c FIRST.C SECOND.C THIRD.OBJ  
```  
  
 Pour créer un fichier exécutable, vous devez appeler LINK :  
  
```  
LINK firsti.obj second.obj third.obj /OUT:filename.exe  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)
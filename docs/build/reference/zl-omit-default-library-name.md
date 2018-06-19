---
title: -Zl (omettre le nom de la bibliothèque par défaut) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /zi
- VC.Project.VCCLCompilerTool.OmitDefaultLibName
dev_langs:
- C++
helpviewer_keywords:
- -Zl compiler option [C++]
- ZI compiler option
- Omit Default Library Name compiler option
- /Zl compiler option [C++]
- default libraries, omitting names
ms.assetid: b27d39d0-44d6-498c-84ae-27c1326fee59
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c14a3217334c2c43bac7fbcce8b0bfd60a609d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379716"
---
# <a name="zl-omit-default-library-name"></a>/Zl (Omettre le nom de la bibliothèque par défaut)
Omet le nom de bibliothèque runtime C par défaut à partir du fichier .obj. Par défaut, le compilateur place le nom de la bibliothèque dans le fichier .obj afin de diriger l’éditeur de liens vers la bibliothèque appropriée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Zl  
```  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur la bibliothèque par défaut, consultez [utiliser la bibliothèque Runtime](../../build/reference/md-mt-ld-use-run-time-library.md).  
  
 Vous pouvez utiliser **/Zl** pour compiler les fichiers .obj que vous envisagez de placer dans une bibliothèque. Bien que l’omission du nom de la bibliothèque enregistre uniquement une petite quantité d’espace pour un seul fichier .obj, l’espace total enregistré est significatif dans une bibliothèque qui contient de nombreux modules objet.  
  
 Cette option est une option avancée. Cette option supprime certaine prise en charge de bibliothèque Runtime C qui peut être requis par votre application, ce qui entraîne des erreurs au moment de la liaison si votre application dépend de cette prise en charge. Si vous utilisez cette option, vous devez fournir les composants requis d’une autre manière.  
  
 Utilisez [/NODEFAULTLIB (ignorer les bibliothèques)](../../build/reference/nodefaultlib-ignore-libraries.md). pour indiquer à l’éditeur de liens pour ignorer les références de bibliothèque dans tous les fichiers .obj.  
  
 Pour plus d’informations, consultez [Fonctionnalités de la bibliothèque CRT](../../c-runtime-library/crt-library-features.md).  
  
 Lors de la compilation avec **/Zl**, `_VC_NODEFAULTLIB` est défini.  Par exemple :  
  
```  
// vc_nodefaultlib.cpp  
// compile with: /Zl  
void Test() {  
   #ifdef _VC_NODEFAULTLIB  
      int i;  
   #endif  
  
   int i;   // C2086  
}  
```  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le dossier **C/C++** .  
  
3.  Cliquez sur le **avancé** page de propriétés.  
  
4.  Modifier la **omettre les noms de bibliothèque par défaut** propriété.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitDefaultLibName%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)
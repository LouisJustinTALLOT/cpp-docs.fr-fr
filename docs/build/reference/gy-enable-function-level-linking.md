---
title: -Gy (activer la liaison au niveau des fonctions) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFunctionLevelLinking
- /gy
- VC.Project.VCCLWCECompilerTool.EnableFunctionLevelLinking
dev_langs:
- C++
helpviewer_keywords:
- enable function-level linking compiler option [C++]
- COMDAT function
- Gy compiler option [C++]
- -Gy compiler option [C++]
- /Gy compiler option [C++]
- packaged functions
ms.assetid: 0d3cf14c-ed7d-4ad3-b4b6-104e56f61046
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36e939a12cf23a9d9e476b676a5b068889414497
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376297"
---
# <a name="gy-enable-function-level-linking"></a>/Gy (Activer la liaison au niveau des fonctions)
Permet au compilateur d’empaqueter des fonctions individuelles sous la forme de fonctions empaquetées (COMDATs).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Gy[-]  
```  
  
## <a name="remarks"></a>Notes  
 L’éditeur de liens requiert que les fonctions soient empaquetées séparément en tant que COMDAT à exclure ou de trier des fonctions individuelles dans un fichier .exe ou DLL.  
  
 Vous pouvez utiliser l’option de l’éditeur de liens [/OPT (optimisations)](../../build/reference/opt-optimizations.md) à exclure des fonctions empaquetées non référencées à partir du fichier .exe.  
  
 Vous pouvez utiliser l’option de l’éditeur de liens [/ORDER (mettre les fonctions dans l’ordre)](../../build/reference/order-put-functions-in-order.md) pour inclure des fonctions empaquetées dans un ordre spécifié dans le fichier .exe.  
  
 Les fonctions inline sont toujours empaquetées si elles sont instanciées en tant qu’appels (ce qui se produit, par exemple, si la fonctionnalité inline est désactivée ou si vous prenez une adresse de fonction). En outre, les fonctions membres C++ définies dans la déclaration de classe sont empaquetées automatiquement ; autres fonctions ne sont pas, et si cette option est requise pour les compiler en tant que fonctions empaquetées.  
  
> [!NOTE]
>  Le [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) option, utilisée pour modifier & Continuer, définit automatiquement le **/Gy** option.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le dossier **C/C++** .  
  
3.  Cliquez sur le **génération de Code** page de propriétés.  
  
4.  Modifier la **activer la liaison au niveau des fonctions** propriété.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)
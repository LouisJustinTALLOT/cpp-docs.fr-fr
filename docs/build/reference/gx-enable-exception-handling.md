---
title: -GX (activer la gestion des exceptions) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /gx
dev_langs:
- C++
helpviewer_keywords:
- exception handling, enabling
- /GX compiler option [C++]
- -GX compiler option [C++]
- cl.exe compiler, exception handling
- enable exception handling compiler option [C++]
- GX compiler option [C++]
ms.assetid: 933b43ba-de77-4ff8-a48b-7074de90bc1c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ee2d3d31a9f091e6aa3fbed39f702471047a01dd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376713"
---
# <a name="gx-enable-exception-handling"></a>/GX (Activer la gestion des exceptions)
Obsolète. Gestion synchrone des exceptions à l’aide de l’hypothèse que les fonctions déclarées à l’aide d’Active `extern "C"` lèvent jamais d’exception.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/GX  
```  
  
## <a name="remarks"></a>Notes  
 **/GX** est déconseillée. Utiliser les équivalents [/EHsc](../../build/reference/eh-exception-handling-model.md) option à la place. Pour obtenir la liste des options du compilateur déconseillées, consultez le **déconseillées et supprimées des Options du compilateur** section [Options du compilateur classées par catégorie](../../build/reference/compiler-options-listed-by-category.md).  
  
 Par défaut, **/EHsc**, l’équivalent de **/GX**, est en vigueur lorsque vous compilez à l’aide de l’environnement de développement Visual Studio. Lorsque vous utilisez les outils de ligne de commande, sans gestion des exceptions sont spécifiée. C’est l’équivalent de **/GX-**.  
  
 Pour plus d’informations, consultez [gestion des exceptions C++](../../cpp/cpp-exception-handling.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Dans le volet de navigation, choisissez **propriétés de Configuration**, **C/C++**, **ligne de commande**.  
  
3.  Tapez l'option de compilateur dans la zone **Options supplémentaires** .  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des Options du compilateur](../../build/reference/setting-compiler-options.md)   
 [/EH (Modèle de gestion des exceptions)](../../build/reference/eh-exception-handling-model.md)
---
title: -Za, - Ze (désactiver les Extensions de langage) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.DisableLanguageExtensions
- /za
- /ze
- VC.Project.VCCLCompilerTool.DisableLanguageExtensions
dev_langs:
- C++
helpviewer_keywords:
- -Za compiler option [C++]
- Za compiler option [C++]
- language extensions, disabling in compiler
- -Ze compiler option [C++]
- language extensions
- enable language extensions
- /Za compiler option [C++]
- /Ze compiler option [C++]
- Disable Language Extensions compiler option
- Ze compiler option [C++]
ms.assetid: 65e49258-7161-4289-a176-7c5c0656b1a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2949a3d60af6d9058f02d12aac1fd86dead5affa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378143"
---
# <a name="za-ze-disable-language-extensions"></a>/Za, /Ze (Désactiver les extensions de langage)
Le **/Za** option du compilateur émet une erreur pour les constructions de langage qui ne sont pas compatibles avec ANSI C89 ou ISO C ++ 11. Le **/Ze** option du compilateur, qui est activée par défaut, Active les extensions Microsoft.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Za  
/Ze  
```  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Le **/Ze** option est déconseillée, car son comportement est activé par défaut. Nous vous recommandons d’utiliser le [/Zc (conformité)](../../build/reference/zc-conformance.md) options du compilateur pour contrôler les fonctionnalités d’extension de langage spécifique. Pour obtenir la liste des options du compilateur déconseillées, consultez le **déconseillées et supprimées des Options du compilateur** section [Options du compilateur classées par catégorie](../../build/reference/compiler-options-listed-by-category.md).  
  
 Le [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] compilateur offre un certain nombre de fonctionnalités au-delà de celles spécifiées dans les normes de l’ANSI C89, ISO C99 ou ISO C++. Ces fonctionnalités sont appelées collectivement les extensions Microsoft pour C et C++. Ces extensions sont disponibles par défaut et non disponible quand le **/Za** option est spécifiée. Pour plus d’informations sur les extensions spécifiques, consultez [Extensions Microsoft pour C et C++](../../build/reference/microsoft-extensions-to-c-and-cpp.md).  
  
 Nous vous conseillons de désactiver les extensions de langage en spécifiant le **/Za** option si vous prévoyez de déplacer votre programme à d’autres environnements. Lorsque **/Za** est spécifié, le compilateur traite l’étendue des mots clés comme identificateurs simples Microsoft, désactive les autres extensions Microsoft et définit automatiquement la `__STDC__` macro prédéfinie pour les programmes C.  
  
 Autres options du compilateur utilisées avec **/Za** peut affecter la façon dont le compilateur garantit la conformité aux normes. Par exemple, **/Za** et [/fp (spécifier du comportement de nombres à virgule flottante)](../../build/reference/fp-specify-floating-point-behavior.md) peut entraîner un comportement promotion type à virgule flottante qui n’est pas conforme à la norme ISO C99 ou C ++ 11 normes.  
  
 Pour savoir comment spécifier des paramètres de comportement spécifique conformes aux standards, consultez le [/Zc](../../build/reference/zc-conformance.md) option du compilateur.  
  
 Pour plus d’informations sur les problèmes de conformité avec [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)], consultez [comportement non standard](../../cpp/nonstandard-behavior.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Dans le volet de navigation, choisissez **propriétés de Configuration**, **C/C++**, **langue**.  
  
3.  Modifier la **désactiver les Extensions de langage** propriété.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des Options du compilateur](../../build/reference/setting-compiler-options.md)   
 [/Zc (Conformité)](../../build/reference/zc-conformance.md)
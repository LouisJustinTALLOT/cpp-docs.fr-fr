---
title: -U, -u (annuler la définition de symboles) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLWCECompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLCompilerTool.UndefineAllPreprocessorDefinitions
- /u
- VC.Project.VCCLWCECompilerTool.UndefineAllPreprocessorDefinitions
dev_langs:
- C++
helpviewer_keywords:
- -U compiler option [C++]
- Undefine Symbols compiler option
- /U compiler option [C++]
- U compiler option [C++]
ms.assetid: 7bc0474f-6d1f-419b-807d-0d8816763b2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 897ca229ec7312812b6f2bd2991bf519e98c836c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378325"
---
# <a name="u-u-undefine-symbols"></a>/U, /u (Annuler la définition de symboles)
Le **/U** option du compilateur annule la définition du symbole de préprocesseur spécifié. Le **/u** option du compilateur annule les symboles spécifiques à Microsoft que le compilateur définit.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/U[ ]symbol  
/u  
```  
  
## <a name="arguments"></a>Arguments  
 `symbol`  
 Le symbole de préprocesseur pour annuler la définition.  
  
## <a name="remarks"></a>Notes  
 Ni le **/U** ou **/u** option peut annuler la définition d’un symbole créé à l’aide de la **#define** directive.  
  
 Le **/U** option peut annuler la définition d’un symbole qui a été précédemment défini à l’aide de la **/D** option.  
  
 Par défaut, le compilateur définit les symboles spécifiques à Microsoft ci-dessous.  
  
|Symbole|Fonction|  
|------------|--------------|  
|_CHAR_UNSIGNED|Type de caractère par défaut n’est pas signé. Définie lorsque le [/J](../../build/reference/j-default-char-type-is-unsigned.md) option est spécifiée.|  
|_CPPRTTI|Défini pour le code compilé avec le [/GR](../../build/reference/gr-enable-run-time-type-information.md) option.|  
|_CPPUNWIND|Défini pour le code compilé avec le [/EHsc](../../build/reference/eh-exception-handling-model.md) option.|  
|_DLL|Définie lorsque le [/MD](../../build/reference/md-mt-ld-use-run-time-library.md) option est spécifiée.|  
|_M_IX86|Par défaut, défini à 600 pour x86 cibles.|  
|_MSC_VER|Pour plus d'informations, consultez [Predefined Macros](../../preprocessor/predefined-macros.md).|  
|_WIN32|Défini pour les applications WIN32. Toujours défini.|  
|_MT|Définie lorsque le [/MD ou /MT](../../build/reference/md-mt-ld-use-run-time-library.md) option est spécifiée.|  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le dossier **C/C++** .  
  
3.  Cliquez sur le **avancé** page de propriétés.  
  
4.  Modifier la **définitions de préprocesseur** ou **annuler la définition de toutes les définitions de préprocesseur** propriétés.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefineAllPreprocessorDefinitions%2A> ou <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefinePreprocessorDefinitions%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des Options du compilateur](../../build/reference/setting-compiler-options.md)   
 [/J (caractère par défaut est de Type non signé)](../../build/reference/j-default-char-type-is-unsigned.md)   
 [/GR (activer les informations de Type au moment de l’exécution)](../../build/reference/gr-enable-run-time-type-information.md)   
 [/EH (modèle de gestion des exceptions)](../../build/reference/eh-exception-handling-model.md)   
 [/MD, /MT, /LD (Utiliser la bibliothèque Runtime)](../../build/reference/md-mt-ld-use-run-time-library.md)
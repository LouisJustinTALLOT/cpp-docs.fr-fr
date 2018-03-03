---
title: "-constexpr (évaluation de constexpr de contrôle) | Documents Microsoft"
ms.custom: 
ms.date: 08/15/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /constexpr
- -constexpr
dev_langs:
- C++
helpviewer_keywords:
- /constexpr control constexpr evaluation [C++]
- -constexpr control constexpr evaluation [C++]
- constexpr control constexpr evaluation [C++]
ms.assetid: 76d56784-f5ad-401d-841d-09d1059e8b8c
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7e594eb697c8972d28b513a3638d3eb704258b5e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="constexpr-control-constexpr-evaluation"></a>/constexpr (évaluation de constexpr de contrôle)  
  
Utilisez le **/constexpr** options du compilateur pour les paramètres de contrôle pour `constexpr` évaluation au moment de la compilation.  
  
## <a name="syntax"></a>Syntaxe  
  
> /constexpr:Depth*N*  
> /constexpr:backtrace*N*  
> / constexpr : Steps*N*  
  
## <a name="arguments"></a>Arguments  
  
**profondeur***N*  
Limiter la profondeur des récursive `constexpr` invocation de fonction *N* niveaux. La valeur par défaut est 512.  
  
**suivi de***N*  
Afficher jusqu'à *N* `constexpr` évaluations dans les diagnostics. La valeur par défaut est 10.  
  
**étapes***N*  
Terminer `constexpr` évaluation après *N* étapes. La valeur par défaut est 100 000.  
  
## <a name="remarks"></a>Notes  
  
Le **/constexpr** options du compilateur contrôlent l’évaluation de compilation de `constexpr` expressions. Les étapes d’évaluation, les niveaux de récursivité et la profondeur de suivi sont contrôlés pour empêcher que le compilateur passe trop de temps sur `constexpr` évaluation. Pour plus d’informations sur la `constexpr` l’élément de langage, consultez [constexpr (C++)](../../cpp/constexpr-cpp.md).  

Le **/constexpr** options sont disponibles à partir de Visual Studio 2015.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1. Ouvrez votre projet **Pages de propriétés** boîte de dialogue.   
  
2. Sous **propriétés de Configuration**, développez le **C/C++** dossier et choisissez le **ligne de commande** page de propriétés.  
  
3. Entrez les **/constexpr** options du compilateur dans le **des Options supplémentaires** boîte. Choisissez **OK** ou **appliquer** pour enregistrer vos modifications.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Voir aussi  
  
[Options du compilateur](../../build/reference/compiler-options.md)   
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)
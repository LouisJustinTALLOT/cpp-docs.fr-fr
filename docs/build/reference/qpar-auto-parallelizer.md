---
title: -/Qpar (PARALLÉLISEUR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableParallelCodeGeneration
dev_langs:
- C++
ms.assetid: 33ecf49d-c0d5-4f34-bce3-84ff03f38918
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 430bf1ebc79008d97435ecbcb3b15cf19dda5f8d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375686"
---
# <a name="qpar-auto-parallelizer"></a>/Qpar (paralléliseur automatique)
Permet la [PARALLÉLISEUR](../../parallel/auto-parallelization-and-auto-vectorization.md) fonctionnalité du compilateur automatiquement paralléliser les boucles dans votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Qpar  
```  
  
## <a name="remarks"></a>Notes  
 Lorsque le compilateur parallélise automatiquement des boucles de code, il répartit le calcul sur plusieurs cœurs de processeur. Une boucle est parallélisée uniquement si le compilateur détermine qu’il est permis de le faire et que la parallélisation améliorera les performances.  
  
 Le `#pragma loop()` directives sont disponibles pour aider à l’optimiseur de paralléliser les boucles spécifiques. Pour plus d’informations, consultez [boucle](../../preprocessor/loop.md).  
  
 Pour plus d’informations sur la façon d’activer les messages de sortie pour le PARALLÉLISEUR automatique, consultez [/qpar-report (niveau de Reporting PARALLÉLISEUR automatique)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md).  
  
### <a name="to-set-the-qpar-compiler-option-in-visual-studio"></a>Pour définir l’option de compilateur /Qpar dans Visual Studio  
  
1.  Dans l' **Explorateur de solutions**, ouvrez le menu contextuel du projet et choisissez **Propriétés**.  
  
2.  Dans le **Pages de propriétés** boîte de dialogue **C/C++**, sélectionnez **ligne de commande**.  
  
3.  Dans le **des Options supplémentaires** , entrez `/Qpar`.  
  
### <a name="to-set-the-qpar-compiler-option-programmatically"></a>Pour définir l’option de compilateur /Qpar par programmation  
  
-   Utilisez l'exemple de code fourni dans <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [/Q (opérations de bas niveau), options](../../build/reference/q-options-low-level-operations.md)   
 [/ Qpar-report (PARALLÉLISEUR niveau de rapport)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)   
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des Options du compilateur](../../build/reference/setting-compiler-options.md)   
 [#pragma loop()](../../preprocessor/loop.md)   
 [Programmation parallèle en Code natif](http://go.microsoft.com/fwlink/p/?linkid=263662)
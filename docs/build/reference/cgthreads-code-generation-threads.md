---
title: -cgthreads (Threads de génération de Code) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /cgthreads
dev_langs:
- C++
helpviewer_keywords:
- /cgthreads compiler option (C++)
- -cgthreads compiler option (C++)
- cgthreads compiler option (C++)
- cgthreads
ms.assetid: 64bc768c-6caa-4baf-9dea-7cfa1ffb01c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 32c88fe00958a0fc767d8a316bfe4edab7b4fb0e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372433"
---
# <a name="cgthreads-code-generation-threads"></a>/cgthreads (threads de génération de code)
Définit le nombre de threads de cl.exe à utiliser pour l'optimisation et la génération de code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/cgthreads[1-8]  
```  
  
## <a name="arguments"></a>Arguments  
 nombre  
 Nombre maximal de threads utilisables par cl.exe, dans la plage de 1 à 8.  
  
## <a name="remarks"></a>Notes  
 Le **/cgthreads** option spécifie le nombre maximal de threads que cl.exe utilise en parallèle pour l’optimisation et le code des phases de génération de la compilation. Notez qu’il ne peut y avoir aucun espace entre **/cgthreads** et `number` argument. Par défaut, cl.exe utilise quatre threads, comme si **/cgthreads4** ont été spécifiés. Si un plus grand nombre de cœurs de processeur sont disponibles, une valeur `number` plus élevée peut améliorer les durées de génération. Cette option est particulièrement utile lorsqu’il est combiné avec [/GL (optimisation de l’ensemble du programme)](../../build/reference/gl-whole-program-optimization.md).  
  
 Vous pouvez spécifier plusieurs niveaux de parallélisme pour une build. Le commutateur de msbuild.exe **/maxcpucount** Spécifie le nombre de processus MSBuild qui peuvent être exécutés en parallèle. Le [/MP (générer avec plusieurs processus)](../../build/reference/mp-build-with-multiple-processes.md) indicateur de compilateur spécifie le nombre de processus cl.exe qui compilent les fichiers sources simultanément. Le **/cgthreads** option spécifie le nombre de threads utilisés par chaque processus cl.exe. Le processeur ne pouvant pas exécuter simultanément plus de threads qu'il n'y a de cœurs de processeur, il est inutile de spécifier simultanément des valeurs plus élevées pour toutes ces options et cela peut même être contre-productif. Pour plus d’informations sur la façon de créer des projets en parallèle, consultez [génération parallèle de plusieurs projets](/visualstudio/msbuild/building-multiple-projects-in-parallel-with-msbuild).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Sélectionnez le **propriétés de Configuration**, **C/C++** dossier.  
  
3.  Sélectionnez le **ligne de commande** page de propriétés.  
  
4.  Modifier la **des Options supplémentaires** propriété à inclure **/cgthreads**`N`, où `N` est une valeur comprise entre 1 et 8, puis **OK**.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)
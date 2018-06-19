---
title: -CGTHREADS (Threads du compilateur) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- /CGTHREADS linker option
- -CGTHREADS linker option
- CGTHREADS linker option
ms.assetid: 4b52cfdb-3702-470b-9580-fabeb1417488
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5905c29170a7ad636420a9bcdbd282ccfc2e7ec3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371419"
---
# <a name="cgthreads-compiler-threads"></a>/CGTHREADS (threads du compilateur)
Définit le nombre de threads de cl.exe à utiliser pour l'optimisation et la génération de code quand la génération de code durant l'édition de liens est spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/CGTHREADS:[1-8]  
```  
  
## <a name="arguments"></a>Arguments  
 nombre  
 Nombre maximal de threads utilisables par cl.exe, dans la plage de 1 à 8.  
  
## <a name="remarks"></a>Notes  
 Le **/CGTHREADS** option spécifie le nombre maximal de threads que cl.exe utilise en parallèle pour les phases de l’optimisation et la génération de code de compilation, quand le moment de la liaison de génération de code ([LTCG](../../build/reference/ltcg-link-time-code-generation.md)) est spécifié. Par défaut, cl.exe utilise quatre threads, comme si **/CGTHREADS:4** ont été spécifiés. Si un plus grand nombre de cœurs de processeur sont disponibles, une valeur `number` plus élevée peut améliorer les durées de génération.  
  
 Vous pouvez spécifier plusieurs niveaux de parallélisme pour une build. Le commutateur de msbuild.exe **/maxcpucount** Spécifie le nombre de processus MSBuild qui peuvent être exécutés en parallèle. Le [/MP (générer avec plusieurs processus)](../../build/reference/mp-build-with-multiple-processes.md) indicateur de compilateur spécifie le nombre de processus cl.exe qui compilent les fichiers sources simultanément. Le [/cgthreads](../../build/reference/cgthreads-code-generation-threads.md) option du compilateur spécifie le nombre de threads utilisés par chaque processus cl.exe. Le processeur ne pouvant pas exécuter simultanément plus de threads qu'il n'y a de cœurs de processeur, il est inutile de spécifier simultanément des valeurs plus élevées pour toutes ces options et cela peut même être contre-productif. Pour plus d’informations sur la façon de créer des projets en parallèle, consultez [génération parallèle de plusieurs projets](/visualstudio/msbuild/building-multiple-projects-in-parallel-with-msbuild).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Sélectionnez le **propriétés de Configuration**, **l’éditeur de liens** dossier.  
  
3.  Sélectionnez le **ligne de commande** page de propriétés.  
  
4.  Modifier la **des Options supplémentaires** propriété à inclure **/CGTHREADS :**`number`, où `number` est une valeur comprise entre 1 et 8, puis choisissez **OK**.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)   
 [Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)
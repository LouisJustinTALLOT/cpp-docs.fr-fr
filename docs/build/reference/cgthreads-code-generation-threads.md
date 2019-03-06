---
title: /cgthreads (threads de génération de code)
ms.date: 11/04/2016
f1_keywords:
- /cgthreads
helpviewer_keywords:
- /cgthreads compiler option (C++)
- -cgthreads compiler option (C++)
- cgthreads compiler option (C++)
- cgthreads
ms.assetid: 64bc768c-6caa-4baf-9dea-7cfa1ffb01c2
ms.openlocfilehash: 6c3d3b51691247ddef5614cae113ffa9ded576e9
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57425235"
---
# <a name="cgthreads-code-generation-threads"></a>/cgthreads (threads de génération de code)

Définit le nombre de threads de cl.exe à utiliser pour l'optimisation et la génération de code.

## <a name="syntax"></a>Syntaxe

```
/cgthreads[1-8]
```

## <a name="arguments"></a>Arguments

*number*<br/>
Nombre maximal de threads utilisables par cl.exe, dans la plage de 1 à 8.

## <a name="remarks"></a>Notes

Le **/cgthreads** option spécifie le nombre maximal de threads cl.exe utilise en parallèle pour l’optimisation et le code des phases de génération de la compilation. Notez qu’il ne peut y avoir aucun espace entre **/cgthreads** et `number` argument. Par défaut, cl.exe utilise quatre threads, comme si **/cgthreads4** ont été spécifiés. Si un plus grand nombre de cœurs de processeur sont disponibles, une valeur `number` plus élevée peut améliorer les durées de génération. Cette option est particulièrement utile lorsqu’il est combiné avec [/GL (Whole Program Optimization)](../../build/reference/gl-whole-program-optimization.md).

Vous pouvez spécifier plusieurs niveaux de parallélisme pour une build. Le commutateur de msbuild.exe **/maxcpucount** Spécifie le nombre de processus MSBuild qui peuvent être exécutés en parallèle. Le [/MP (générer avec plusieurs processus)](../../build/reference/mp-build-with-multiple-processes.md) indicateur de compilateur spécifie le nombre de processus cl.exe qui compilent simultanément les fichiers sources. Le **/cgthreads** option spécifie le nombre de threads utilisés par chaque processus cl.exe. Le processeur ne pouvant pas exécuter simultanément plus de threads qu'il n'y a de cœurs de processeur, il est inutile de spécifier simultanément des valeurs plus élevées pour toutes ces options et cela peut même être contre-productif. Pour plus d’informations sur la façon de générer des projets en parallèle, consultez [génération parallèle de plusieurs projets](/visualstudio/msbuild/building-multiple-projects-in-parallel-with-msbuild).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration**, **C/C++** dossier.

1. Sélectionnez le **ligne de commande** page de propriétés.

1. Modifier le **des Options supplémentaires** propriété à inclure **/cgthreads**`N`, où `N` est une valeur comprise entre 1 et 8, puis sélectionnez **OK**.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)

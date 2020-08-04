---
title: /cgthreads (Threads de génération de code)
ms.date: 07/31/2020
f1_keywords:
- /cgthreads
helpviewer_keywords:
- /cgthreads compiler option (C++)
- -cgthreads compiler option (C++)
- cgthreads compiler option (C++)
- cgthreads
ms.assetid: 64bc768c-6caa-4baf-9dea-7cfa1ffb01c2
ms.openlocfilehash: 319a42ab68f02df6019ff283f1039ef3d561c4a0
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520873"
---
# <a name="cgthreads-code-generation-threads"></a>`/cgthreads`(Threads de génération de code)

Définit le nombre de threads de cl.exe à utiliser pour l'optimisation et la génération de code.

## <a name="syntax"></a>Syntaxe

> **`/cgthreads1`**\
> **`/cgthreads2`**\
> **`/cgthreads3`**\
> **`/cgthreads4`**\
> **`/cgthreads5`**\
> **`/cgthreads6`**\
> **`/cgthreads7`**\
> **`/cgthreads8`**

## <a name="arguments"></a>Arguments

**`cgthreadsN`**\
Nombre maximal de threads à utiliser pour cl.exe, où *N* est un nombre compris entre 1 et 8.

## <a name="remarks"></a>Remarques

L' **`cgthreads`** option spécifie le nombre maximal de threads cl.exe utilise en parallèle pour les phases d’optimisation et de génération de code de la compilation. Notez qu’il ne peut pas y avoir d’espace entre **`cgthreads`** et l’argument *Number* . Par défaut, cl.exe utilise quatre threads, comme si **`/cgthreads4`** a été spécifié. Si davantage de cœurs de processeur sont disponibles, une valeur *numérique* supérieure peut améliorer les temps de génération. Cette option est particulièrement utile quand elle est associée à [ `/GL` (optimisation de l’ensemble du programme)](gl-whole-program-optimization.md).

Vous pouvez spécifier plusieurs niveaux de parallélisme pour une build. Le commutateur msbuild.exe **`/maxcpucount`** spécifie le nombre de processus MSBuild qui peuvent être exécutés en parallèle. L’indicateur de compilateur [ `/MP` (générer avec plusieurs processus)](mp-build-with-multiple-processes.md) spécifie le nombre de processus de cl.exe qui compilent simultanément les fichiers sources. L' **`cgthreads`** option spécifie le nombre de threads utilisés par chaque processus de cl.exe. Le processeur ne peut exécuter qu’un nombre de threads en même temps qu’il y a de cœurs de processeur. Il n’est pas utile de spécifier des valeurs plus élevées pour toutes ces options en même temps, et cela peut être contre-productive. Pour plus d’informations sur la façon de générer des projets en parallèle, consultez [génération de plusieurs projets en parallèle](/visualstudio/msbuild/building-multiple-projects-in-parallel-with-msbuild).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >  **Command Line** .

1. Modifiez la propriété **options supplémentaires** pour inclure **`cgthreadsN`** , où *`N`* est une valeur comprise entre 1 et 8, puis sélectionnez **OK**.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)

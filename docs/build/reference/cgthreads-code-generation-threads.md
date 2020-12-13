---
description: 'En savoir plus sur : `/cgthreads` (threads de génération de code)'
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
ms.openlocfilehash: 41f1e2ab6aa9263a2faf81e83d47db953819827a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182474"
---
# <a name="cgthreads-code-generation-threads"></a>`/cgthreads` (Threads de génération de code)

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

## <a name="remarks"></a>Notes

L' **`cgthreads`** option spécifie le nombre maximal de threads cl.exe utilise en parallèle pour les phases d’optimisation et de génération de code de la compilation. Notez qu’il ne peut pas y avoir d’espace entre **`cgthreads`** et l’argument *Number* . Par défaut, cl.exe utilise quatre threads, comme si **`/cgthreads4`** a été spécifié. Si davantage de cœurs de processeur sont disponibles, une valeur *numérique* supérieure peut améliorer les temps de génération. Cette option est particulièrement utile quand elle est associée à [ `/GL` (optimisation de l’ensemble du programme)](gl-whole-program-optimization.md).

Vous pouvez spécifier plusieurs niveaux de parallélisme pour une build. Le commutateur msbuild.exe **`/maxcpucount`** spécifie le nombre de processus MSBuild qui peuvent être exécutés en parallèle. L’indicateur de compilateur [ `/MP` (générer avec plusieurs processus)](mp-build-with-multiple-processes.md) spécifie le nombre de processus de cl.exe qui compilent simultanément les fichiers sources. L' **`cgthreads`** option spécifie le nombre de threads utilisés par chaque processus de cl.exe. Le processeur ne peut exécuter qu’un nombre de threads en même temps qu’il y a de cœurs de processeur. Il n’est pas utile de spécifier des valeurs plus élevées pour toutes ces options en même temps, et cela peut être contre-productive. Pour plus d’informations sur la façon de générer des projets en parallèle, consultez [génération de plusieurs projets en parallèle](/visualstudio/msbuild/building-multiple-projects-in-parallel-with-msbuild).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >   .

1. Modifiez la propriété **options supplémentaires** pour inclure **`cgthreadsN`** , où *`N`* est une valeur comprise entre 1 et 8, puis sélectionnez **OK**.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)

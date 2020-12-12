---
description: En savoir plus sur:/CGTHREADS (threads du compilateur)
title: /CGTHREADS (threads du compilateur)
ms.date: 11/04/2016
helpviewer_keywords:
- /CGTHREADS linker option
- -CGTHREADS linker option
- CGTHREADS linker option
ms.assetid: 4b52cfdb-3702-470b-9580-fabeb1417488
ms.openlocfilehash: 71c5031c7013ec6f8ddad153d9cc16bee2004751
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179250"
---
# <a name="cgthreads-compiler-threads"></a>/CGTHREADS (threads du compilateur)

Définit le nombre de threads de cl.exe à utiliser pour l'optimisation et la génération de code quand la génération de code durant l'édition de liens est spécifiée.

## <a name="syntax"></a>Syntaxe

```
/CGTHREADS:[1-8]
```

## <a name="arguments"></a>Arguments

*number*<br/>
Nombre maximal de threads utilisables par cl.exe, dans la plage de 1 à 8.

## <a name="remarks"></a>Notes

L’option **/CGTHREADS** spécifie le nombre maximal de threads cl.exe utilise en parallèle pour les phases d’optimisation et de génération de code de la compilation lorsque la génération de code durant l’édition de liens ([/LTCG](ltcg-link-time-code-generation.md)) est spécifiée. Par défaut, cl.exe utilise quatre threads, comme si **/CGTHREADS : 4** était spécifié. Si un plus grand nombre de cœurs de processeur sont disponibles, une valeur `number` plus élevée peut améliorer les durées de génération.

Vous pouvez spécifier plusieurs niveaux de parallélisme pour une build. Le commutateur msbuild.exe **/maxcpucount** spécifie le nombre de processus MSBuild qui peuvent être exécutés en parallèle. L’indicateur de compilateur [/MP (générer avec plusieurs processus)](mp-build-with-multiple-processes.md) spécifie le nombre de processus de cl.exe qui compilent simultanément les fichiers sources. L’option du compilateur [/cgthreads](cgthreads-code-generation-threads.md) spécifie le nombre de threads utilisés par chaque processus de cl.exe. Le processeur ne pouvant pas exécuter simultanément plus de threads qu'il n'y a de cœurs de processeur, il est inutile de spécifier simultanément des valeurs plus élevées pour toutes ces options et cela peut même être contre-productif. Pour plus d’informations sur la façon de générer des projets en parallèle, consultez [génération de plusieurs projets en parallèle](/visualstudio/msbuild/building-multiple-projects-in-parallel-with-msbuild).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le dossier **Propriétés de configuration**, éditeur de **liens** .

1. Sélectionnez la page de propriétés **ligne de commande** .

1. Modifiez la propriété **options supplémentaires** pour inclure **/CGTHREADS :** `number` , où `number` est une valeur comprise entre 1 et 8, puis choisissez **OK**.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options de l’éditeur de liens MSVC](linker-options.md)<br/>
[Informations de référence sur l’éditeur de liens MSVC](linking.md)

---
title: Utilisation de Clang-Tidy dans Visual Studio
ms.date: 10/04/2019
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.clangtidy
author: frozenpandaman
ms.author: efessler
ms.openlocfilehash: 19ec35ee931822d6952512f417bbbdba14ee04b9
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77418885"
---
# <a name="using-clang-tidy-in-visual-studio"></a>Utilisation de Clang-Tidy dans Visual Studio

L’analyse du code prend en charge [Clang-Tidy](https://clang.llvm.org/extra/clang-tidy/) en mode natif pour les projets MSBuild et cmake, qu’il s’agisse d’utiliser des ensembles d’outils CLANG ou MSVC. Les contrôles Clang-Tidy peuvent s’exécuter dans le cadre de l’analyse du code en arrière-plan, comme des avertissements dans l’éditeur (tildes) et s’affichent dans la Liste d’erreurs.

Pour utiliser Clang-Tidy, le composant «C++ outils Clang pour Windows » doit être installé via le Visual Studio installer.

Clang-Tidy est l’outil d’analyse par défaut lors de l’utilisation de l’ensemble d’outils LLVM/Clang-CL, disponible à la fois dans MSBuild et CMake. Vous pouvez le configurer pour qu’il s’exécute parallèlement ou remplace l’expérience d’analyse du code standard lors de l’utilisation d’un ensemble d’outils MSVC. Si vous utilisez l’ensemble d’outils Clang-CL, l’analyse du code Microsoft ne sera pas disponible.

Clang-Tidy s’exécute après la réussite de la compilation ; vous devrez peut-être résoudre les erreurs de code source pour obtenir les résultats Clang-Tidy.

## <a name="msbuild"></a>MSBuild

Vous pouvez configurer Clang-tidy pour qu’il s’exécute dans le cadre de l’analyse du code et le générer sous la page **analyse du code** > **général** dans le fenêtre Propriétés de projet. Les options permettant de configurer l’outil se trouvent dans le sous-menu Clang-Tidy.

Pour plus d’informations, consultez [Comment : définir les propriétés d’analyse du codeC++ pour les projets C/](../code-quality/how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="cmake"></a>CMake

Dans les projets CMake, vous pouvez configurer des contrôles Clang-Tidy dans `CMakeSettings.json`. Une fois ouvert, cliquez sur « modifier JSON » dans le coin supérieur droit de l’éditeur de paramètres de projet CMake. Les clés suivantes sont reconnues :

- `enableMicrosoftCodeAnalysis`: active l’analyse du code Microsoft
- `enableClangTidyCodeAnalysis`: active l’analyse Clang-Tidy
- `clangTidyChecks`: Clang-Tidy configuration, spécifiée sous la forme d’une liste séparée par des virgules, c’est-à-dire des vérifications à activer ou à désactiver

Si aucune des options « activer » n’est spécifiée, Visual Studio sélectionne l’outil d’analyse correspondant à l’ensemble d’outils de plateforme utilisé.

## <a name="warning-display"></a>Affichage de l’avertissement

Clang-Tidy exécute les avertissements affichés dans le Liste d’erreurs et en tant que tildes dans l’éditeur sous les sections de code pertinentes. Utilisez la colonne « Category » de la Liste d’erreurs pour trier et organiser les avertissements Clang-Tidy. Vous pouvez configurer les avertissements dans l’éditeur en basculant sur le paramètre Désactiver les tildes de l’analyse du code sous **outils** > **options**.

## <a name="clang-tidy-configuration"></a>Configuration de Clang-Tidy

Vous pouvez configurer les contrôles qui sont exécutés par Clang-Tidy dans Visual Studio à l’aide de l’option **Clang-Tidy Checks** . Cette entrée est fournie à l’argument **--Checks** de l’outil. Toutes les autres configurations peuvent être incluses dans les fichiers **. Clang-Tidy** personnalisés. Pour plus d’informations, consultez la [documentation Clang-Tidy sur LLVM.org](https://clang.llvm.org/extra/clang-tidy/) .

## <a name="see-also"></a>Voir aussi

- [Prise en charge de Clang/LLVM pour les projets MSBuild](https://devblogs.microsoft.com/cppblog/clang-llvm-support-for-msbuild-projects/)
- [Prise en charge de Clang/LLVM pour les projets CMake](https://devblogs.microsoft.com/cppblog/visual-studio-cmake-support-clang-llvm-cmake-3-14-vcpkg-and-performance-improvements/)

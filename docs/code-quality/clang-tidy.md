---
title: Utilisation de Clang-Tidy dans Visual Studio
description: Comment utiliser Clang-Tidy dans Visual Studio pour l’analyse de code Microsoft C.
ms.date: 02/19/2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.clangtidy
author: frozenpandaman
ms.author: efessler
ms.openlocfilehash: ff32f522eaacee67e19aedaa1153b2c68edc98d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355152"
---
# <a name="using-clang-tidy-in-visual-studio"></a>Utilisation de Clang-Tidy dans Visual Studio

::: moniker range="<=vs-2017"

Le support pour Clang-Tidy nécessite Visual Studio 2019 version 16.4 ou plus tard. Pour voir la documentation de cette version, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end

::: moniker range=">=vs-2019"

L’analyse de code prend en charge [nativement Clang-Tidy](https://clang.llvm.org/extra/clang-tidy/) pour les projets MSBuild et CMake, que ce soit à l’aide d’outils Clang ou MSVC. Les vérifications Clang-Tidy peuvent s’exécuter dans le cadre de l’analyse du code d’arrière-plan. Ils apparaissent comme des avertissements en cours d’éditeur (squiggles), et s’affichent dans la liste d’erreurs.

Le support Clang-Tidy est disponible à partir de Visual Studio 2019 version 16.4. Il est inclus automatiquement lorsque vous choisissez une charge de travail CMD dans l’installateur visual Studio.

Clang-Tidy est l’outil d’analyse par défaut lors de l’utilisation de l’toolset LLVM/clang-cl, disponible à la fois dans MSBuild et CMake. Vous pouvez le configurer lors de l’utilisation d’un jeu d’outils MSVC pour exécuter à côté ou pour remplacer l’expérience standard d’analyse de code. Si vous utilisez l’toolset clang-cl, Microsoft Code Analysis n’est pas disponible.

Clang-Tidy fonctionne après une compilation réussie. Vous devrez peut-être résoudre des erreurs de code source pour obtenir les résultats de Clang-Tidy.

## <a name="msbuild"></a>MSBuild

Vous pouvez configurer Clang-Tidy pour exécuter dans le cadre de l’analyse de code et de construire sous la page**générale** **d’analyse** > de code dans la fenêtre Propriétés de projet. Les options pour configurer l’outil peuvent être trouvées sous le sous-marin Clang-Tidy.

Pour plus d’informations, voir [Comment : Définir les propriétés d’analyse de code pour les projets C/C.](../code-quality/how-to-set-code-analysis-properties-for-c-cpp-projects.md)

## <a name="cmake"></a>CMake

Dans les projets CMake, vous pouvez `CMakeSettings.json`configurer les contrôles Clang-Tidy à l’intérieur . Une fois ouvert, cliquez sur "Edit JSON" dans le coin supérieur droit de l’éditeur de paramètres de projet CMake. Les clés suivantes sont reconnues :

- `enableMicrosoftCodeAnalysis`: Permet l’analyse du code Microsoft
- `enableClangTidyCodeAnalysis`: Permet l’analyse Clang-Tidy
- `clangTidyChecks`: Configuration Clang-Tidy, spécifiée comme une liste séparée par virgule, c’est-à-dire les contrôles à permettre ou désactivés

Si aucune des options « actives » n’est spécifiée, Visual Studio sélectionnera l’outil d’analyse correspondant à l’outil platform Toolset utilisé.

## <a name="warning-display"></a>Affichage d’avertissement

Les courses de Clang-Tidy donnent lieu à des avertissements affichés dans la liste d’erreurs et à des gribouillis sous les sections de code pertinentes. Utilisez la colonne "Catégorie" de la Liste d’erreur pour trier et organiser les avertissements Clang-Tidy. Vous pouvez configurer les avertissements en édition en toggling le paramètre « Désabonnement d’analyse de code » sous les**options** **Outils** > .

## <a name="clang-tidy-configuration"></a>Configuration Clang-Tidy

Vous pouvez configurer les contrôles que clang-tidy exécute à l’intérieur de Visual Studio via **l’option Clang-Tidy Checks.** Cette entrée est fournie à l’argument **de l’outil.** Toute autre configuration peut *`.clang-tidy`* être incluse dans les fichiers personnalisés. Pour plus d’informations, voir la [documentation Clang-Tidy sur LLVM.org](https://clang.llvm.org/extra/clang-tidy/).

## <a name="see-also"></a>Voir aussi

- [Soutien Clang/LLVM pour les projets MSBuild](https://devblogs.microsoft.com/cppblog/clang-llvm-support-for-msbuild-projects/)
- [Soutien Clang/LLVM pour les projets CMake](https://devblogs.microsoft.com/cppblog/visual-studio-cmake-support-clang-llvm-cmake-3-14-vcpkg-and-performance-improvements/)

::: moniker-end

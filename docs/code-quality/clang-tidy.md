---
title: Utilisation de Clang-Tidy dans Visual Studio
description: Comment utiliser Clang-Tidy dans Visual Studio pour l’analyse du code Microsoft C++.
ms.date: 02/19/2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.clangtidy
ms.openlocfilehash: 5b2da222caea435bdb24d774b5e93c995e734bb7
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919070"
---
# <a name="using-clang-tidy-in-visual-studio"></a>Utilisation de Clang-Tidy dans Visual Studio

::: moniker range="<=msvc-150"

La prise en charge de Clang-Tidy nécessite Visual Studio 2019 version 16,4 ou ultérieure. Pour afficher la documentation de cette version, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end

::: moniker range=">=msvc-160"

L’analyse du code prend en charge [Clang-Tidy](https://clang.llvm.org/extra/clang-tidy/) en mode natif pour les projets MSBuild et cmake, qu’il s’agisse d’utiliser des ensembles d’outils CLANG ou MSVC. Les contrôles de Clang-Tidy peuvent s’exécuter dans le cadre de l’analyse du code en arrière-plan. Ils apparaissent en tant qu’avertissements dans l’éditeur (tildes) et s’affichent dans la Liste d’erreurs.

La prise en charge de Clang-Tidy est disponible à partir de Visual Studio 2019 version 16,4. Elle est automatiquement incluse lorsque vous choisissez une charge de travail C++ dans le Visual Studio Installer.

Clang-Tidy est l’outil d’analyse par défaut lors de l’utilisation de l’ensemble d’outils LLVM/Clang-CL, disponible à la fois dans MSBuild et CMake. Vous pouvez le configurer lors de l’utilisation d’un ensemble d’outils MSVC pour l’exécuter à côté de l’expérience d’analyse du code standard ou pour le remplacer. Si vous utilisez l’ensemble d’outils Clang-CL, l’analyse du code Microsoft n’est pas disponible.

Clang-Tidy s’exécute après la réussite de la compilation. Vous devrez peut-être résoudre les erreurs de code source pour obtenir Clang-Tidy résultats.

## <a name="msbuild"></a>MSBuild

Vous pouvez configurer Clang-Tidy pour qu’il s’exécute dans le cadre de l’analyse du code et le générer sous la page général de l' **analyse du code**  >  **General** dans le fenêtre Propriétés de projet. Les options permettant de configurer l’outil se trouvent dans le sous-menu Clang-Tidy.

Pour plus d’informations, consultez [Comment : définir les propriétés d’analyse du code pour les projets C/C++](../code-quality/how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="cmake"></a>CMake

Dans les projets CMake, vous pouvez configurer des contrôles de Clang-Tidy dans `CMakeSettings.json` . Une fois ouvert, sélectionnez « Modifier JSON » dans le coin supérieur droit de l’éditeur de paramètres de projet CMake. Les clés suivantes sont reconnues :

- `enableMicrosoftCodeAnalysis`: Active l’analyse du code Microsoft
- `enableClangTidyCodeAnalysis`: Active Clang-Tidy analyse
- `clangTidyChecks`: Clang-Tidy configuration, spécifiée sous la forme d’une liste séparée par des virgules, c’est-à-dire qu’elle vérifie l’activation ou la désactivation

Si aucune des options « activer » n’est spécifiée, Visual Studio sélectionne l’outil d’analyse correspondant à l’ensemble d’outils de plateforme utilisé.

## <a name="warning-display"></a>Affichage de l’avertissement

Clang-Tidy s’exécutent, les avertissements sont affichés dans le Liste d’erreurs, et comme tildes dans l’éditeur sous les sections de code pertinentes. Utilisez la colonne « Category » de la Liste d’erreurs pour trier et organiser les avertissements Clang-Tidy. Vous pouvez configurer les avertissements dans l’éditeur en basculant sur le paramètre Désactiver les tildes de l’analyse du code sous Options des **Outils**  >  **Options** .

## <a name="clang-tidy-configuration"></a>Configuration de Clang-Tidy

Vous pouvez configurer les contrôles qui sont exécutés par Clang-Tidy dans Visual Studio à l’aide de l’option **Clang-Tidy Checks** . Cette entrée est fournie à l' **`--checks`** argument de l’outil. Toutes les autres configurations peuvent être incluses dans des *`.clang-tidy`* fichiers personnalisés. Pour plus d’informations, consultez la [documentation Clang-Tidy sur LLVM.org](https://clang.llvm.org/extra/clang-tidy/).

## <a name="see-also"></a>Voir aussi

- [Prise en charge de Clang/LLVM pour les projets MSBuild](https://devblogs.microsoft.com/cppblog/clang-llvm-support-for-msbuild-projects/)
- [Prise en charge de Clang/LLVM pour les projets CMake](https://devblogs.microsoft.com/cppblog/visual-studio-cmake-support-clang-llvm-cmake-3-14-vcpkg-and-performance-improvements/)

::: moniker-end

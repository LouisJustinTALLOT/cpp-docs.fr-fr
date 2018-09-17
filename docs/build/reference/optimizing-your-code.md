---
title: Optimisation de votre Code | Microsoft Docs
ms.custom: ''
ms.date: 12/28/2017
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- performance, optimizing code
- optimization
- cl.exe compiler, performance
- optimization, C++ code
- code, optimizing
- performance, compiler
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 180586f55ea57100286c3c598ac62eb83107d7c9
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714374"
---
# <a name="optimizing-your-code"></a>Optimisation de votre code

En optimisant un fichier exécutable, vous pouvez obtenir un équilibre entre vitesse d’exécution et la taille de la taille du code. Cette rubrique décrit certains des mécanismes fournis par Visual C++ pour vous aider à optimiser le code.

## <a name="language-features"></a>Fonctionnalités de langage

Les rubriques suivantes décrivent certaines des fonctionnalités d’optimisation dans le langage C/C++.

[Optimisation des Pragmas et mots clés](../../build/reference/optimization-pragmas-and-keywords.md) une liste de mots clés et pragmas que vous pouvez utiliser dans votre code pour améliorer les performances.

[Options du compilateur classées par catégorie](../../build/reference/compiler-options-listed-by-category.md) une liste de **/O** options du compilateur qui affectent spécifiquement la taille de la vitesse ou code d’exécution.

[Déclarateur de rvalue référence : & &](../../cpp/rvalue-reference-declarator-amp-amp.md) Références Rvalue prennent en charge l’implémentation de *la sémantique de déplacement*. Si le déplacement de sémantique est utilisée pour implémenter des bibliothèques de modèles, les performances des applications qui utilisent ces modèles peut améliorer considérablement.

### <a name="the-optimize-pragma"></a>Le pragma optimize

Si une section de code optimisée provoque des erreurs ou un ralentissement, vous pouvez utiliser la [optimiser](../../preprocessor/optimize.md) pragma pour désactiver l’optimisation de cette section.

Placez le code entre deux pragmas, comme illustré ici :

```cpp
#pragma optimize("", off)
// some code here
#pragma optimize("", on)
```

## <a name="programming-practices"></a>Pratiques de programmation

Vous pouvez remarquer des messages d’avertissement supplémentaires lorsque vous compilez votre code avec l’optimisation. Ce comportement est normal car certains avertissements concernent uniquement au code optimisé. Vous pouvez éviter de nombreux problèmes d’optimisation si vous tenez compte de ces avertissements.

Paradoxalement, l’optimisation d’un programme pour la vitesse pourrait code à s’exécuter plus lentement. Il s’agit, car certaines optimisations de vitesse augmenter la taille du code. Par exemple, les fonctions inline élimine la surcharge des appels de fonction. Toutefois, incorporation (inlining) trop grande quantité de code peut rendre votre programme tellement important que le nombre de page de mémoire virtuelle erreurs. Par conséquent, la vitesse gagnée en supprimant les appels de fonction peut-être être perdue à l’échange de mémoire.

Les rubriques suivantes traitent des bonnes pratiques de programmation.

[Conseils pour l’amélioration de Code à durée critique](../../build/reference/tips-for-improving-time-critical-code.md) meilleures techniques de codage peuvent produire de meilleures performances. Cette rubrique suggère des techniques de codage qui peuvent vous aider à vous assurer que les parties critiques de votre code s’exécutent correctement.

[Meilleures pratiques d’optimisation](../../build/reference/optimization-best-practices.md) fournit des recommandations générales sur la meilleure façon d’optimiser votre application.

## <a name="debugging-optimized-code"></a>Débogage de code optimisé

Étant donné que l’optimisation peut modifier le code créé par le compilateur, nous vous recommandons de déboguer votre application et mesurer ses performances et optimiser votre code.

Les rubriques suivantes fournissent des informations de base sur le débogage.

- [Débogage dans Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)

- [Problèmes courants lors de la création d’une version Release](../../build/reference/common-problems-when-creating-a-release-build.md)

Les rubriques suivantes fournissent des informations plus approfondies sur le débogage.

- [Guide pratique pour déboguer le code optimisé](/visualstudio/debugger/how-to-debug-optimized-code)

- [Pourquoi les nombres à virgule flottante peuvent manquer de précision](../../build/reference/why-floating-point-numbers-may-lose-precision.md)

Les rubriques suivantes fournissent des informations sur la façon d’optimiser la création, le chargement et l’exécution de votre code.

- [Amélioration du débit du compilateur](../../build/reference/improving-compiler-throughput.md)

- [L’utilisation d’un nom de fonction sans () ne génère pas de code](../../build/reference/using-function-name-without-parens-produces-no-code.md)

- [Optimisation de l’assembly inline](../../assembler/inline/optimizing-inline-assembly.md)

- [Spécification de l’optimisation du compilateur pour un projet ATL](../../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)

- [Quelles techniques d’optimisation dois-je utiliser pour améliorer les performances de l’application cliente lors du chargement ?](../../build/dll-frequently-asked-questions.md#mfc_optimization)

## <a name="see-also"></a>Voir aussi

[Référence de la génération C/C++](../../build/reference/c-cpp-building-reference.md)

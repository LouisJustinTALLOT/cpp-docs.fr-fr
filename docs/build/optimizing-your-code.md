---
title: Optimisation du code
ms.date: 05/06/2019
helpviewer_keywords:
- performance, optimizing code
- optimization
- cl.exe compiler, performance
- optimization, C++ code
- code, optimizing
- performance, compiler
ms.openlocfilehash: 00356cf50ca8e50c80e8a1142adf654816490c9b
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078491"
---
# <a name="optimizing-your-code"></a>Optimisation du code

En optimisant un fichier exécutable, vous pouvez obtenir un équilibre entre la vitesse d’exécution rapide et la petite taille de code. Cette rubrique présente certains des mécanismes fournis par Visual Studio pour vous aider à optimiser le code.

## <a name="language-features"></a>Fonctionnalités de langage

Les rubriques suivantes décrivent quelques-unes des fonctionnalités d’optimisation du langage C/C++.

[Pragmas et Mots clés d’optimisation](optimization-pragmas-and-keywords.md) \
Liste des mots clés et des pragmas que vous pouvez utiliser dans votre code pour améliorer les performances.

[Options du compilateur classées par catégorie](reference/compiler-options-listed-by-category.md) \
Liste d’options du compilateur **/o** qui affectent spécifiquement la vitesse d’exécution ou la taille du code.

[Déclarateur de référence rvalue :  &&](../cpp/rvalue-reference-declarator-amp-amp.md) \
Les références rvalue prennent en charge l’implémentation de la *sémantique de déplacement*. Si la sémantique de déplacement est utilisée pour implémenter des bibliothèques de modèles, les performances des applications qui utilisent ces modèles peuvent être considérablement améliorées.

### <a name="the-optimize-pragma"></a>Le pragma optimize

Si une section de code optimisée génère des erreurs ou un ralentissement, vous pouvez utiliser le pragma [optimize](../preprocessor/optimize.md) pour désactiver l’optimisation de cette section.

Placez le code entre deux pragmas, comme illustré ici :

```cpp
#pragma optimize("", off)
// some code here
#pragma optimize("", on)
```

## <a name="programming-practices"></a>Pratiques de programmation

Vous pouvez remarquer des messages d’avertissement supplémentaires quand vous compilez votre code avec l’optimisation. Ce comportement est normal, car certains avertissements se rapportent uniquement au code optimisé. Vous pouvez éviter de nombreux problèmes d’optimisation si vous tenez à l’attention de ces avertissements.

Paradoxalement, l’optimisation d’un programme pour une vitesse peut entraîner un ralentissement de l’exécution du code. Cela est dû au fait que certaines optimisations pour augmenter la taille du code. Par exemple, les fonctions d’incorporation éliminent la surcharge des appels de fonction. Toutefois, l’incorporation d’un trop grand code peut rendre votre programme si volumineux que le nombre d’erreurs de page de mémoire virtuelle augmente. Par conséquent, la vitesse obtenue en éliminant les appels de fonction peut être perdue à l’échange de mémoire.

Les rubriques suivantes abordent les bonnes pratiques en matière de programmation.

[Conseils pour améliorer le code critique dans le temps](tips-for-improving-time-critical-code.md) \
De meilleures techniques de codage peuvent donner de meilleures performances. Cette rubrique suggère des techniques de codage qui peuvent vous aider à vous assurer que les parties critiques de votre code s’exécutent de manière satisfaisante.

[Meilleures pratiques pour l’optimisation](optimization-best-practices.md) \
Fournit des indications générales sur la meilleure façon d’optimiser votre application.

## <a name="debugging-optimized-code"></a>Débogage du code optimisé

Étant donné que l’optimisation peut modifier le code créé par le compilateur, nous vous recommandons de déboguer votre application et de mesurer ses performances, puis d’optimiser votre code.

Les rubriques suivantes fournissent des informations sur le débogage des versions release.

- [Débogage dans Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)

- [Comment : déboguer le code optimisé](/visualstudio/debugger/how-to-debug-optimized-code)

- [Pourquoi les nombres à virgule flottante peuvent manquer de précision](why-floating-point-numbers-may-lose-precision.md)

Les rubriques suivantes fournissent des informations sur l’optimisation de la génération, du chargement et de l’exécution de votre code.

- [Amélioration du débit du compilateur](improving-compiler-throughput.md)

- [L’utilisation d’un nom de fonction sans () ne génère pas de code](using-function-name-without-parens-produces-no-code.md)

- [Optimisation de l'assembly inline](../assembler/inline/optimizing-inline-assembly.md)

- [Spécification de l’optimisation du compilateur pour un projet ATL](../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)

- [Quelles techniques d'optimisation dois-je utiliser pour améliorer les performances de l'application cliente lors du chargement ?](../build/dll-frequently-asked-questions.md#mfc_optimization)

## <a name="in-this-section"></a>Contenu de cette section

[Pragmas et Mots clés d’optimisation](optimization-pragmas-and-keywords.md) \
[Amélioration du débit du compilateur](improving-compiler-throughput.md) \
[Pourquoi les nombres à virgule flottante peuvent perdre la précision](why-floating-point-numbers-may-lose-precision.md) \
[Représentation à virgule flottante IEEE](ieee-floating-point-representation.md) \
[Conseils pour améliorer le code critique dans le temps](tips-for-improving-time-critical-code.md) \
[L’utilisation d’un nom de fonction sans () ne génère pas de code](using-function-name-without-parens-produces-no-code.md) \
[Meilleures pratiques pour l’optimisation](optimization-best-practices.md) \
[Optimisations guidées par profil](profile-guided-optimizations.md) \
[Variables d’environnement pour les optimisations guidées par profil](environment-variables-for-profile-guided-optimizations.md) \
[PgoAutoSweep](pgoautosweep.md) \
[pgomgr](pgomgr.md) \
[pgosweep](pgosweep.md) \
[Comment : fusionner plusieurs profils PGO en un seul profil](how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)

## <a name="see-also"></a>Voir aussi

[Référence à la génération C/C++](reference/c-cpp-building-reference.md)

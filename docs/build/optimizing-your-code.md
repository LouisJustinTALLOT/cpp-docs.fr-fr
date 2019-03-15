---
title: Optimisation du code
ms.date: 12/10/2018
helpviewer_keywords:
- performance, optimizing code
- optimization
- cl.exe compiler, performance
- optimization, C++ code
- code, optimizing
- performance, compiler
ms.openlocfilehash: ae60070959c683a6365992e7b6cc510fd4111b36
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826182"
---
# <a name="optimizing-your-code"></a>Optimisation de votre code

En optimisant un fichier exécutable, vous pouvez obtenir un équilibre entre vitesse d’exécution et la taille de la taille du code. Cette rubrique décrit certains des mécanismes fournis par Visual C++ pour vous aider à optimiser le code.

## <a name="language-features"></a>Fonctionnalités de langage

Les rubriques suivantes décrivent certaines des fonctionnalités d’optimisation dans le langage C/C++.

[Pragmas et mots clés de l’optimisation](optimization-pragmas-and-keywords.md)<br/>
Une liste de mots clés et pragmas que vous pouvez utiliser dans votre code pour améliorer les performances.

[Options du compilateur classées par catégorie](reference/compiler-options-listed-by-category.md)<br/>
Une liste de **/O** options du compilateur qui affectent spécifiquement la taille de la vitesse ou code d’exécution.

[Déclarateur de référence Rvalue : &&](../cpp/rvalue-reference-declarator-amp-amp.md)<br/>
Références rvalue prennent en charge l’implémentation de *la sémantique de déplacement*. Si le déplacement de sémantique est utilisée pour implémenter des bibliothèques de modèles, les performances des applications qui utilisent ces modèles peut améliorer considérablement.

### <a name="the-optimize-pragma"></a>Le pragma optimize

Si une section de code optimisée provoque des erreurs ou un ralentissement, vous pouvez utiliser la [optimiser](../preprocessor/optimize.md) pragma pour désactiver l’optimisation de cette section.

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

[Conseils pour l’amélioration du code à durée critique](tips-for-improving-time-critical-code.md)<br/>
Meilleures techniques de codage peuvent produire de meilleures performances. Cette rubrique suggère des techniques de codage qui peuvent vous aider à vous assurer que les parties critiques de votre code s’exécutent correctement.

[Optimisation, bonnes pratiques](optimization-best-practices.md)<br/>
Fournit des recommandations générales sur la meilleure façon d’optimiser votre application.

## <a name="debugging-optimized-code"></a>Débogage de code optimisé

Étant donné que l’optimisation peut modifier le code créé par le compilateur, nous vous recommandons de déboguer votre application et mesurer ses performances et optimiser votre code.

Les rubriques suivantes fournissent plus d’informations sur le débogage de version s’appuie.

- [Débogage dans Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)

- [Guide pratique pour déboguer du code optimisé](/visualstudio/debugger/how-to-debug-optimized-code)

- [Pourquoi les nombres à virgule flottante peuvent manquer de précision](why-floating-point-numbers-may-lose-precision.md)


Les rubriques suivantes fournissent des informations sur la façon d’optimiser la création, le chargement et l’exécution de votre code.

- [Amélioration du débit du compilateur](improving-compiler-throughput.md)

- [L’utilisation d’un nom de fonction sans () ne génère pas de code](using-function-name-without-parens-produces-no-code.md)

- [Optimisation de l’assembly inline](../assembler/inline/optimizing-inline-assembly.md)

- [Spécification de l’optimisation du compilateur pour un projet ATL](../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)

- [Quelles techniques d’optimisation dois-je utiliser pour améliorer les performances de l’application cliente lors du chargement ?](../build/dll-frequently-asked-questions.md#mfc_optimization)


## <a name="in-this-section"></a>Dans cette section

[Pragmas et mots clés de l’optimisation](optimization-pragmas-and-keywords.md)<br/>
[Amélioration du débit du compilateur](improving-compiler-throughput.md)<br/>
[Pourquoi les nombres à virgule flottante peuvent manquer de précision](why-floating-point-numbers-may-lose-precision.md)<br/>
[Représentation à virgule flottante IEEE](ieee-floating-point-representation.md)<br/>
[Conseils pour l’amélioration du code à durée critique](tips-for-improving-time-critical-code.md)<br/>
[L’utilisation d’un nom de fonction sans () ne génère pas de code](using-function-name-without-parens-produces-no-code.md)<br/>
[Optimisation, bonnes pratiques](optimization-best-practices.md)<br/>
[Optimisations guidées par profil](profile-guided-optimizations.md)<br/>
[Variables d’environnement pour les optimisations guidées par profil](environment-variables-for-profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
[pgomgr](pgomgr.md)<br/>
[pgosweep](pgosweep.md)<br/>
[Guide pratique pour fusionner plusieurs profils PGO en un seul profil](how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)<br/>
[Complément PGO Visual Studio 2013 dans le hub Performances et diagnostics](profile-guided-optimization-in-the-performance-and-diagnostics-hub.md)<br/>

## <a name="see-also"></a>Voir aussi

[Référence de la génération C/C++](reference/c-cpp-building-reference.md)

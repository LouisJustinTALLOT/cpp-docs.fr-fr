---
title: Bonnes pratiques d’optimisation
ms.date: 05/06/2019
helpviewer_keywords:
- C++, optimization
- optimization, best practices
ms.assetid: f3433148-7255-4ca6-8a4f-7c31aac88508
ms.openlocfilehash: 541114b4cbf7d3d063e48b50ab265b4c95c6237c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328450"
---
# <a name="optimization-best-practices"></a>Bonnes pratiques d’optimisation

Ce document décrit quelques pratiques exemplaires pour optimiser les programmes de CMD dans Visual Studio.

## <a name="compiler-and-linker-options"></a>Options Compilateur et Linker

### <a name="profile-guided-optimization"></a>Optimisation guidée par le profil

Visual Studio prend en charge *l’optimisation guidée par profil* (PGO). Cette optimisation utilise les données de profil provenant des exécutions de formation d’une version instrumentée d’une application pour piloter l’optimisation ultérieure de l’application. L’utilisation de PGO peut prendre beaucoup de temps, de sorte qu’il peut ne pas être quelque chose que chaque développeur utilise, mais nous recommandons d’utiliser PGO pour la version finale de la construction d’un produit. Pour plus d’informations, consultez [Optimisations guidées par profil](profile-guided-optimizations.md).

En outre, *l’optimisation des programmes entiers* (aussi sait que Link Time Code Generation) et les optimisations **/O1** et **/O2** ont été améliorées. En général, une application compilée avec l’une de ces options sera plus rapide que la même application compilée avec un compilateur plus tôt.

Pour plus d’informations, voir [/GL (Optimisation du programme complet)](reference/gl-whole-program-optimization.md) et [/O1, /O2 (Minimiser la taille, maximiser la vitesse)](reference/o1-o2-minimize-size-maximize-speed.md).

### <a name="which-level-of-optimization-to-use"></a>Quel niveau d’optimisation utiliser

Si possible, les versions finales doivent être compilées avec profile Guided Optimizations. S’il n’est pas possible de construire avec PGO, que ce soit en raison d’une infrastructure insuffisante pour l’exploitation des constructions instrumentées ou de ne pas avoir accès à des scénarios, alors nous vous suggérons de construire avec l’optimisation du programme entier.

Le commutateur **/Gy** est également très utile. Il génère un COMDAT distinct pour chaque fonction, donnant au linker plus de flexibilité quand il s’agit de supprimer les COMDAT non référés et le pliage COMDAT. Le seul inconvénient à l’utilisation **/Gy,** c’est qu’il peut causer des problèmes lors de débogage. Par conséquent, il est généralement recommandé de l’utiliser. Pour plus d’informations, consultez l’article [/Gy (Activer la liaison au niveau des fonctions)](reference/gy-enable-function-level-linking.md).

Pour la liaison dans des environnements 64 bits, il est recommandé d’utiliser **l’option /OPT:REF, liaison ICF,** et dans les environnements 32 bits, **/OPT:REF** est recommandé. Pour plus d’informations, voir [/OPT (Optimisations)](reference/opt-optimizations.md).

Il est également fortement recommandé de générer des symboles de débogé, même avec des versions optimisées. Il n’affecte pas le code généré, et il est beaucoup plus facile de débog votre application, si nécessaire.

### <a name="floating-point-switches"></a>Commutateurs à points flottants

L’option de compilation **/Op** a été supprimée, et les quatre options de compilateur suivantes traitant des optimisations des points flottants ont été ajoutées :

|||
|-|-|
|**/fp:précis**|Il s’agit de la recommandation par défaut et doit être utilisé dans la plupart des cas.|
|**/fp:rapide**|Recommandé si la performance est de la plus haute importance, par exemple dans les jeux. Il en résultera la performance la plus rapide.|
|**/fp:strict**|Recommandé si des exceptions précises de point flottant et le comportement de l’IEEE est souhaité. Cela se traduira par les performances les plus lentes.|
|**/fp:sauf[-]**|Peut être utilisé en conjonction avec **/fp:strict** ou **/fp:précis**, mais pas **/fp:fast**.|

Pour plus d’informations, consultez l’article [/fp (Spécifier le comportement de virgule flottante)](reference/fp-specify-floating-point-behavior.md).

## <a name="optimization-declspecs"></a>D’optimisation declspecs

Dans cette section, nous allons examiner deux declspecs qui `__declspec(restrict)` peuvent `__declspec(noalias)`être utilisés dans les programmes pour aider à la performance: et .

La `restrict` declspec ne peut être appliquée qu’aux déclarations de fonction qui renvoient un pointeur,`__declspec(restrict) void *malloc(size_t size);`

Le `restrict` declspec est utilisé sur des fonctions qui renvoient des pointeurs non-aliased. Ce mot clé est utilisé pour la `malloc` mise en œuvre de la bibliothèque C-Runtime puisqu’il ne retournera jamais une valeur de pointeur qui est déjà utilisée dans le programme actuel (sauf si vous faites quelque chose d’illégal, comme l’utilisation de la mémoire après qu’il a été libéré).

Le `restrict` declspec donne au compilateur plus d’informations pour effectuer des optimisations compilateur. Une des choses les plus difficiles pour un compilateur à déterminer est ce pointeurs alias d’autres pointeurs, et l’utilisation de cette information aide grandement le compilateur.

Il convient de souligner qu’il s’agit d’une promesse au compilateur, pas quelque chose que le compilateur va vérifier. Si votre programme `restrict` utilise ce declspec de manière inappropriée, votre programme peut avoir un comportement incorrect.

Pour plus d’informations, voir [limitez](../cpp/restrict.md).

Le `noalias` declspec est également appliqué uniquement aux fonctions, et indique que la fonction est une fonction semi-pure. Une fonction semi-pure est celle qui ne fait référence ou modifie que les habitants, les arguments et les indirects de premier niveau des arguments. Ce declspec est une promesse pour le compilateur, et si la fonction fait référence à des globaux ou des indirections de deuxième niveau d’arguments pointeurs, alors le compilateur peut générer du code qui casse l’application.

Pour plus d’informations, consultez [noalias](../cpp/noalias.md).

## <a name="optimization-pragmas"></a>Pragmas d’optimisation

Il existe également plusieurs pragmas utiles pour aider à optimiser le code. Le premier dont nous `#pragma optimize`allons discuter est :

```cpp
#pragma optimize("{opt-list}", on | off)
```

Ce pragma vous permet de définir un niveau d’optimisation donné fonction par fonction. Ceci est idéal pour les rares occasions où votre application se bloque lorsqu’une fonction donnée est compilée avec optimisation. Vous pouvez l’utiliser pour désactiver les optimisations pour une seule fonction :

```cpp
#pragma optimize("", off)
int myFunc() {...}
#pragma optimize("", on)
```

Pour plus d’informations, voir [optimiser](../preprocessor/optimize.md).

Inlining est l’une des optimisations les plus importantes que le compilateur effectue et ici nous parlons d’un couple de pragmas qui aident à modifier ce comportement.

`#pragma inline_recursion`est utile pour spécifier si oui ou non vous voulez que l’application soit en mesure d’inlimiter un appel récursif. Par défaut, il est éteint. Pour la récursion superficielle de petites fonctions, vous pouvez l’allumer. Pour plus d’informations, voir [inline_recursion](../preprocessor/inline-recursion.md).

Un autre pragma utile pour limiter la `#pragma inline_depth`profondeur de l’inlining est . Ceci est généralement utile dans les situations où vous essayez de limiter la taille d’un programme ou d’une fonction. Pour plus d’informations, voir [inline_depth](../preprocessor/inline-depth.md).

## <a name="__restrict-and-__assume"></a>__restrict et \__assume

Il ya un couple de mots clés dans Visual Studio qui peut aider à la performance: [__restrict](../cpp/extension-restrict.md) et [__assume](../intrinsics/assume.md).

Premièrement, il convient `__restrict` `__declspec(restrict)` de noter que ce sont deux choses différentes. Bien qu’ils soient quelque peu liés, leur sémantique est différente. `__restrict`est un type `const` de `volatile`qualification, comme ou , mais exclusivement pour les types de pointeurs.

Un pointeur qui `__restrict` est modifié avec est appelé un *pointeur __restrict*. Un pointeur __restrict est un pointeur qui \_ne peut être consulté que par le pointeur _restrict. En d’autres termes, un autre pointeur ne \_peut pas être utilisé pour accéder aux données indiquées par le pointeur _restrict.

`__restrict`peut être un outil puissant pour l’optimiseur Microsoft C, mais l’utiliser avec beaucoup de soin. S’il est utilisé de manière inappropriée, l’optimiseur peut effectuer une optimisation qui casserait votre application.

Le `__restrict` mot clé remplace le commutateur **/Oa** des versions précédentes.

Avec `__assume`, un développeur peut dire au compilateur de faire des hypothèses sur la valeur d’une certaine variable.

Par `__assume(a < 5);` exemple, indique à l’optimiseur `a` qu’à cette ligne de code la variable est inférieure à 5. Encore une fois, c’est une promesse pour le compilateur. Si `a` est en fait 6 à ce stade du programme, puis le comportement du programme après le compilateur a optimisé peut ne pas être ce que vous attendez. `__assume`est le plus utile avant de changer d’instructions et/ou d’expressions conditionnelles.

Il ya quelques `__assume`limites à . Tout d’abord, comme, `__restrict`ce n’est qu’une suggestion, de sorte que le compilateur est libre de l’ignorer. En `__assume` outre, ne fonctionne actuellement qu’avec des inégalités variables contre les constantes. Il ne propage pas les inégalités symboliques, par exemple, assumer (un < b).

## <a name="intrinsic-support"></a>Soutien intrinsèque

Les intrinsèques sont des appels de fonction où le compilateur a des connaissances intrinsèques sur l’appel, et plutôt que d’appeler une fonction dans une bibliothèque, il émet du code pour cette fonction. Le fichier \<d’en-tête intrin.h> contient tous les intrinsèques disponibles pour chacune des plates-formes matérielles prises en charge.

Les intrinsèques donnent au programmeur la possibilité d’entrer profondément dans le code sans avoir à utiliser l’assemblage. L’utilisation d’intrinsèques est de plusieurs avantages :

- Votre code est plus portable. Plusieurs des intrinsèques sont disponibles sur plusieurs architectures CPU.

- Votre code est plus facile à lire, puisque le code est toujours écrit en C/CM.

- Votre code bénéficie de l’optimisation des compileurs. Au fur et à mesure que le compilateur s’améliore, la génération de code pour les intrinsèques s’améliore.

Pour plus d’informations, voir [Compiler Intrinsics](../intrinsics/compiler-intrinsics.md).

## <a name="exceptions"></a>Exceptions

Il y a un succès de performance associé à l’utilisation d’exceptions. Certaines restrictions sont introduites lors de l’utilisation de blocs d’essai qui empêchent le compilateur d’effectuer certaines optimisations. Sur les plates-formes x86, il y a une dégradation supplémentaire des performances des blocs d’essai en raison d’informations supplémentaires de l’état qui doivent être générées pendant l’exécution du code. Sur les plates-formes 64 bits, les blocs d’essai ne dégradent pas les performances autant, mais une fois qu’une exception est lancée, le processus de trouver le gestionnaire et de dénouer la pile peut être coûteux.

Par conséquent, il est recommandé d’éviter d’introduire des blocs d’essai/capture dans le code qui n’en a pas vraiment besoin. Si vous devez utiliser des exceptions, utilisez des exceptions synchrones si possible. Pour plus d'informations, consultez [Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md).

Enfin, jetez des exceptions pour des cas exceptionnels seulement. L’utilisation d’exceptions pour le flux de contrôle général fera probablement souffrir les performances.

## <a name="see-also"></a>Voir aussi

- [Optimisation du code](optimizing-your-code.md)

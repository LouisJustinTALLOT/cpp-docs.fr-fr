---
title: Meilleures pratiques d’optimisation
ms.date: 11/04/2016
helpviewer_keywords:
- Visual C++, optimization
- optimization, best practices
ms.assetid: f3433148-7255-4ca6-8a4f-7c31aac88508
ms.openlocfilehash: edb036292b87593a3f8bb9b3f5ec5f7beb84c3a5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825984"
---
# <a name="optimization-best-practices"></a>Meilleures pratiques d’optimisation

Ce document décrit certaines meilleures pratiques pour l’optimisation dans Visual C++.

## <a name="compiler-and-linker-options"></a>Options du compilateur et éditeur de liens

### <a name="profile-guided-optimization"></a>Optimisation guidée par profil

Visual C++ prend en charge *optimisation guidée par profil* (PGO). Cette optimisation utilise les données de profil à partir des exécutions de formation d’une version d’une application instrumentée pour piloter optimisation ultérieure de l’application. À l’aide de la PGO peut prendre du temps, il est donc pas quelque chose qui utilise tous les développeurs, mais nous ne recommandons pas l’utilisation de la PGO pour la génération de la version finale d’un produit. Pour plus d’informations, consultez [optimisations guidées par profil](profile-guided-optimizations.md).

En outre, *Whole Program Optimization* (également appelée génération de Code) et le **/O1** et **/O2** optimisations ont été améliorées. En règle générale, une application compilée avec l’une de ces options sera plus rapide que la même application compilée avec un compilateur antérieur.

Pour plus d’informations, consultez [/GL (Whole Program Optimization)](reference/gl-whole-program-optimization.md) et [/O1, / O2 (réduire la taille, augmenter la vitesse)](reference/o1-o2-minimize-size-maximize-speed.md).

### <a name="which-level-of-optimization-to-use"></a>Quel niveau d’optimisation à utiliser

Si possible, les builds de version finale doivent être compilés avec les optimisations guidées par profil. Si elle n’est pas possible de créer avec PGO, en raison d’une infrastructure insuffisante pour les builds instrumentées en cours d’exécution ou n’ayant ne pas accès aux scénarios, nous vous suggérons construction avec Whole Program Optimization.

Le **/Gy** commutateur est également très utile. Il génère un COMDAT distinct pour chaque fonction, ce qui donne de l’éditeur de liens davantage de flexibilité lorsqu’il s’agit de suppression de COMDAT non référencés et COMDAT pliage. Le seul inconvénient à l’utilisation de **/Gy** est que peut provoquer des problèmes lors du débogage. Par conséquent, il est généralement recommandé pour l’utiliser. Pour plus d’informations, consultez l’article [/Gy (Activer la liaison au niveau des fonctions)](reference/gy-enable-function-level-linking.md).

Pour la liaison dans les environnements 64 bits, il est recommandé d’utiliser le **/OPT : REF, ICF** option de l’éditeur de liens et dans les environnements 32 bits, **/OPT : REF** est recommandé. Pour plus d’informations, consultez [/OPT (optimisations)](reference/opt-optimizations.md).

Il est également recommandé pour générer les symboles de débogage, même avec les versions release optimisées. Cela n’affecte pas le code généré, et il rend beaucoup plus facile à déboguer votre application, si besoin d’être.

### <a name="floating-point-switches"></a>Commutateurs à virgule flottante

Le **/Op** option du compilateur a été supprimée, et les quatre options de compilateur suivantes traitant des optimisations à virgule flottante ont été ajoutées :

|||
|-|-|
|**/fp:precise**|Cela est la recommandation par défaut et doit être utilisé dans la plupart des cas.|
|**/fp:fast**|Recommandé si les performances sont d’une importance capitale, par exemple dans les jeux. Cela entraîne des performances plus rapides.|
|**/fp:strict**|Recommandée si les exceptions de virgule flottante précises et IEEE comportement est souhaité. Ainsi, les performances les plus lentes.|
|**/fp:except[-]**|Peut être utilisé conjointement avec **/fp : strict** ou **/fp : precise**, mais pas **Fast**.|

Pour plus d’informations, consultez l’article [/fp (Spécifier le comportement de virgule flottante)](reference/fp-specify-floating-point-behavior.md).

## <a name="optimization-declspecs"></a>Optimisation declspec

Dans cette section, nous allons examiner deux declspec qui peuvent être utilisés dans les programmes pour améliorer les performances : `__declspec(restrict)` et `__declspec(noalias)`.

Le `restrict` declspec peut être appliqué uniquement aux déclarations de fonction qui retournent un pointeur, comme `__declspec(restrict) void *malloc(size_t size);`

Le `restrict` declspec est utilisé sur les fonctions qui retournent des pointeurs sans alias. Ce mot clé est utilisé pour l’implémentation de la bibliothèque Runtime C de `malloc` puisqu’il ne retourne jamais une valeur de pointeur qui est déjà en cours d’utilisation dans le programme en cours (sauf si vous effectuez une opération non autorisée, par exemple à l’aide de la mémoire une fois qu’il a été libéré).

Le `restrict` declspec donne au compilateur plus d’informations pour effectuer des optimisations du compilateur. Une des opérations plus difficiles pour un compilateur à déterminer est les alias de pointeurs autres pointeurs et à l’aide de ces informations considérablement aide le compilateur.

Il est important de noter qu’il s’agit d’une promesse pour le compilateur, et non quelque chose que le compilateur vérifie. Si votre programme utilise ce `restrict` declspec inappropriée, votre programme peut avoir un comportement incorrect.

Pour plus d’informations, consultez [restreindre](../cpp/restrict.md).

Le `noalias` declspec est également appliqué uniquement aux fonctions et indique que la fonction est une fonction pure semi-structurées. Une fonction pure partiel est une référence ou modifie uniquement des variables locales, des arguments et des indirections de premier niveau d’arguments. Ce declspec est une promesse au compilateur, et si la fonction fait référence globals ou indirections de second niveau d’arguments de pointeur, le compilateur peuvent générer du code qui arrête l’application.

Pour plus d’informations, consultez [noalias](../cpp/noalias.md).

## <a name="optimization-pragmas"></a>Optimisation des pragmas

Il existe également plusieurs pragmas utiles pour optimiser le code. Le premier nous aborderons est `#pragma optimize`:

```cpp
#pragma optimize("{opt-list}", on | off)
```

Ce pragma vous permet de définir un niveau d’optimisation donné sur une base fonction par fonction. Cela est idéal pour les rares occasions où votre application se bloque quand une fonction donnée est compilée avec l’optimisation. Vous pouvez utiliser cela pour désactiver les optimisations pour une fonction unique :

```cpp
#pragma optimize("", off)
int myFunc() {...}
#pragma optimize("", on)
```

Pour plus d’informations, consultez [optimiser](../preprocessor/optimize.md).

L’incorporation est une des optimisations plus importantes que le compilateur effectue et ici nous parlons de deux des pragmas qui aident à modifier ce comportement.

`#pragma inline_recursion` est utile pour spécifier ou non que l’application soit capable d’insérer un appel récurrent. Par défaut, il est désactivé. Pour la récursivité superficielle des petites fonctions vous pouvez le pour activer. Pour plus d’informations, consultez [inline_recursion](../preprocessor/inline-recursion.md).

Un autre pragma utile pour limiter la profondeur d’incorporation (inlining) est `#pragma inline_depth`. Cela est généralement utile dans les situations où vous essayez de limiter la taille d’un programme ou une fonction. Pour plus d’informations, consultez [inline_depth](../preprocessor/inline-depth.md).

## <a name="restrict-and-assume"></a>__restrict et \__assume

Il existe deux mots clés dans Visual C++ qui peut améliorer les performances : [__restrict](../cpp/extension-restrict.md) et [__assume](../intrinsics/assume.md).

Tout d’abord, il convient de noter que `__restrict` et `__declspec(restrict)` sont deux choses différentes. Pendant qu’ils sont similaires, leur sémantique est différente. `__restrict` est un qualificateur de type, comme `const` ou `volatile`, mais exclusivement pour les types de pointeur.

Un pointeur est modifié à l’aide `__restrict` est appelé un *pointeur __restrict*. Un pointeur __restrict est un pointeur qui est accessible via la \__restrict pointeur. En d’autres termes, un autre pointeur ne peut pas être utilisé pour accéder aux données vers laquelle pointées le \__restrict pointeur.

`__restrict` peut être un outil puissant pour l’optimiseur Visual C++, mais utilisez-la avec précaution. Une utilisation incorrecte, l’optimiseur peut exécuter une optimisation qui ne fonctionneraient pas votre application.

Le `__restrict` mot clé remplace la **/Oa** basculer à partir de versions précédentes.

Avec `__assume`, un développeur peut demander au compilateur d’émettre des hypothèses sur la valeur d’une variable quelconque.

Par exemple `__assume(a < 5);` indique que l’optimiseur à cette ligne de code, la variable `a` est inférieur à 5. Il s’agit à nouveau une promesse au compilateur. Si `a` est réellement 6 à ce stade dans le programme, puis le comportement du programme une fois que le compilateur a optimisé ne peut pas être ce à quoi vous pensez. `__assume` est particulièrement utile avant les instructions switch et/ou les expressions conditionnelles.

Il existe certaines limitations à `__assume`. Tout d’abord, `__restrict`, il est uniquement une suggestion, par conséquent, le compilateur est libre pour l’ignorer. En outre, `__assume` actuellement ne fonctionne qu’avec les inégalités variables par rapport aux constantes. Il ne propage pas les inégalités symboliques, par exemple, assume(a < b).

## <a name="intrinsic-support"></a>Prise en charge intrinsèque

Fonctions intrinsèques sont fonction appelle où le compilateur a une connaissance intrinsèque de l’appel, et au lieu d’appeler une fonction dans une bibliothèque, il émet du code pour cette fonction. Le fichier d’en-tête \<intrin.h > contient tous les éléments intrinsèques disponibles pour chacune des plateformes matérielles prises en charge.

Fonctions intrinsèques permettent au programmeur à se plonger dans le code sans avoir à utiliser l’assembly. Il existe plusieurs avantages à l’utilisation des fonctions intrinsèques :

- Votre code est plus portable. Plusieurs des intrinsèques sont disponibles sur plusieurs architectures d’UC.

- Votre code est plus facile à lire, étant donné que le code est toujours écrit en C/C++.

- Votre code tire profit des optimisations du compilateur. Comme le compilateur s’améliore, la génération de code pour les fonctions intrinsèques améliore.

Pour plus d’informations, consultez [intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md).

## <a name="exceptions"></a>Exceptions

Il existe un performance positionnement associé à l’utilisation d’exceptions. Des restrictions sont appliquées lorsque vous utilisez des blocs try qui interdisent au compilateur d’effectuer certaines optimisations. Sur x86 plateformes, il existe une dégradation des performances supplémentaires à partir des blocs en raison d’informations d’état supplémentaires qui doivent être générées pendant l’exécution de code try. Sur les plateformes 64 bits, essayez de blocs n’altèrent pas autant les performances, mais une fois qu’une exception est levée, le processus de recherche du gestionnaire et le déroulement de la pile peut être coûteux.

Par conséquent, il est recommandé pour éviter d’introduire des blocs try/catch dans le code qui n’a pas vraiment besoin. Si vous devez utiliser des exceptions, utilisez si possible des exceptions synchrones. Pour plus d'informations, consultez [Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md).

Enfin, lever des exceptions pour des cas exceptionnels. Utilisation d’exceptions pour le flux de contrôle général risque de provoquer une performance en pâtir.

## <a name="see-also"></a>Voir aussi

- [Optimisation du code](optimizing-your-code.md)

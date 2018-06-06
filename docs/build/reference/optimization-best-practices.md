---
title: Meilleures pratiques de l’optimisation | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, optimization
- optimization, best practices
ms.assetid: f3433148-7255-4ca6-8a4f-7c31aac88508
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 63d3437a08e3c8b69b564176e0f377566ab491e6
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704238"
---
# <a name="optimization-best-practices"></a>Meilleures pratiques de l’optimisation

Ce document décrit quelques-unes des meilleures pratiques pour l’optimisation dans Visual C++.

## <a name="compiler-and-linker-options"></a>Options du compilateur et l’éditeur de liens

### <a name="profile-guided-optimization"></a>Optimisation guidée par profil

Visual C++ prend en charge *l’optimisation guidée par profil* (PGO). Cette optimisation utilise les données de profil à partir des exécutions de formation d’une version instrumentée d’une application pour une optimisation ultérieure de l’application. À l’aide de PGO peut prendre beaucoup de temps, il est donc pas quelque chose que chaque développeur utilise, mais nous ne recommandons pas l’utilisation de PGO pour la version Release finale d’un produit. Pour plus d’informations, consultez [optimisations guidées par profil](../../build/reference/profile-guided-optimizations.md).

En outre, *Whole Program Optimization* (également appelée génération de Code) et le **/O1** et **/O2** optimisations ont été améliorées. En règle générale, une application compilée avec une de ces options sera plus rapide que la même application compilée avec un compilateur antérieur. 

Pour plus d’informations, consultez [/GL (optimisation de l’ensemble du programme)](../../build/reference/gl-whole-program-optimization.md) et [/O1, / O2 (réduire la taille, augmenter la vitesse)](../../build/reference/o1-o2-minimize-size-maximize-speed.md).

### <a name="which-level-of-optimization-to-use"></a>Le niveau d’optimisation à utiliser

Si possible, les versions release finale doivent être compilées avec les optimisations guidées par profil. Si elle n’est pas possible de générer avec PGO, en raison d’une infrastructure insuffisante pour les builds instrumentées en cours d’exécution ou n’a ne pas accès à des scénarios, nous vous suggérons génération avec l’optimisation de programme entier.

Le **/Gy** commutateur est également très utile. Il génère un COMDAT distinct pour chaque fonction, en donnant à l’éditeur de liens davantage de souplesse en matière de suppression COMDAT non référencés et des COMDAT repli. Le seul inconvénient à l’utilisation de **/Gy** est qu’elle peut entraîner des problèmes lors du débogage. Par conséquent, il est généralement recommandé d’utiliser. Pour plus d’informations, consultez l’article [/Gy (Activer la liaison au niveau des fonctions)](../../build/reference/gy-enable-function-level-linking.md).

Pour la liaison dans les environnements 64 bits, il est recommandé d’utiliser le **/OPT : REF, ICF** option de l’éditeur de liens et dans les environnements 32 bits, **/OPT : REF** est recommandé. Pour plus d’informations, consultez [/OPT (optimisations)](../../build/reference/opt-optimizations.md).

Il est également recommandé pour générer les symboles de débogage, même avec les versions release optimisées. Cela n’affecte pas le code généré, et il rend beaucoup plus facile à déboguer votre application, si besoin est.

### <a name="floating-point-switches"></a>Commutateurs à virgule flottante

Le **/Op** option du compilateur a été supprimée, et les quatre options de compilateur suivantes vous traitez des optimisations à virgule flottante ont été ajoutées :

|||
|-|-|
|**/ fp : precise**|Cette recommandation par défaut et doit être utilisée dans la plupart des cas.|
|**Fast**|Recommandé si les performances sont d’une importance capitale, par exemple dans les jeux. Cela entraîne de meilleures performances.|
|**/ fp : strict**|Recommandée si les exceptions de virgule flottante précises et IEEE comportement est souhaité. Ainsi, les performances les plus lents.|
|**/ fp : except [-]**|Peut être utilisé conjointement avec **/fp : strict** ou **/fp : precise**, mais pas **Fast**.|

Pour plus d’informations, consultez l’article [/fp (Spécifier le comportement de virgule flottante)](../../build/reference/fp-specify-floating-point-behavior.md).

## <a name="optimization-declspecs"></a>L’optimisation declspec

Dans cette section, nous allons étudier deux declspec qui peuvent être utilisés dans les programmes pour améliorer les performances : `__declspec(restrict)` et `__declspec(noalias)`.

Le `restrict` declspec peut être appliqué uniquement aux déclarations de fonction qui retournent un pointeur, par exemple `__declspec(restrict) void *malloc(size_t size);`

Le `restrict` declspec est utilisé sur les fonctions qui retournent des pointeurs sans alias. Ce mot clé est utilisé pour l’implémentation de la bibliothèque Runtime C de `malloc` puisqu’il ne retourne jamais une valeur de pointeur qui est déjà en cours d’utilisation dans le programme en cours (sauf si vous effectuez une opération non autorisée, par exemple à l’aide de la mémoire une fois qu’il a été libéré).

Le `restrict` declspec donne au compilateur plus d’informations pour effectuer des optimisations du compilateur. Une des opérations plus difficiles pour un compilateur déterminer les alias des pointeurs autres pointeurs, et à l’aide de ces informations considérablement aide les le compilateur.

Il est important de noter qu’il s’agit d’une promesse au compilateur, pas quelque chose que le compilateur vérifie. Si votre programme utilise ce `restrict` declspec inappropriée, votre programme peut avoir un comportement incorrect.

Pour plus d’informations, consultez [restreindre](../../cpp/restrict.md).

Le `noalias` declspec est également appliqué uniquement aux fonctions et indique que la fonction est une fonction pure semi-structurées. Une fonction pure partiel est une référence ou modifie uniquement des variables locales, des arguments et des indirections de premier niveau d’arguments. Ce declspec est une promesse au compilateur, et si la fonction fait référence à des variables globales ou des indirections de deuxième niveau d’arguments de pointeur, le compilateur peuvent générer du code qui arrête l’application.

Pour plus d’informations, consultez [noalias](../../cpp/noalias.md).

## <a name="optimization-pragmas"></a>Optimisation des pragmas

Il existe également plusieurs pragmas utiles pour optimiser le code. La première nous discuterons est `#pragma optimize`:

```cpp
#pragma optimize("{opt-list}", on | off)
```

Ce pragma vous permet de définir un niveau d’optimisation donné sur une base fonction par fonction. Cette approche est idéale pour les rares occasions où votre application tombe en panne lorsqu’une fonction donnée est compilée avec l’optimisation. Cela permet de désactiver les optimisations pour une fonction unique :

```cpp
#pragma optimize("", off)
int myFunc() {...}
#pragma optimize("", on)
```

Pour plus d’informations, consultez [optimiser](../../preprocessor/optimize.md).

La fonctionnalité inline est une des plus importantes optimisations que le compilateur effectue et nous parlons ici quelques des pragmas permettant de modifier ce comportement.

`#pragma inline_recursion` est utile pour spécifier ou non que l’application doit pouvoir inline un appel récurrent. Elle est désactivée par défaut. Vous pouvez pour activer pour la récursivité superficielle de petites fonctions. Pour plus d’informations, consultez [inline_recursion](../../preprocessor/inline-recursion.md).

Un autre pragma utile pour limiter la profondeur d’incorporation (inlining) est `#pragma inline_depth`. Cela est généralement utile dans les situations où vous essayez de limiter la taille d’un programme ou une fonction. Pour plus d’informations, consultez [inline_depth](../../preprocessor/inline-depth.md).

## <a name="restrict-and-assume"></a>__restrict et \__assume

Il existe deux mots clés dans Visual C++ qui peut améliorer les performances : [__restrict](../../cpp/extension-restrict.md) et [__assume](../../intrinsics/assume.md).

Tout d’abord, il convient de noter que `__restrict` et `__declspec(restrict)` sont deux choses différentes. Pendant qu’ils sont similaires, leur sémantique est différents. `__restrict` est un qualificateur de type, comme `const` ou `volatile`, mais exclusivement pour les types pointeur.

Un pointeur est modifié avec `__restrict` est appelé un *pointeur __restrict*. Un pointeur __restrict est un pointeur qui est accessible via la \__restreindre le pointeur. En d’autres termes, un autre pointeur ne peut pas être utilisé pour accéder aux données vers laquelle pointées le \__restreindre le pointeur.

`__restrict` peut être un outil puissant pour l’optimiseur Visual C++, mais l’utiliser avec précaution. Une utilisation incorrecte, l’optimiseur peut exécuter une optimisation qui arrête votre application.

Le `__restrict` mot clé remplace la **/Oa** basculer à partir de versions précédentes.

Avec `__assume`, un développeur peut demander au compilateur d’émettre des hypothèses sur la valeur d’une variable.

Par exemple `__assume(a < 5);` indique que l’optimiseur à cette ligne de code, la variable `a` est inférieur à 5. Là encore, cela est une promesse au compilateur. Si `a` est réellement 6 à ce stade du programme, puis le comportement du programme après l’optimisation par le compilateur ne peut pas être celui que vous attendez. `__assume` est très utile avant les instructions switch et/ou les expressions conditionnelles.

Il existe certaines limitations à `__assume`. Tout d’abord, `__restrict`, il s’agit uniquement d’une suggestion, par conséquent, le compilateur est libre pour l’ignorer. En outre, `__assume` actuellement fonctionne uniquement avec les inégalités variables par rapport aux constantes. Il ne propage pas inégalités symboliques, par exemple, assume(a < b).

## <a name="intrinsic-support"></a>Prise en charge intrinsèque

Fonctions intrinsèques sont fonction appelle où le compilateur a une connaissance intrinsèque sur l’appel, et au lieu d’appeler une fonction dans une bibliothèque, il émet du code pour cette fonction. Le fichier d’en-tête \<intrin.h > contient tous les éléments intrinsèques disponibles pour chacune des plateformes matérielles prises en charge.

Fonctions intrinsèques permettent au programmeur de sonder le code sans avoir à utiliser l’assembly. Il existe plusieurs avantages à l’utilisation des fonctions intrinsèques :

- Votre code est plus portable. Plusieurs des intrinsèques sont disponibles sur plusieurs architectures d’UC.

- Votre code est plus facile à lire, car le code est toujours écrit en C/C++.

- Votre code tire profit des optimisations du compilateur. Comme le compilateur améliore, améliore la la génération de code pour les fonctions intrinsèques.

Pour plus d’informations, consultez [intrinsèques du compilateur](../../intrinsics/compiler-intrinsics.md).

## <a name="exceptions"></a>Exceptions

Il existe des performances atteint associé à l’aide des exceptions. Des restrictions sont appliquées lorsque vous utilisez des blocs try qui interdisent au compilateur d’effectuer certaines optimisations. Il existe une dégradation des performances supplémentaires à partir de plateformes try (blocs) en raison d’informations d’état supplémentaires qui doivent être générées pendant l’exécution de code sur x86. Sur les plateformes 64 bits, essayez de blocs n’altèrent pas autant les performances, mais une fois qu’une exception est levée, le processus de recherche du gestionnaire et de déroulement de la pile peut être coûteux.

Par conséquent, il est recommandé pour éviter d’introduire des blocs try/catch dans le code qui le n'a pas vraiment besoin. Si vous devez utiliser des exceptions, utilisez si possible des exceptions synchrones. Pour plus d'informations, consultez [Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md).

Enfin, lever des exceptions pour des cas exceptionnels. Utilisation d’exceptions pour le flux de contrôle général risque de provoquer une performances en souffriront.

## <a name="see-also"></a>Voir aussi

- [Optimisation du code](../../build/reference/optimizing-your-code.md)

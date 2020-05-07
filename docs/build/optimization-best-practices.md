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

Ce document décrit quelques-unes des meilleures pratiques pour l’optimisation des programmes C++ dans Visual Studio.

## <a name="compiler-and-linker-options"></a>Options du compilateur et de l’éditeur de liens

### <a name="profile-guided-optimization"></a>Optimisation guidée par profil

Visual Studio prend en charge l' *optimisation guidée par profil* (PGO). Cette optimisation utilise les données de profil des exécutions d’apprentissage d’une version instrumentée d’une application pour améliorer l’optimisation de l’application. L’utilisation de la PGO peut prendre du temps, ce qui n’est pas tout ce que chaque développeur utilise, mais nous vous recommandons d’utiliser PGO pour la version finale d’un produit. Pour plus d’informations, consultez [Optimisations guidées par profil](profile-guided-optimizations.md).

En outre, l’optimisation de l' *ensemble du programme* (également connue en tant que génération de code durant l’édition de liens) et les optimisations **/O1** et **/O2** ont été améliorées. En général, une application compilée avec l’une de ces options est plus rapide que la même application compilée avec un compilateur antérieur.

Pour plus d’informations, consultez [/GL (optimisation de l’ensemble du programme)](reference/gl-whole-program-optimization.md) et [/O1,/O2 (réduire la taille, augmenter la vitesse)](reference/o1-o2-minimize-size-maximize-speed.md).

### <a name="which-level-of-optimization-to-use"></a>Le niveau d’optimisation à utiliser

Si possible, les versions finales des versions doivent être compilées avec des optimisations guidées par profil. S’il n’est pas possible de générer avec PGO, qu’il s’agisse d’une infrastructure insuffisante pour l’exécution des builds instrumentées ou de l’absence d’accès aux scénarios, nous vous suggérons de générer l’ensemble avec l’optimisation de l’ensemble du programme.

Le commutateur **/Gy** est également très utile. Il génère un COMDAT distinct pour chaque fonction, ce qui donne à l’éditeur de liens une plus grande flexibilité lorsqu’il s’agit de supprimer les COMDAT non référencés et le repli COMDAT. Le seul inconvénient à l’utilisation de **/Gy** est qu’il peut provoquer des problèmes lors du débogage. Par conséquent, il est généralement recommandé de l’utiliser. Pour plus d’informations, consultez l’article [/Gy (Activer la liaison au niveau des fonctions)](reference/gy-enable-function-level-linking.md).

Pour la liaison dans les environnements 64 bits, il est recommandé d’utiliser l’option de l’éditeur de liens **/OPT : REF, ICF** et, dans les environnements 32 bits, **/OPT : Ref** est recommandé. Pour plus d’informations, consultez [/OPT (optimisations)](reference/opt-optimizations.md).

Il est également vivement recommandé de générer des symboles de débogage, même avec des builds de version optimisées. Il n’affecte pas le code généré, et il est beaucoup plus facile de déboguer votre application, si nécessaire.

### <a name="floating-point-switches"></a>Commutateurs à virgule flottante

L’option de compilateur **/op** a été supprimée, et les quatre options de compilateur suivantes traitant des optimisations à virgule flottante ont été ajoutées :

|||
|-|-|
|**/FP : precise**|Il s’agit de la recommandation par défaut qui doit être utilisée dans la plupart des cas.|
|**/FP : Fast**|Recommandé si les performances sont d’une importance capitale, par exemple dans les jeux. Cela entraînera des performances plus rapides.|
|**/FP : strict**|Recommandé si les exceptions de virgule flottante précises et le comportement IEEE sont souhaitées. Cela entraînera des performances plus lentes.|
|**/FP : except [-]**|Peut être utilisé conjointement avec **/FP : strict** ou **/FP : precise**, mais pas dans **/FP : Fast**.|

Pour plus d’informations, consultez l’article [/fp (Spécifier le comportement de virgule flottante)](reference/fp-specify-floating-point-behavior.md).

## <a name="optimization-declspecs"></a>Declspec d’optimisation

Dans cette section, nous allons examiner deux declspecet qui peuvent être utilisés dans les programmes pour améliorer `__declspec(restrict)` les `__declspec(noalias)`performances : et.

Le `restrict` declspec ne peut être appliqué qu’aux déclarations de fonctions qui retournent un pointeur, telles que`__declspec(restrict) void *malloc(size_t size);`

Le `restrict` declspec est utilisé sur les fonctions qui retournent des pointeurs sans alias. Ce mot clé est utilisé pour l’implémentation de la bibliothèque Runtime `malloc` C de, car il ne retourne jamais de valeur de pointeur qui est déjà utilisée dans le programme en cours (sauf si vous effectuez une opération non conforme, par exemple en utilisant la mémoire après qu’elle a été libérée).

Le `restrict` declspec donne plus d’informations au compilateur pour effectuer des optimisations du compilateur. L’un des éléments les plus difficiles pour un compilateur à déterminer est ce que les pointeurs aliasent d’autres pointeurs, et l’utilisation de ces informations aide beaucoup le compilateur.

Il convient de noter qu’il s’agit d’une promesse pour le compilateur, et non d’un aspect que le compilateur vérifiera. Si votre programme utilise ce `restrict` declspec de manière inappropriée, votre programme peut avoir un comportement incorrect.

Pour plus d’informations, consultez [restrict](../cpp/restrict.md).

Le `noalias` declspec est également appliqué uniquement aux fonctions et indique que la fonction est une fonction semi-pure. Une fonction semi-pure est une fonction qui référence ou modifie uniquement les variables locales, les arguments et les indirections de premier niveau des arguments. Ce declspec est une promesse pour le compilateur, et si la fonction fait référence à des éléments globaux ou à des indirections de second niveau d’arguments de pointeur, le compilateur peut générer du code qui interrompt l’application.

Pour plus d’informations, consultez [noalias](../cpp/noalias.md).

## <a name="optimization-pragmas"></a>Pragmas d’optimisation

Il existe également plusieurs pragmas utiles pour aider à optimiser le code. Le premier que nous allons aborder est `#pragma optimize`le suivant :

```cpp
#pragma optimize("{opt-list}", on | off)
```

Ce pragma vous permet de définir un niveau d’optimisation donné fonction par fonction. Cela est idéal pour les rares cas où votre application se bloque quand une fonction donnée est compilée avec l’optimisation. Vous pouvez l’utiliser pour désactiver les optimisations pour une seule fonction :

```cpp
#pragma optimize("", off)
int myFunc() {...}
#pragma optimize("", on)
```

Pour plus d’informations, consultez [optimize](../preprocessor/optimize.md).

L’incorporation est l’une des optimisations les plus importantes effectuées par le compilateur, et ici nous parlerons de quelques pragmas qui permettent de modifier ce comportement.

`#pragma inline_recursion`est utile pour spécifier si vous souhaitez que l’application soit en mesure d’incorporer un appel récursif. Par défaut, il est désactivé. Pour une récurrence superficielle des petites fonctions, vous pouvez activer cette fonction. Pour plus d’informations, consultez [inline_recursion](../preprocessor/inline-recursion.md).

Un autre pragma utile pour limiter la profondeur d’incorporation est `#pragma inline_depth`. Cela est généralement utile dans les situations où vous essayez de limiter la taille d’un programme ou d’une fonction. Pour plus d’informations, consultez [inline_depth](../preprocessor/inline-depth.md).

## <a name="__restrict-and-__assume"></a>__restrict et \__assume

Il existe quelques mots clés dans Visual Studio qui peuvent aider à améliorer les performances : [__restrict](../cpp/extension-restrict.md) et [__assume](../intrinsics/assume.md).

Tout d’abord, il convient de `__restrict` noter `__declspec(restrict)` que et sont deux choses différentes. Bien qu’elles soient relativement liées, leur sémantique est différente. `__restrict`est un qualificateur de type, comme `const` ou `volatile`, mais exclusivement pour les types pointeur.

Un pointeur modifié avec `__restrict` est appelé *pointeur __restrict*. Un pointeur __restrict est un pointeur qui est uniquement accessible via le \_pointeur _restrict. En d’autres termes, un autre pointeur ne peut pas être utilisé pour accéder aux données \_vers lesquelles pointe le pointeur _restrict.

`__restrict`peut être un outil puissant pour l’optimiseur Microsoft C++, mais l’utiliser avec beaucoup de soin. S’il est utilisé de manière incorrecte, l’optimiseur peut effectuer une optimisation qui interrompt votre application.

Le `__restrict` mot clé remplace le commutateur **/OA** des versions précédentes.

Avec `__assume`, un développeur peut demander au compilateur de faire des hypothèses sur la valeur d’une variable.

Par exemple `__assume(a < 5);` , indique à l’optimiseur qu’à cette ligne de code `a` la variable est inférieure à 5. Là encore, cela est une promesse pour le compilateur. Si `a` est en fait 6 à ce stade du programme, le comportement du programme après l’optimisation du compilateur peut ne pas être celui que vous attendez. `__assume`est particulièrement utile avant les instructions Switch et/ou les expressions conditionnelles.

Il existe certaines limitations à `__assume`. Tout d’abord `__restrict`, comme, il ne s’agit que d’une suggestion, le compilateur est donc libre de l’ignorer. En outre `__assume` , ne fonctionne actuellement qu’avec des inégalités de variables sur des constantes. Elle ne propage pas les inégalités symboliques, par exemple, supposons (a < b).

## <a name="intrinsic-support"></a>Prise en charge intrinsèque

Les intrinsèques sont des appels de fonction où le compilateur a des connaissances intrinsèques sur l’appel et, au lieu d’appeler une fonction dans une bibliothèque, il émet du code pour cette fonction. Le fichier \<d’en-tête Intro. h> contient toutes les fonctions intrinsèques disponibles pour chacune des plateformes matérielles prises en charge.

Les intrinsèques permettent au programmeur d’entrer en profondeur dans le code sans avoir à utiliser l’assembly. L’utilisation d’intrinsèques présente plusieurs avantages :

- Votre code est plus portable. Plusieurs des intrinsèques sont disponibles sur plusieurs architectures d’UC.

- Votre code est plus facile à lire, car le code est toujours écrit en C/C++.

- Votre code tire parti des optimisations du compilateur. À mesure que le compilateur est amélioré, la génération de code pour les fonctions intrinsèques est améliorée.

Pour plus d’informations, consultez [intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md).

## <a name="exceptions"></a>Exceptions

Une baisse des performances est associée à l’utilisation des exceptions. Certaines restrictions sont introduites lors de l’utilisation de blocs try qui empêchent le compilateur d’effectuer certaines optimisations. Sur les plateformes x86, les blocs try entraînent une dégradation des performances en raison d’informations d’État supplémentaires qui doivent être générées lors de l’exécution du code. Sur les plateformes 64 bits, les blocs try n’altèrent pas autant les performances, mais une fois qu’une exception est levée, le processus de recherche du gestionnaire et de déroulement de la pile peut être coûteux.

Par conséquent, il est recommandé d’éviter d’introduire des blocs try/catch dans du code qui n’en a pas vraiment besoin. Si vous devez utiliser des exceptions, utilisez des exceptions synchrones si possible. Pour plus d'informations, consultez [Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md).

Enfin, levez des exceptions uniquement pour des cas exceptionnels. L’utilisation d’exceptions pour le workflow de contrôle général risque d’entraîner une dégradation des performances.

## <a name="see-also"></a>Voir aussi

- [Optimisation du code](optimizing-your-code.md)

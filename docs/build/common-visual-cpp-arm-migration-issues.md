---
title: Problèmes courants de Migration ARM Visual C++ | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0f4c434e-0679-4331-ba0a-cc15dd435a46
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04253b5d71de75f6a06f2934dae24df2e6d4e3e2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376232"
---
# <a name="common-visual-c-arm-migration-issues"></a>Problèmes courants de migration ARM Visual C++

Lorsque vous utilisez Microsoft Visual C++ (MSVC), le même code source C++ peut produire des résultats différents sur l’architecture ARM qu’à sur les architectures x86 ou x64.

## <a name="sources-of-migration-issues"></a>Sources de problèmes de migration

Nombreux problèmes que vous pouvez rencontrer lorsque vous migrez le code dans les architectures x86 ou x64 à l’architecture ARM sont liées à des constructions de code source qui peuvent appeler un comportement non défini, défini par l’implémentation ou non spécifié.

*Un comportement indéfini* est un comportement qui ne définit pas de la norme C++, et qui est provoquée par une opération qui n’a aucun résultat raisonnable : par exemple, la conversion d’une valeur à virgule flottante en un entier non signé, ou le décalage d’une valeur d’un nombre de positions qui est un nombre négatif ou est supérieur au nombre de bits dans le type promu.

*Comportement défini par l’implémentation* est le comportement de la norme C++ requiert le fournisseur de compilateur définir et de document. Un programme peut compter sur le comportement défini par l’implémentation, bien que cela donc peut-être pas portable. Les tailles des types de données intégrés et leurs spécifications d’alignement sont des exemples de comportement définis par l’implémentation. Un exemple d’une opération qui peut être affectée par le comportement défini par l’implémentation est l’accès à la liste d’arguments variable.

*Comportement non spécifié* est le comportement de la norme C++ laisse délibérément non déterministe. Bien que le comportement est considérée comme non déterministes, les appels particuliers d’un comportement non spécifié sont déterminés par l’implémentation du compilateur. Toutefois, il n’est pas obligatoire pour un fournisseur de compilateur d’avance le résultat ou de garantir un comportement cohérent entre les appels sont comparables, et n’est pas obligatoire pour la documentation. Un exemple d’un comportement non spécifié est l’ordre dans lequel les sous-expressions, qui incluent des arguments d’un appel de fonction, sont évaluées.

Autres problèmes de migration peuvent être attribuées à des différences matérielles entre ARM et architectures x86 ou x64 qui interagissent avec la norme C++ différemment. Par exemple, le modèle de mémoire fort de l’architecture x86 et x64 donne `volatile`-qualifié variables des propriétés supplémentaires qui ont été utilisées pour faciliter certains types de communication entre les threads dans le passé. Mais le modèle de mémoire faible de l’architecture ARM ne prend pas en charge cette utilisation, ni la norme C++ requiert.

> [!IMPORTANT]
>  Bien que `volatile` des gains de certaines propriétés qui peuvent être utilisées pour implémenter des formes limitées de communication entre les threads sur x86 et x64, ces propriétés supplémentaires ne sont pas suffisantes pour mettre en œuvre entre les threads communication en général. La norme C++ recommande l’implémentation de cette communication à l’aide des primitives de synchronisation approprié à la place.

Étant donné que les différentes plateformes peuvent exprimer ces types de comportement différemment, portage des logiciels entre les plateformes peut être difficile et bogue susceptible d’engendrer des si elle dépend du comportement d’une plateforme spécifique. Bien que la plupart de ces types de comportement peuvent être observés et peuvent apparaître stables, leur utilisation est au moins non portable et dans les cas d’un comportement non défini ou non spécifié, est également une erreur. Même le comportement qui est mentionné dans ce document ne doit pas représenter et peut changer dans les futures compilateurs ou les implémentations de processeur.

## <a name="example-migration-issues"></a>Problèmes de migration d’exemple

Le reste de ce document décrit comment la différence de comportement de ces éléments de langage C++ peut produire des résultats différents sur différentes plateformes.

### <a name="conversion-of-floating-point-to-unsigned-integer"></a>Conversion de la virgule flottante en entier non signé

Sur l’architecture ARM, la conversion d’une valeur à virgule flottante en un entier 32 bits sature à la valeur la plus proche qui l’entier peut représenter si la valeur à virgule flottante est en dehors de la plage de l’entier peut représenter. Sur les architectures x86 et x64, la conversion revient si l’entier non signé ou a la valeur -2147483648 si l’entier est signé. Aucun de ces architectures prennent directement en charge la conversion de valeurs à virgule flottante pour les types d’entier plus petits ; au lieu de cela, les conversions sont effectuées à 32 bits, et les résultats sont tronquées à une taille plus petite.

Pour l’architecture ARM, la combinaison de saturation et de troncation signifie que la conversion en types non signés sature correctement plus petit des types non signés lorsqu’elle sature un entier 32 bits, mais produit un résultat tronqué pour les valeurs supérieures à la plus petit type peut représenter, mais il est trop petite pour saturer l’entier 32 bits. Conversion sature correctement pour les entiers signés 32 bits, mais la troncation des entiers saturées, signés entraîne -1 pour les valeurs de clairement saturés et 0 pour les valeurs négativement saturée. La conversion en un plus petit entier signé produit un résultat tronqué est imprévisible.

Pour les architectures x86 et x64, la combinaison de comportement enveloppant pour les conversions de l’entier non signé et évaluation explicite pour les conversions de l’entier signé de dépassement de capacité, ainsi que la troncation, que les résultats pour la plupart des équipes imprévisible si elles sont trop grand.

Ces plateformes diffèrent également dans la façon dont ils gèrent la conversion NaN (Not-a-Number) pour les types d’entiers. ARM, NaN convertit à 0 x 00000000 ; x86 et x64, il convertit à 0 x 80000000.

Conversion en virgule flottante peut uniquement être reposait sur si vous savez que la valeur est dans la plage du type qui est converti en entier.

### <a name="shift-operator---behavior"></a>Opérateur de décalage (\< \< >>) comportement

Sur l’architecture ARM, une valeur peut être décalée vers la gauche ou droite jusqu'à 255 bits avant que le modèle ne commence à répéter. Sur les architectures x86 et x64, le modèle est répété à chaque multiple de 32, sauf si la source du modèle est une variable 64 bits ; Dans ce cas, le modèle est répété à chaque multiple de 64 sur x 64 et chaque multiple de 256 sur x86, où une implémentation de logiciels est employée. Par exemple, pour une variable 32 bits qui a la valeur 1 décalée vers la gauche par 32 positions, sur ARM, le résultat est 0, sur x86, le résultat est 1, et sur x64 le résultat est également 1. Toutefois, si la source de la valeur est une variable 64 bits, le résultat sur les trois plateformes est 4294967296, et la valeur ne « enveloppé » jusqu'à ce qu’il a déplacé les 64 positions sur x64 ou 256 positions sur ARM et x86.

Étant donné que le résultat d’une opération de décalage qui dépasse le nombre de bits dans le type de source n’est pas défini, le compilateur n’est pas obligé de disposer d’un comportement cohérent dans toutes les situations. Par exemple, si les deux opérandes d’un décalage vers sont connues au moment de la compilation, le compilateur peut optimiser le programme à l’aide d’une routine interne à précalculer le résultat de l’équipe et de puis en remplaçant le résultat à la place de l’opération de décalage. Si le décalage est trop grand ou négatif, le résultat de la routine interne peut être différent que le résultat de la même expression MAJ exécutée par l’UC.

### <a name="variable-arguments-varargs-behavior"></a>Comportement des arguments de variable (varargs)

Sur l’architecture ARM, les paramètres à partir de la liste d’arguments de variables qui sont passés sur la pile sont soumises à l’alignement. Par exemple, un paramètre 64 bits est aligné sur une limite de 64 bits. Sur x86 et x64, les arguments sont passés sur la pile ne sont pas soumis à l’alignement et pack étroitement. Cette différence peut entraîner une fonction variadique comme `printf` pour lire les adresses de mémoire qui étaient censées remplissage sur ARM si la disposition attendue de la liste d’arguments de variables ne correspond pas exactement, même si elle peut travailler pour un sous-ensemble de valeurs de la x86 ou x64 architectures. Considérez cet exemple :

```C
// notice that a 64-bit integer is passed to the function, but '%d' is used to read it.
// on x86 and x64 this may work for small values because %d will “parse” the low-32 bits of the argument.
// on ARM the calling convention will align the 64-bit value and the code will print a random value
printf("%d\n", 1LL);
```

Dans ce cas, le bogue peut être résolu en s’assurant que la spécification de format correct est utilisée afin que l’alignement de l’argument est pris en compte. Ce code est correct :

```C
// CORRECT: use %I64d for 64-bit integers
printf("%I64d\n", 1LL);
```

### <a name="argument-evaluation-order"></a>Ordre d’évaluation des arguments

Étant donné que ARM, x 86 et x64 processeurs sont donc différents, ils peuvent présenter des exigences différentes pour les implémentations du compilateur, ainsi que les différentes possibilités pour les optimisations. Pour cette raison, ainsi que d’autres facteurs tels que les paramètres de la convention d’appel et l’optimisation, un compilateur peut évaluer les arguments de fonction dans un ordre différent sur différentes architectures ou lorsque les autres facteurs sont modifiées. Cela peut entraîner le comportement d’une application qui s’appuie sur un ordre spécifique d’évaluation pour changer de façon inattendue.

Ce type d’erreur peut se produire lorsque les arguments pour une fonction ont des effets secondaires qui a un impact sur les autres arguments de la fonction dans le même appel. Ce type de dépendance n’est généralement facile à éviter, mais il peut parfois être masqué par les dépendances qui sont difficiles à distinguer, ou par la surcharge d’opérateur. Considérez cet exemple de code :

```cpp
handle memory_handle;

memory_handle->acquire(*p);
```

Cela semble bien défini, mais si `->` et `*` sont les opérateurs surchargés, ce code est traduit en quelque chose qui ressemble à ceci :

```cpp
Handle::acquire(operator->(memory_handle), operator*(p));
```

Et s’il existe une dépendance entre `operator->(memory_handle)` et `operator*(p)`, le code peut-être faire appel à un ordre d’évaluation spécifiques, même si le code d’origine se présente comme il n’existe aucune dépendance possible.

### <a name="volatile-keyword-default-behavior"></a>comportement par défaut de mot clé volatile

Le compilateur MSVC prend en charge deux différemment de la `volatile` qualificateur de stockage que vous pouvez spécifier à l’aide des commutateurs de compilation. Le [/volatile:ms](../build/reference/volatile-volatile-keyword-interpretation.md) commutateur sélectionne Microsoft étendus sémantiques volatiles qui garantissent le classement fort, comme cela a été le cas classique pour x86 et x64 en raison du modèle en mémoire fort sur ces architectures. Le [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) commutateur sélectionne la strict standard volatile sémantique C++ qui ne garantie pas le classement fort.

Sur l’architecture ARM, la valeur par défaut est **/volatile:iso** , car les processeurs ARM ont une faiblement classés de modèle de mémoire et, car les logiciels ARM ne sont pas héritée de la partie de confiance de la sémantique d’étendue de **/volatile:ms**  et n’a généralement pas d’interface avec le logiciel qui effectue. Toutefois, il est toujours parfois commode ou même requis pour compiler un programme ARM à utiliser la sémantique d’étendue. Par exemple, il peut être trop importante porter un programme à utiliser la sémantique C++ ISO ou pilote peut-être à respecter la sémantique traditionnelle pour fonctionner correctement. Dans ce cas, vous pouvez utiliser la **/volatile:ms** commutateur ; Toutefois, pour recréer la sémantique volatile traditionnelle sur les cibles ARM, le compilateur doit insérer les barrières de mémoire autour de chaque lecture ou d’écriture une `volatile` variable à appliquer fort de classement, ce qui peut avoir un impact négatif sur les performances.

Sur les architectures x86 et x64, la valeur par défaut est **/volatile:ms** car repose en grande partie du logiciel qui a déjà été créé pour les architectures à l’aide de MSVC sur ces derniers. Lorsque vous compilez les programmes x86 et x64, vous pouvez spécifier le **/volatile:iso** commutateur afin de mieux éviter inutiles envers la sémantique volatile traditionnelle et pour promouvoir la portabilité.

## <a name="see-also"></a>Voir aussi

[Configurer Visual C++ pour les processeurs ARM](../build/configuring-programs-for-arm-processors-visual-cpp.md)  

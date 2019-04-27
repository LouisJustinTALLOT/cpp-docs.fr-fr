---
title: Problèmes courants de migration ARM Visual C++
ms.date: 11/04/2016
ms.assetid: 0f4c434e-0679-4331-ba0a-cc15dd435a46
ms.openlocfilehash: a39e1d5e26a62cafa093067bb42f33178a1af6af
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195260"
---
# <a name="common-visual-c-arm-migration-issues"></a>Problèmes courants de migration ARM Visual C++

Lorsque vous utilisez Microsoft Visual C++ (MSVC), le même code source C++ peut produire des résultats différents sur l’architecture ARM que c’est le cas sur les architectures x86 ou x64.

## <a name="sources-of-migration-issues"></a>Sources de problèmes de migration

Nombreux problèmes que vous pouvez rencontrer lorsque vous migrez des code depuis les architectures x86 ou x64 à l’architecture ARM sont liées à des constructions de code source qui peuvent appeler un comportement indéfini, défini par l’implémentation ou non spécifié.

*Un comportement indéfini* est un comportement qui ne définit pas de la norme C++, et qui est provoquée par une opération qui n’a aucun résultat raisonnable : par exemple, la conversion d’une valeur à virgule flottante en entier non signé, ou le décalage d’une valeur d’un nombre de positions qui est un nombre négatif ou dépasse le nombre de bits dans son type promu.

*Comportement défini par l’implémentation* est le comportement de la norme C++ nécessite le fournisseur de compilateur définir et de document. Un programme peut compter sur le comportement défini par l’implémentation, bien que cela donc peut-être pas portable. Exemples de comportement défini par l’implémentation incluent la taille des types de données intégrés et leurs conditions d’alignement. Un exemple d’une opération qui peut être affectée par le comportement défini par l’implémentation est l’accès à la liste d’arguments variable.

*Comportement non spécifié* est le comportement de la norme C++ laisse intentionnellement non déterministe. Bien que le comportement est considérée comme non déterministe, appels particuliers de comportement non spécifié sont déterminées par l’implémentation du compilateur. Toutefois, il n’est pas obligatoire pour un fournisseur de compilateur à déterminer au préalable le résultat ou de garantir un comportement cohérent entre les appels sont comparables, et n’est pas obligatoire pour la documentation. Un exemple de comportement non spécifié est l’ordre dans lequel les sous-expressions, qui incluent des arguments à un appel de fonction, sont évaluées.

Autres problèmes de migration peuvent être attribuées à des différences matérielles entre ARM et architectures x86 ou x64 qui interagissent avec la norme C++ différemment. Par exemple, le modèle de mémoire fort de l’architecture x86 et x64 offre `volatile`-qualifié variables des propriétés supplémentaires qui ont été utilisées pour faciliter certains types de communication entre les threads dans le passé. Mais le modèle de mémoire faible de l’architecture ARM ne prend pas en charge cette utilisation, ni la norme C++ l’impose.

> [!IMPORTANT]
>  Bien que `volatile` des gains de certaines propriétés peuvent être utilisées pour implémenter des formes limitées de communication entre les threads sur x86 et x64, ces propriétés supplémentaires ne sont pas suffisantes pour mettre en œuvre entre les threads communication en général. La norme C++ recommande l’implémentation de ce type communication au lieu de cela à l’aide des primitives de synchronisation approprié.

Étant donné que les différentes plateformes peuvent exprimer ces types de comportement différemment, portage logiciels entre plateformes peut être difficile et sujettes aux bogues si elle dépend du comportement d’une plateforme spécifique. Bien que la plupart de ces types de comportement peuvent être observés et peuvent sembler stables, leur utilisation est au moins non portable et dans les cas de comportement non défini ou non spécifié, est également une erreur. Même le comportement qui est indiquée dans ce document ne sont pas fiables sur et peut changer dans les futures implémentations de processeur ou de compilateurs.

## <a name="example-migration-issues"></a>Problèmes de migration d’exemple

Le reste de ce document décrit comment le comportement différent de ces éléments de langage C++ peut produire des résultats différents sur différentes plateformes.

### <a name="conversion-of-floating-point-to-unsigned-integer"></a>Conversion de la virgule flottante en entier non signé

Sur l’architecture ARM, la conversion d’une valeur à virgule flottante en un entier 32 bits sature à la valeur la plus proche qui l’entier peut représenter si la valeur à virgule flottante est en dehors de la plage que l’entier peut représenter. Sur les architectures x86 et x64, la conversion inclut dans un wrapper autour de si l’entier n’est pas signé ou a la valeur -2147483648 si l’entier est signé. Aucune de ces architectures prennent directement en charge la conversion de valeurs à virgule flottante en plus petits types entiers ; au lieu de cela, les conversions sont effectuées à 32 bits, et les résultats sont tronquées à une taille plus petite.

Pour l’architecture ARM, la combinaison de saturation et de troncation signifie que la conversion en types non signés correctement sature plus petits des types non signés, lorsqu’elle sature un entier 32 bits, mais produit un résultat tronqué pour les valeurs supérieures à la plus petit type peut représenter, mais il est trop petite pour saturer l’entier 32 bits. Conversion sature correctement pour les entiers signés 32 bits, mais troncation d’entiers saturés, signés entraîne -1 pour les valeurs positivement saturé et 0 pour les valeurs négativement saturée. Conversion en un entier signé plus petits génère un résultat tronqué qui est imprévisible.

Pour les architectures x86 et x64, la combinaison de comportement cumulatif pour les conversions de l’entier non signé et explicites d’évaluation pour les conversions d’entier signé de dépassement de capacité, ainsi que de troncation, vérifiez les résultats pour la plupart des équipes imprévisible si elles sont trop grand.

Ces plateformes diffèrent également dans la façon dont ils gèrent la conversion de NaN (Not a Number) pour les types d’entiers. Sur ARM, NaN convertit en 0 x 00000000 ; sur x86 et x64, il convertit en 0 x 80000000.

Conversion à virgule flottante peut uniquement être s’appuyaient sur si vous savez que la valeur est dans la plage du type converti en entier.

### <a name="shift-operator---behavior"></a>Opérateur de décalage (\< \< >>) comportement

Sur l’architecture ARM, une valeur peut être déplacée vers la gauche ou droite jusqu'à 255 bits avant que le modèle ne commence à répéter. Sur les architectures x86 et x64, le modèle est répété à chaque multiple de 32, sauf si la source du modèle est une variable 64 bits ; Dans ce cas, le modèle est répété à chaque multiple de 64 sur x 64 et chaque multiple de 256 sur x86, où une implémentation de logiciels est employée. Par exemple, pour une variable 32 bits qui a la valeur 1 décalée vers la gauche par des 32 positions, sur ARM, le résultat est 0, sur x86 le résultat est 1, et sur x64 le résultat est également 1. Toutefois, si la source de la valeur est une variable 64 bits, puis le résultat sur les trois plateformes est 4294967296, et la valeur ne « enveloppé » jusqu'à ce qu’il a déplacé les 64 positions sur x64 ou 256 positions sur ARM et x86.

Étant donné que le résultat d’une opération de décalage qui dépasse le nombre de bits dans le type de source est non défini, le compilateur n’est pas obligé d’ont un comportement cohérent dans toutes les situations. Par exemple, si les deux opérandes d’un travail d’équipe sont connus au moment de la compilation, le compilateur peut optimiser le programme en utilisant une routine interne à précalculer le résultat de la touche MAJ enfoncée et en puis en remplaçant le résultat à la place de l’opération de décalage. Si le décalage est trop grand ou négatif, le résultat de la routine interne peut être autre que le résultat de l’expression de décalage vers la même exécuté par le processeur.

### <a name="variable-arguments-varargs-behavior"></a>Comportement d’arguments variable (varargs)

Sur l’architecture ARM, les paramètres dans la liste d’arguments de variables qui sont passés sur la pile sont susceptibles d’être alignement. Par exemple, un paramètre de 64 bits est aligné sur une limite de 64 bits. Sur x86 et x64, les arguments sont passés sur la pile ne sont pas soumis à l’alignement et pack étroitement. Cette différence peut entraîner une fonction variadique comme `printf` pour lire les adresses de mémoire qui étaient censés remplissage sur ARM si la disposition de la liste d’arguments variable attendue ne correspond pas exactement, même si elle peut fonctionner pour un sous-ensemble de valeurs sur le x86 ou x64 architectures. Considérez cet exemple :

```C
// notice that a 64-bit integer is passed to the function, but '%d' is used to read it.
// on x86 and x64 this may work for small values because %d will “parse” the low-32 bits of the argument.
// on ARM the calling convention will align the 64-bit value and the code will print a random value
printf("%d\n", 1LL);
```

Dans ce cas, le bogue peut être résolu en veillant à ce que la spécification de format correct est utilisée afin que l’alignement de l’argument est considéré comme. Ce code est correct :

```C
// CORRECT: use %I64d for 64-bit integers
printf("%I64d\n", 1LL);
```

### <a name="argument-evaluation-order"></a>Ordre d’évaluation des arguments

Étant donné que ARM, x 86 et x64 processeurs sont donc que différents, ils peuvent présenter des exigences différentes pour les implémentations du compilateur, ainsi que les différentes possibilités d’optimisations. Pour cette raison, ainsi que d’autres facteurs tels que les paramètres de la convention d’appel et l’optimisation, un compilateur peut évaluer les arguments de fonction dans un ordre différent sur différentes architectures ou lorsque les autres facteurs sont modifiés. Cela peut entraîner le comportement d’une application qui s’appuie sur un ordre d’évaluation spécifiques à changer de manière inattendue.

Ce type d’erreur peut se produire lorsque les arguments d’une fonction aient des effets secondaires qui affectent les autres arguments de la fonction dans le même appel. Généralement ce type de dépendance est facile à éviter, mais il peut parfois être masqué par les dépendances qui sont difficiles à discerner ou par la surcharge d’opérateur. Considérez cet exemple de code :

```cpp
handle memory_handle;

memory_handle->acquire(*p);
```

Cela semble bien défini, mais si `->` et `*` sont les opérateurs surchargés, ce code est convertie en quelque chose qui ressemble à ceci :

```cpp
Handle::acquire(operator->(memory_handle), operator*(p));
```

Et s’il existe une dépendance entre `operator->(memory_handle)` et `operator*(p)`, le code peut s’appuyer sur un ordre d’évaluation spécifiques, même si le code d’origine se présente comme il n’existe aucune dépendance possible.

### <a name="volatile-keyword-default-behavior"></a>comportement par défaut de mot clé volatile

Le compilateur MSVC prend en charge deux différentes interprétations du `volatile` qualificateur de stockage que vous pouvez spécifier à l’aide des commutateurs du compilateur. Le [/volatile:ms](reference/volatile-volatile-keyword-interpretation.md) commutateur sélectionne l’étendue des sémantiques volatiles qui garantissent le classement fort, comme cela a été le cas classique pour x86 et x64 en raison du modèle de mémoire fort sur ces architectures de Microsoft. Le [/volatile:iso](reference/volatile-volatile-keyword-interpretation.md) commutateur sélectionne strict C++ standard des sémantiques volatiles qui ne garantissent pas le classement fort.

Sur l’architecture ARM, la valeur par défaut est **/volatile:iso** les processeurs ARM ont une faiblement triés de modèle de mémoire, et parce que le logiciel ARM ne présente pas un héritage de s’appuyer sur la sémantique d’étendues de **/volatile:ms**  et n’a généralement pour interagir avec les logiciels qui effectuent. Toutefois, il est toujours parfois pratique ou même obligatoire pour compiler un programme ARM à utiliser la sémantique d’étendue. Par exemple, il peut être trop coûteux porter un programme à utiliser la sémantique de la norme ISO C++ ou pilote logiciel devra peut-être respecter la sémantique traditionnelle pour fonctionner correctement. Dans ce cas, vous pouvez utiliser la **/volatile:ms** commutateur ; Toutefois, pour recréer des sémantiques volatiles traditionnels sur les objectifs d’ARM, le compilateur doit insérer des barrières de mémoire autour de chaque lecture ou d’écriture d’un `volatile` variable à appliquer classement fort, qui peut avoir un impact négatif sur les performances.

Sur les architectures x86 et x64, la valeur par défaut est **/volatile:ms** , car une grande partie du logiciel qui a déjà été créé pour ces architectures à l’aide de MSVC s’appuie dessus. Lorsque vous compilez les programmes x86 et x64, vous pouvez spécifier le **/volatile:iso** commutateur afin d’éviter la dépendance inutile sur des sémantiques volatiles traditionnels et de promouvoir la portabilité.

## <a name="see-also"></a>Voir aussi

[Configurer Visual C++ pour les processeurs ARM](configuring-programs-for-arm-processors-visual-cpp.md)

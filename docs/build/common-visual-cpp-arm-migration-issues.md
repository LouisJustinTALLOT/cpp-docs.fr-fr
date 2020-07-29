---
title: Problèmes courants de migration ARM Visual C++
ms.date: 05/06/2019
ms.assetid: 0f4c434e-0679-4331-ba0a-cc15dd435a46
ms.openlocfilehash: 889eed2b02362f33446cd9441ef84f406817b01a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224069"
---
# <a name="common-visual-c-arm-migration-issues"></a>Problèmes courants de migration ARM Visual C++

Lorsque vous utilisez le compilateur Microsoft C++ (MSVC), le même code source C++ peut produire des résultats différents sur l’architecture ARM que sur des architectures x86 ou x64.

## <a name="sources-of-migration-issues"></a>Sources de problèmes de migration

De nombreux problèmes que vous pouvez rencontrer lors de la migration du code de l’architecture x86 ou x64 vers l’architecture ARM sont liés aux constructions de code source qui peuvent appeler un comportement non défini, défini par l’implémentation ou non spécifié.

Le comportement non *défini* est le comportement que la norme C++ ne définit pas, et cela est dû à une opération qui n’a pas de résultat raisonnable : par exemple, la conversion d’une valeur à virgule flottante en entier non signé ou le décalage d’une valeur par un nombre de positions négatif ou supérieur au nombre de bits dans son type promu.

Le *comportement défini par l’implémentation* est le comportement que la norme C++ exige que le fournisseur du compilateur définit et documente. Un programme peut s’appuyer en toute sécurité sur un comportement défini par l’implémentation, même si cela ne peut pas être portable. Les tailles des types de données intégrés et leurs exigences d’alignement sont des exemples de comportement défini par l’implémentation. Un exemple d’opération qui peut être affectée par le comportement défini par l’implémentation accède à la liste d’arguments de la variable.

Le *comportement non spécifié* est le comportement que la norme C++ laisse intentionnellement non déterministe. Bien que le comportement soit considéré comme non déterministe, les appels particuliers du comportement non spécifié sont déterminés par l’implémentation du compilateur. Toutefois, il n’est pas nécessaire pour un fournisseur de compilateur de prédéterminer le résultat ou de garantir un comportement cohérent entre les appels comparables, et il n’existe aucune exigence pour la documentation. Un exemple de comportement non spécifié est l’ordre dans lequel les sous-expressions, qui incluent des arguments pour un appel de fonction, sont évaluées.

D’autres problèmes de migration peuvent être attribués aux différences matérielles entre les architectures ARM et x86 ou x64 qui interagissent différemment avec la norme C++. Par exemple, le modèle de mémoire forte de l’architecture x86 et x64 donne **`volatile`** à des variables qualifiées des propriétés supplémentaires qui ont été utilisées pour faciliter certains types de communications inter-threads dans le passé. Toutefois, le modèle de mémoire faible de l’architecture ARM ne prend pas en charge cette utilisation et la norme C++ ne l’exige pas.

> [!IMPORTANT]
> Bien que **`volatile`** obtient certaines propriétés qui peuvent être utilisées pour implémenter des formes limitées de communication inter-threads sur x86 et x64, ces propriétés supplémentaires ne sont pas suffisantes pour implémenter la communication entre les threads en général. La norme C++ recommande l’implémentation de cette communication en utilisant à la place des primitives de synchronisation appropriées.

Étant donné que les différentes plateformes peuvent exprimer différemment ces genres de comportements, le portage de logiciels entre les plateformes peut être difficile et sujet aux bogues s’il dépend du comportement d’une plateforme spécifique. Bien qu’un grand nombre de ces types de comportement puissent être observés et être stables, la confiance est au moins non portable et, dans le cas d’un comportement non défini ou non spécifié, est également une erreur. Même le comportement mentionné dans ce document ne doit pas être basé sur et peut changer dans les compilateurs ou implémentations d’UC futurs.

## <a name="example-migration-issues"></a>Exemples de problèmes de migration

Le reste de ce document décrit comment les différents comportements de ces éléments de langage C++ peuvent produire des résultats différents sur différentes plateformes.

### <a name="conversion-of-floating-point-to-unsigned-integer"></a>Conversion de virgule flottante en entier non signé

Sur l’architecture ARM, la conversion d’une valeur à virgule flottante en entier 32 bits sature à la valeur la plus proche que l’entier peut représenter si la valeur à virgule flottante est en dehors de la plage que l’entier peut représenter. Sur les architectures x86 et x64, la conversion est encapsulée si l’entier n’est pas signé, ou a la valeur-2147483648 si l’entier est signé. Aucune de ces architectures ne prend directement en charge la conversion des valeurs à virgule flottante en types d’entier plus petits ; au lieu de cela, les conversions sont effectuées à 32 bits, et les résultats sont tronqués à une taille plus petite.

Pour l’architecture ARM, la combinaison de saturation et de troncation signifie que la conversion en types non signés sature correctement les types non signés plus petits lorsqu’il sature un entier de 32 bits, mais produit un résultat tronqué pour les valeurs supérieures au type le plus petit pouvant être représentées, mais trop petites pour saturer l’entier 32 bits complet. La conversion est également saturée pour les entiers signés 32 bits, mais la troncation des entiers signés saturés donne la valeur-1 pour les valeurs saturées de manière positive et 0 pour les valeurs ayant une saturation négative. La conversion en un entier signé plus petit produit un résultat tronqué qui est imprévisible.

Pour les architectures x86 et x64, la combinaison du comportement de retour à la ligne pour les conversions d’entiers non signés et l’évaluation explicite pour les conversions d’entiers signés en cas de dépassement de capacité, ainsi que la troncation, rendent les résultats de la plupart des décalages imprévisibles s’ils sont trop volumineux.

Ces plateformes diffèrent également dans la façon dont elles gèrent la conversion des types d’entiers NaN (not-a-Number). Sur ARM, NaN convertit en 0x00000000 ; sur x86 et x64, elle est convertie en 0x80000000.

La conversion à virgule flottante ne peut s’appuyer que si vous savez que la valeur est comprise dans la plage du type entier vers lequel elle est convertie.

### <a name="shift-operator---behavior"></a>Comportement de l’opérateur de décalage ( \<\< >>)

Dans l’architecture ARM, une valeur peut être décalée vers la gauche ou vers la droite jusqu’à 255 bits avant que le modèle commence à se répéter. Sur les architectures x86 et x64, le modèle est répété à chaque multiple de 32, sauf si la source du modèle est une variable 64 bits ; dans ce cas, le modèle se répète à chaque multiple de 64 sur x64, et chaque multiple de 256 sur x86, où une implémentation logicielle est employée. Par exemple, pour une variable 32 bits dont la valeur 1 est décalée de gauche à 32 positions, sur ARM, le résultat est 0, sur x86, le résultat est 1 et, sur x64, le résultat est également 1. Toutefois, si la source de la valeur est une variable de 64 bits, le résultat sur les trois plateformes est 4294967296, et la valeur n’est pas entourée de zéro jusqu’à ce qu’elle soit décalée de 64 positions sur x64, ou 256 positions sur ARM et x86.

Étant donné que le résultat d’une opération de décalage qui dépasse le nombre de bits dans le type de source n’est pas défini, le compilateur n’a pas besoin d’avoir un comportement cohérent dans toutes les situations. Par exemple, si les deux opérandes d’un Shift sont connus au moment de la compilation, le compilateur peut optimiser le programme à l’aide d’une routine interne pour précalculer le résultat de la touche Maj, puis substituer le résultat à la place de l’opération de décalage. Si la valeur de décalage est trop grande ou négative, le résultat de la routine interne peut être différent du résultat de la même expression de décalage que celle exécutée par l’UC.

### <a name="variable-arguments-varargs-behavior"></a>Comportement des arguments variables (varargs)

Dans l’architecture ARM, les paramètres de la liste d’arguments variables qui sont transmis sur la pile sont sujets à l’alignement. Par exemple, un paramètre 64 bits est aligné sur une limite de 64 bits. Sur x86 et x64, les arguments passés sur la pile ne sont pas soumis à un alignement et à un pack serrés. Cette différence peut entraîner une fonction variadiques comme `printf` la lecture des adresses mémoire qui étaient destinées à être remplies sur ARM si la disposition attendue de la liste d’arguments de la variable n’est pas exactement mise en correspondance, même si elle peut fonctionner pour un sous-ensemble de certaines valeurs sur les architectures x86 ou x64. Examinez cet exemple :

```C
// notice that a 64-bit integer is passed to the function, but '%d' is used to read it.
// on x86 and x64 this may work for small values because %d will "parse" the low-32 bits of the argument.
// on ARM the calling convention will align the 64-bit value and the code will print a random value
printf("%d\n", 1LL);
```

Dans ce cas, le bogue peut être corrigé en s’assurant que la spécification de format correcte est utilisée afin que l’alignement de l’argument soit pris en compte. Ce code est correct :

```C
// CORRECT: use %I64d for 64-bit integers
printf("%I64d\n", 1LL);
```

### <a name="argument-evaluation-order"></a>Ordre d’évaluation des arguments

Étant donné que les processeurs ARM, x86 et x64 sont tellement différents, ils peuvent présenter des exigences différentes pour les implémentations du compilateur, ainsi que des possibilités différentes pour les optimisations. Pour cette raison, avec d’autres facteurs tels que les paramètres de convention d’appel et d’optimisation, un compilateur peut évaluer des arguments de fonction dans un ordre différent sur des architectures différentes ou lorsque les autres facteurs sont modifiés. Cela peut entraîner une modification inattendue du comportement d’une application qui s’appuie sur un ordre d’évaluation spécifique.

Ce type d’erreur peut se produire lorsque des arguments d’une fonction ont des effets secondaires qui affectent d’autres arguments à la fonction dans le même appel. En général, ce type de dépendance est facile à éviter, mais il peut parfois être masqué par des dépendances difficiles à discerner ou par la surcharge d’opérateur. Prenons l’exemple de code suivant :

```cpp
handle memory_handle;

memory_handle->acquire(*p);
```

Cela semble bien défini, mais si `->` et `*` sont des opérateurs surchargés, ce code est traduit en un nom qui ressemble à ceci :

```cpp
Handle::acquire(operator->(memory_handle), operator*(p));
```

Et s’il existe une dépendance entre `operator->(memory_handle)` et `operator*(p)` , le code peut reposer sur un ordre d’évaluation spécifique, même si le code d’origine semble ne pas être une dépendance possible.

### <a name="volatile-keyword-default-behavior"></a>comportement par défaut du mot clé volatile

Le compilateur MSVC prend en charge deux interprétations différentes du **`volatile`** qualificateur de stockage que vous pouvez spécifier à l’aide de commutateurs du compilateur. Le commutateur [/volatile : ms](reference/volatile-volatile-keyword-interpretation.md) sélectionne la sémantique volatile étendue Microsoft qui garantit un classement fort, comme c’était le cas traditionnellement pour x86 et x64 en raison du modèle de mémoire forte sur ces architectures. Le commutateur [/volatile : ISO](reference/volatile-volatile-keyword-interpretation.md) sélectionne la sémantique volatile standard C++ strict qui ne garantit pas un classement renforcé.

Dans l’architecture ARM, la valeur par défaut est **/volatile : ISO** , car les processeurs ARM ont un modèle de mémoire faiblement ordonné, et parce que ARM Software n’a pas de repos sur la sémantique étendue de **/volatile : ms** et n’a généralement pas besoin d’interagir avec le logiciel que fait. Toutefois, il est parfois pratique, voire nécessaire, de compiler un programme ARM pour utiliser la sémantique étendue. Par exemple, il peut s’avérer trop coûteux de déplacer un programme pour utiliser la sémantique ISO C++, ou le logiciel de pilote peut être amené à adhérer à la sémantique traditionnelle pour fonctionner correctement. Dans ce cas, vous pouvez utiliser le commutateur **/volatile : ms** . Toutefois, pour recréer la sémantique volatile traditionnelle sur les cibles ARM, le compilateur doit insérer des barrières de mémoire autour de chaque lecture ou écriture d’une **`volatile`** variable pour appliquer un ordre renforcé, ce qui peut avoir un impact négatif sur les performances.

Sur les architectures x86 et x64, la valeur par défaut est **/volatile : ms** , car la plupart des logiciels qui ont déjà été créés pour ces architectures à l’aide de MSVC s’appuient sur eux. Quand vous compilez des programmes x86 et x64, vous pouvez spécifier le commutateur **/volatile : ISO** afin d’éviter une dépendance inutile sur la sémantique volatile traditionnelle et de promouvoir la portabilité.

## <a name="see-also"></a>Voir aussi

[Configurer Visual C++ pour les processeurs ARM](configuring-programs-for-arm-processors-visual-cpp.md)

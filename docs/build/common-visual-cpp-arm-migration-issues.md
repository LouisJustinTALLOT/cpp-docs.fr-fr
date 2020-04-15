---
title: Problèmes courants de migration ARM Visual C++
ms.date: 05/06/2019
ms.assetid: 0f4c434e-0679-4331-ba0a-cc15dd435a46
ms.openlocfilehash: 2c29b4ffa5344b309622314970ce52c47a0ebd05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328793"
---
# <a name="common-visual-c-arm-migration-issues"></a>Problèmes courants de migration ARM Visual C++

Lors de l’utilisation du compilateur Microsoft CMD (MSVC), le même code source CMD peut produire des résultats différents sur l’architecture ARM que sur les architectures x86 ou x64.

## <a name="sources-of-migration-issues"></a>Sources de questions migratoires

De nombreux problèmes que vous pourriez rencontrer lorsque vous migrez le code des architectures x86 ou x64 à l’architecture ARM sont liés à des constructions de code source qui pourraient invoquer un comportement indéfini, défini par implémentation ou non spécifié.

*Un comportement indéfini* est un comportement que la norme Cmd ne définit pas, et c’est causé par une opération qui n’a pas de résultat raisonnable: par exemple, la conversion d’une valeur de point flottant à un integer non signé, ou le déplacement d’une valeur par un certain nombre de positions qui est négative ou dépasse le nombre de bits dans son type promu.

*Le comportement défini par implémentation* est un comportement que la norme CMD exige que le fournisseur de compilateur définisse et documente. Un programme peut s’appuyer en toute sécurité sur un comportement défini par la mise en œuvre, même si cela pourrait ne pas être portable. Des exemples de comportement définis par la mise en œuvre comprennent la taille des types de données intégrés et leurs exigences d’alignement. Un exemple d’opération qui pourrait être affectée par un comportement défini par la mise en œuvre est l’accès à la liste des arguments variables.

*Un comportement non spécifié* est un comportement que la norme C ' laisse intentionnellement non déterministe. Bien que le comportement soit considéré comme non déterministe, les invocations particulières d’un comportement non spécifié sont déterminées par la mise en œuvre du compilateur. Cependant, il n’est pas nécessaire qu’un vendeur de compilateur prédétermine le résultat ou garantisse un comportement cohérent entre des invocations comparables, et il n’y a aucune exigence de documentation. Un exemple de comportement non spécifié est l’ordre dans lequel les sous-expressions, qui incluent des arguments à un appel de fonction, sont évaluées.

D’autres problèmes de migration peuvent être attribués aux différences matérielles entre les architectures ARM et x86 ou x64 qui interagissent différemment avec la norme C. Par exemple, le modèle de mémoire solide de l’architecture x86 et x64 donne `volatile`des variables -qualifiées quelques propriétés supplémentaires qui ont été utilisées pour faciliter certains types de communication inter-thread dans le passé. Mais le modèle de mémoire faible de l’architecture ARM ne prend pas en charge cette utilisation, pas plus que la norme C N’en a besoin.

> [!IMPORTANT]
> Bien `volatile` que les gains de certaines propriétés qui peuvent être utilisés pour implémenter des formes limitées de communication inter-thread sur x86 et x64, ces propriétés supplémentaires ne sont pas suffisantes pour implémenter la communication inter-thread en général. La norme CMD recommande que cette communication soit mise en œuvre en utilisant plutôt des primitifs de synchronisation appropriés.

Parce que différentes plates-formes peuvent exprimer ce genre de comportement différemment, le portage des logiciels entre les plates-formes peut être difficile et sujette aux bogues si cela dépend du comportement d’une plate-forme spécifique. Bien que beaucoup de ces types de comportement peuvent être observés et peuvent sembler stables, en s’appuyant sur eux est au moins non-portable, et dans les cas de comportement indéfini ou non spécifié, est également une erreur. Même le comportement cité dans ce document ne doit pas être invoqué, et pourrait changer dans les futurs compilateurs ou implémentations CPU.

## <a name="example-migration-issues"></a>Exemple de problèmes de migration

Le reste de ce document décrit comment le comportement différent de ces éléments linguistiques de CMD peut produire des résultats différents sur différentes plates-formes.

### <a name="conversion-of-floating-point-to-unsigned-integer"></a>Conversion du point flottant en integer non signé

Sur l’architecture ARM, la conversion d’une valeur de point flottant en un intégriste 32 bits sature à la valeur la plus proche que l’intégriste peut représenter si la valeur de point flottant est en dehors de la plage que l’intégriste peut représenter. Sur les architectures x86 et x64, la conversion s’enroule autour si l’integer n’est pas signé, ou est réglé à -2147483648 si l’integer est signé. Aucune de ces architectures ne soutient directement la conversion des valeurs flottantes en petits types d’intégreurs; au lieu de cela, les conversions sont effectuées en 32 bits, et les résultats sont tronqués à une plus petite taille.

Pour l’architecture ARM, la combinaison de saturation et de troncation signifie que la conversion en types non signés sature correctement les petits types non signés lorsqu’il sature un intégrisé 32 bits, mais produit un résultat tronqué pour des valeurs qui sont plus grandes que le type plus petit peut représenter, mais trop petite pour saturer l’entier 32 bits integer. La conversion sature également correctement pour les intégriers signés 32 bits, mais la troncation d’intégrages saturés et signés se traduit par -1 pour des valeurs positivement saturées et 0 pour les valeurs saturées négativement. La conversion à un plus petit intégrant signé produit un résultat tronqué qui est imprévisible.

Pour les architectures x86 et x64, la combinaison d’un comportement enveloppant pour les conversions insignables non signées et l’évaluation explicite des conversions d’intégristes signés sur le débordement, ainsi que la troncation, rendent les résultats pour la plupart des changements imprévisibles s’ils sont trop grands.

Ces plates-formes diffèrent également dans la façon dont ils gèrent la conversion de NaN (Not-a-Number) aux types d’intégrerie. Sur ARM, NaN se convertit en 0x000000000; sur x86 et x64, il se convertit en 0x8000000000.

La conversion de points flottants ne peut être invoquée que si vous savez que la valeur se situe dans la plage du type d’intégreur vers lequel elle est convertie.

### <a name="shift-operator---behavior"></a>Comportement de\< \< l’opérateur de quart ( >>)

Sur l’architecture ARM, une valeur peut être décalée à gauche ou à droite jusqu’à 255 bits avant que le modèle commence à se répéter. Sur les architectures x86 et x64, le motif est répété à chaque multiple de 32 à moins que la source du modèle soit une variable de 64 bits ; dans ce cas, le modèle se répète à chaque multiple de 64 sur x64, et chaque multiple de 256 sur x86, où une implémentation logicielle est utilisée. Par exemple, pour une variable de 32 bits qui a une valeur de 1 décalé à gauche par 32 positions, sur ARM le résultat est de 0, sur x86 le résultat est 1, et sur x64 le résultat est également 1. Toutefois, si la source de la valeur est une variable de 64 bits, alors le résultat sur les trois plates-formes est 4294967296, et la valeur ne "enveloppe" pas jusqu’à ce qu’il a décalé 64 positions sur x64, ou 256 positions sur ARM et x86.

Étant donné que le résultat d’une opération de quart qui dépasse le nombre de bits dans le type source n’est pas défini, le compilateur n’est pas tenu d’avoir un comportement cohérent dans toutes les situations. Par exemple, si les deux opérands d’un quart de travail sont connus au moment de la compilation, le compilateur peut optimiser le programme en utilisant une routine interne pour précompter le résultat du quart de travail, puis en substituant le résultat à la place de l’opération de quart. Si le montant de quart est trop grand, ou négatif, le résultat de la routine interne pourrait être différent du résultat de la même expression de décalage que celle exécutée par le processeur.

### <a name="variable-arguments-varargs-behavior"></a>Comportement variable d’arguments (varargs)

Sur l’architecture ARM, les paramètres de la liste des arguments variables qui sont transmis sur la pile sont soumis à l’alignement. Par exemple, un paramètre 64 bits est aligné sur une limite de 64 bits. Sur x86 et x64, les arguments qui sont transmis sur la pile ne sont pas soumis à l’alignement et emballer étroitement. Cette différence peut provoquer une `printf` fonction variadic comme lire des adresses mémoire qui ont été conçus comme rembourrage sur ARM si la disposition attendue de la liste des arguments variables n’est pas assorti exactement, même si elle pourrait fonctionner pour un sous-ensemble de certaines valeurs sur les architectures x86 ou x64. Examinez cet exemple :

```C
// notice that a 64-bit integer is passed to the function, but '%d' is used to read it.
// on x86 and x64 this may work for small values because %d will "parse" the low-32 bits of the argument.
// on ARM the calling convention will align the 64-bit value and the code will print a random value
printf("%d\n", 1LL);
```

Dans ce cas, le bogue peut être corrigé en s’assurant que la spécification de format correcte est utilisée de sorte que l’alignement de l’argument est considéré. Ce code est correct :

```C
// CORRECT: use %I64d for 64-bit integers
printf("%I64d\n", 1LL);
```

### <a name="argument-evaluation-order"></a>Ordonnance d’évaluation de l’argument

Étant donné que les processeurs ARM, x86 et x64 sont si différents, ils peuvent présenter différentes exigences pour compiler les implémentations, ainsi que différentes possibilités d’optimisation. Pour cette raison, avec d’autres facteurs comme les paramètres d’appel-convention et d’optimisation, un compilateur peut évaluer les arguments de fonction dans un ordre différent sur différentes architectures ou lorsque les autres facteurs sont modifiés. Cela peut provoquer le comportement d’une application qui s’appuie sur un ordre d’évaluation spécifique de changer de façon inattendue.

Ce type d’erreur peut se produire lorsque les arguments à une fonction ont des effets secondaires qui ont un impact sur d’autres arguments à la fonction dans le même appel. Habituellement, ce type de dépendance est facile à éviter, mais il peut parfois être obscurci par des dépendances qui sont difficiles à discerner, ou par la surcharge de l’opérateur. Considérez cet exemple de code :

```cpp
handle memory_handle;

memory_handle->acquire(*p);
```

Cela semble bien défini, `->` `*` mais si et sont des opérateurs surchargés, alors ce code est traduit à quelque chose qui ressemble à ceci:

```cpp
Handle::acquire(operator->(memory_handle), operator*(p));
```

Et s’il y `operator->(memory_handle)` a `operator*(p)`une dépendance entre et, le code pourrait s’appuyer sur un ordre d’évaluation spécifique, même si le code original semble qu’il n’y a pas de dépendance possible.

### <a name="volatile-keyword-default-behavior"></a>comportement par défaut de mot-clé volatil

Le compilateur MSVC prend en `volatile` charge deux interprétations différentes du qualificatif de stockage que vous pouvez spécifier à l’aide de commutateurs compilateur. Le [commutateur /volatile:ms](reference/volatile-volatile-keyword-interpretation.md) sélectionne la sémantique volatile étendue de Microsoft qui garantissent une commande forte, comme cela a été le cas traditionnel pour x86 et x64 en raison du modèle de mémoire forte sur ces architectures. Le [commutateur /volatil : iso](reference/volatile-volatile-keyword-interpretation.md) sélectionne la sémantique volatile standard CMD stricte qui ne garantit pas un ordre fort.

Sur l’architecture ARM, la valeur par défaut est **/volatile:iso** parce que les processeurs ARM ont un modèle de mémoire faiblement commandé, et parce que le logiciel ARM n’a pas l’héritage de s’appuyer sur la sémantique étendue de **/volatile:ms** et n’a généralement pas à l’interface avec un logiciel qui ne. Cependant, il est encore parfois pratique ou même nécessaire de compiler un programme ARM pour utiliser la sémantique étendue. Par exemple, il peut être trop coûteux de mettre un programme pour utiliser la sémantique ISO CMD, ou le logiciel pilote pourrait devoir adhérer à la sémantique traditionnelle pour fonctionner correctement. Dans ces cas, vous pouvez utiliser le **commutateur /volatile:ms;** cependant, pour recréer la sémantique volatile traditionnelle sur les cibles ARM, le compilateur doit insérer des barrières de mémoire autour de chaque lecture ou écrire d’une `volatile` variable pour faire respecter l’ordre fort, ce qui peut avoir un impact négatif sur les performances.

Sur les architectures x86 et x64, la valeur par défaut est **/volatile:ms** parce qu’une grande partie du logiciel qui a déjà été créé pour ces architectures en utilisant MSVC s’appuie sur eux. Lorsque vous compilez des programmes x86 et x64, vous pouvez spécifier le commutateur **/volatile:iso** pour aider à éviter une dépendance inutile à la sémantique volatile traditionnelle, et pour promouvoir la portabilité.

## <a name="see-also"></a>Voir aussi

[Configurer Visual C++ pour les processeurs ARM](configuring-programs-for-arm-processors-visual-cpp.md)

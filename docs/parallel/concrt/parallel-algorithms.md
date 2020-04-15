---
title: Algorithmes parallèles
ms.date: 11/19/2018
helpviewer_keywords:
- parallel algorithms [Concurrency Runtime]
ms.assetid: 045dca7b-4d73-4558-a44c-383b88a28473
ms.openlocfilehash: a31787172c89e23e5eb32aa203b9f541584c0f68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363211"
---
# <a name="parallel-algorithms"></a>Algorithmes parallèles

La Bibliothèque des modèles parallèles (PPL) fournit des algorithmes qui effectuent simultanément des travaux sur les collections de données. Ces algorithmes ressemblent à ceux fournis par la Bibliothèque Standard de C.

Les algorithmes parallèles sont composés à partir des fonctionnalités existantes dans le Temps d’exécution de concurrency. Par exemple, la [concordance : :parallel-pour l’algorithme](reference/concurrency-namespace-functions.md#parallel_for) utilise une [concordance : : structured_task_group’objet](../../parallel/concrt/reference/structured-task-group-class.md) pour effectuer les itérations de boucle parallèle. Les `parallel_for` partitions d’algorithme fonctionnent de manière optimale étant donné le nombre disponible de ressources informatiques.

## <a name="sections"></a><a name="top"></a>Sections

- [Algorithme parallel_for](#parallel_for)

- [Algorithme parallel_for_each](#parallel_for_each)

- [Algorithme parallel_invoke](#parallel_invoke)

- [Algorithmes parallel_transform et parallel_reduce](#parallel_transform_reduce)

  - [Algorithme parallel_transform](#parallel_transform)

  - [Algorithme parallel_reduce](#parallel_reduce)

  - [Exemple : exécution du mappage et de la réduction en parallèle](#map_reduce_example)

- [Partitionnement du travail](#partitions)

- [Tri parallèle](#parallel_sorting)

  - [Choisir un algorithme de tri](#choose_sort)

## <a name="the-parallel_for-algorithm"></a><a name="parallel_for"></a>L’algorithme parallel_for

La [concordance: :parallel pour l’algorithme](reference/concurrency-namespace-functions.md#parallel_for) effectue à plusieurs reprises la même tâche en parallèle. Chacune de ces tâches est paramétrée par une valeur d’itération. Cet algorithme est utile lorsque vous avez un corps de boucle qui ne partage pas les ressources entre les itérations de cette boucle.

L’algorithme `parallel_for` divise les tâches d’une manière optimale pour l’exécution parallèle. Il utilise un algorithme de vol de travail et de vol de portée pour équilibrer ces partitions lorsque les charges de travail sont déséquilibrées. Lorsqu’une itération en boucle bloque en coopération, le temps d’exécution redistribue la plage d’itérations qui est attribuée au thread actuel à d’autres threads ou processeurs. De même, lorsqu’un thread complète une gamme d’itérations, le temps d’exécution redistribue le travail d’autres threads à ce thread. L’algorithme `parallel_for` prend également en charge *le parallélisme imbriqué.* Lorsqu’une boucle parallèle contient une autre boucle parallèle, le temps d’exécution coordonne les ressources de traitement entre les organes de boucle d’une manière efficace pour l’exécution parallèle.

L’algorithme `parallel_for` a plusieurs versions surchargées. La première version prend une valeur de démarrage, une valeur finale et une fonction de travail (expression lambda, objet de fonction, ou pointeur de fonction). La deuxième version prend une valeur de démarrage, une valeur finale, une valeur par laquelle marcher, et une fonction de travail. La première version de cette fonction utilise 1 comme valeur d’étape. Les versions restantes prennent des objets de `parallel_for` partitionnement, qui vous permettent de spécifier comment les plages de partition entre les threads. Les partitionneurs sont expliqués plus en détail dans la section [Partitioning Work](#partitions) dans ce document.

Vous pouvez `for` convertir de `parallel_for`nombreuses boucles à utiliser . Toutefois, `parallel_for` l’algorithme diffère `for` de l’énoncé de la manière suivante :

- L’algorithme `parallel_for` `parallel_for` n’exécute pas les tâches dans un ordre prédéterminé.

- L’algorithme `parallel_for` ne prend pas en charge les conditions de résiliation arbitraires. L’algorithme `parallel_for` s’arrête lorsque la valeur actuelle de `last`la variable d’itération est inférieure à .

- Le `_Index_type` paramètre de type doit être un type intégral. Ce type intégral peut être signé ou non signé.

- L’itération de boucle doit être en avant. L’algorithme `parallel_for` jette une exception de type [std::invalid_argument](../../standard-library/invalid-argument-class.md) si le `_Step` paramètre est inférieur à 1.

- Le mécanisme de manipulation `parallel_for` d’exception pour `for` l’algorithme diffère de celui d’une boucle. Si plusieurs exceptions se produisent simultanément dans un corps de boucle parallèle, le runtime `parallel_for`ne propage qu’une seule des exceptions au fil qui a appelé . En outre, lorsqu’une itération en boucle lance une exception, le temps d’exécution n’arrête pas immédiatement la boucle globale. Au lieu de cela, la boucle est placée dans l’état annulé et le temps d’exécution rejette toutes les tâches qui n’ont pas encore commencé. Pour plus d’informations sur la gestion des exceptions et les algorithmes parallèles, voir [Exception Handling](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Bien `parallel_for` que l’algorithme ne prend pas en charge les conditions de résiliation arbitraires, vous pouvez utiliser l’annulation pour arrêter toutes les tâches. Pour plus d’informations sur l’annulation, voir [Annulation dans la PPL](cancellation-in-the-ppl.md).

> [!NOTE]
> Le coût de planification qui résulte de l’équilibrage de charge et le soutien pour des fonctionnalités telles que l’annulation pourrait ne pas surmonter les avantages de l’exécution du corps de boucle en parallèle, particulièrement quand le corps de boucle est relativement petit. Vous pouvez minimiser cette surcharge en utilisant un partitionneur dans votre boucle parallèle. Pour plus d’informations, voir [Partitioning Work](#partitions) plus tard dans ce document.

### <a name="example"></a>Exemple

L’exemple suivant montre la `parallel_for` structure de base de l’algorithme. Cet exemple imprime à la console chaque valeur de la gamme [1, 5] en parallèle.

[!code-cpp[concrt-parallel-for-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_1.cpp)]

Cet exemple produit la sortie de l’échantillon suivant :

```Output
1 2 4 3 5
```

Parce `parallel_for` que l’algorithme agit sur chaque élément en parallèle, l’ordre dans lequel les valeurs sont imprimées à la console variera.

Pour un exemple complet `parallel_for` qui utilise l’algorithme, voir [Comment: Écrire une boucle parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md).

[[Top](#top)]

## <a name="the-parallel_for_each-algorithm"></a><a name="parallel_for_each"></a>L’algorithme parallel_for_each

La [concordance : :parallel-pour-chaque](reference/concurrency-namespace-functions.md#parallel_for_each) algorithme effectue des tâches sur un conteneur itératif, tels que celles fournies par la Bibliothèque standard de C, en parallèle. Il utilise la même logique `parallel_for` de partition que l’algorithme utilise.

L’algorithme `parallel_for_each` ressemble à l’algorithme [std : : for_each](../../standard-library/algorithm-functions.md#for_each) algorithme `parallel_for_each` de la Bibliothèque standard, sauf que l’algorithme exécute les tâches en même temps. Comme d’autres `parallel_for_each` algorithmes parallèles, n’exécute pas les tâches dans un ordre spécifique.

Bien `parallel_for_each` que l’algorithme fonctionne à la fois sur les itérateurs vers l’avant et les itérateurs d’accès aléatoire, il fonctionne mieux avec des itérateurs d’accès aléatoire.

### <a name="example"></a>Exemple

L’exemple suivant montre la `parallel_for_each` structure de base de l’algorithme. Cet exemple imprime à la console chaque valeur dans un [objet std::array](../../standard-library/array-class-stl.md) en parallèle.

[!code-cpp[concrt-parallel-for-each-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_2.cpp)]

Cet exemple produit la sortie de l’échantillon suivant :

```Output
4 5 1 2 3
```

Parce `parallel_for_each` que l’algorithme agit sur chaque élément en parallèle, l’ordre dans lequel les valeurs sont imprimées à la console variera.

Pour un exemple complet `parallel_for_each` qui utilise l’algorithme, voir [Comment: Écrire une boucle parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md).

[[Top](#top)]

## <a name="the-parallel_invoke-algorithm"></a><a name="parallel_invoke"></a>L’algorithme parallel_invoke

La [concordance : :p’algorithme d’appel d’action](reference/concurrency-namespace-functions.md#parallel_invoke) exécute un ensemble de tâches en parallèle. Il ne revient pas avant la fin de chaque tâche. Cet algorithme est utile lorsque vous avez plusieurs tâches indépendantes que vous souhaitez exécuter en même temps.

L’algorithme `parallel_invoke` prend comme paramètres une série de fonctions de travail (fonctions lambda, objets de fonction, ou pointeurs de fonction). L’algorithme `parallel_invoke` est surchargé pour prendre entre deux et dix paramètres. Chaque fonction que vous `parallel_invoke` passez à doit prendre zéro paramètres.

Comme d’autres `parallel_invoke` algorithmes parallèles, n’exécute pas les tâches dans un ordre spécifique. Le sujet [Parallélisme de tâche](../../parallel/concrt/task-parallelism-concurrency-runtime.md) explique comment l’algorithme `parallel_invoke` se rapporte aux tâches et aux groupes de tâches.

### <a name="example"></a>Exemple

L’exemple suivant montre la `parallel_invoke` structure de base de l’algorithme. Cet exemple appelle `twice` simultanément la fonction sur trois variables locales et imprime le résultat à la console.

[!code-cpp[concrt-parallel-invoke-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_3.cpp)]

Cet exemple produit la sortie suivante :

```Output
108 11.2 HelloHello
```

Pour des exemples `parallel_invoke` complets qui utilisent l’algorithme, voir [Comment: Utilisez parallel_invoke pour écrire une routine de tri parallèle](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md) et [comment: Utilisez parallel_invoke pour exécuter des opérations parallèles](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md).

[[Top](#top)]

## <a name="the-parallel_transform-and-parallel_reduce-algorithms"></a><a name="parallel_transform_reduce"></a>Les algorithmes parallel_transform et parallel_reduce

La [concordance : :parallel-transform](reference/concurrency-namespace-functions.md#parallel_transform) et [la concurrence : :p-ci](reference/concurrency-namespace-functions.md#parallel_reduce) sont des versions parallèles des algorithmes de la Bibliothèque standard [de Cmd std : : transformer](../../standard-library/algorithm-functions.md#transform) et [std : : accumuler,](../../standard-library/numeric-functions.md#accumulate)respectivement. Les versions Concurrency Runtime se comportent comme les versions de la Bibliothèque standard de C, sauf que l’ordre d’opération n’est pas déterminé parce qu’ils s’exécutent en parallèle. Utilisez ces algorithmes lorsque vous travaillez avec un ensemble qui est assez grand pour obtenir des performances et des avantages d’évolutivité d’être traité en parallèle.

> [!IMPORTANT]
> Les `parallel_transform` `parallel_reduce` itérateurs et les algorithmes ne prennent en charge que l’accès aléatoire, bidirectionnel et les itérateurs vers l’avant parce que ces itérateurs produisent des adresses mémoire stables. En outre, ces itérateurs`const` doivent produire des valeurs non l-.

### <a name="the-parallel_transform-algorithm"></a><a name="parallel_transform"></a>L’algorithme parallel_transform

Vous pouvez `parallel transform` utiliser l’algorithme pour effectuer de nombreuses opérations de parallélisation des données. Vous pouvez par exemple :

- Ajuster la luminosité d’une image et effectuer d’autres opérations de traitement d’image.

- Résumez ou prenez le produit à points entre deux vecteurs et effectuez d’autres calculs numériques sur les vecteurs.

- Effectuer le traçage des rayons 3D, où chaque itération se réfère à un pixel qui doit être rendu.

L’exemple suivant montre la structure de `parallel_transform` base qui est utilisée pour appeler l’algorithme. Cet exemple nie chaque élément d’un std:: objet[vectoriel](../../standard-library/vector-class.md) de deux façons. La première façon utilise une expression lambda. La deuxième façon utilise [std::negate](../../standard-library/negate-struct.md), qui dérive de [std::unary_function](../../standard-library/unary-function-struct.md).

[!code-cpp[concrt-basic-parallel-transform#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_4.cpp)]

> [!WARNING]
> Cet exemple démontre l’utilisation de base de `parallel_transform`. Étant donné que la fonction de travail n’effectue pas une quantité importante de travail, on ne s’attend pas à une augmentation significative du rendement dans cet exemple.

L’algorithme `parallel_transform` a deux surcharges. La première surcharge prend une portée d’entrée et une fonction nonary. La fonction unaire peut être une expression lambda qui prend un argument, `unary_function`un objet de fonction, ou un type qui dérive de . La deuxième surcharge prend deux gammes d’entrées et une fonction binaire. La fonction binaire peut être une expression lambda qui prend deux arguments, un objet de fonction, ou un type qui dérive de [std::binary_function](../../standard-library/binary-function-struct.md). L’exemple suivant illustre ces différences.

[!code-cpp[concrt-parallel-transform-vectors#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_5.cpp)]

> [!IMPORTANT]
> L’itérateur que vous fournissez pour la sortie de `parallel_transform` doit complètement chevaucher l’itérateur d’entrée ou ne pas se chevaucher du tout. Le comportement de cet algorithme n’est pas précisé si les itérateurs d’entrée et de sortie se chevauchent partiellement.

### <a name="the-parallel_reduce-algorithm"></a><a name="parallel_reduce"></a>L’algorithme parallel_reduce

L’algorithme `parallel_reduce` est utile lorsque vous avez une séquence d’opérations qui satisfont la propriété associative. (Cet algorithme ne nécessite pas la propriété commutative.) Voici quelques-unes des opérations `parallel_reduce`que vous pouvez effectuer avec :

- Multipliez les séquences de matrices pour produire une matrice.

- Multipliez un vecteur par une séquence de matrices pour produire un vecteur.

- Calculez la longueur d’une séquence de cordes.

- Combinez une liste d’éléments, tels que les cordes, en un seul élément.

L’exemple de base suivant `parallel_reduce` montre comment utiliser l’algorithme pour combiner une séquence de cordes en une seule chaîne. Comme pour les `parallel_transform`exemples pour , les gains de performance ne sont pas attendus dans cet exemple de base.

[!code-cpp[concrt-basic-parallel-reduce#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_6.cpp)]

Dans de nombreux cas, `parallel_reduce` vous pouvez penser comme `parallel_for_each` un raccourci pour l’utilisation de l’algorithme avec la [concordance::classe combinable.](../../parallel/concrt/reference/combinable-class.md)

### <a name="example-performing-map-and-reduce-in-parallel"></a><a name="map_reduce_example"></a>Exemple : Effectuer la carte et réduire en parallèle

Une opération *de carte* applique une fonction à chaque valeur dans une séquence. Une opération *de réduction* combine les éléments d’une séquence en une seule valeur. Vous pouvez utiliser la [std](../../standard-library/algorithm-functions.md#transform) de la Bibliothèque standard : : transformer et [std : : accumuler des](../../standard-library/numeric-functions.md#accumulate) fonctions pour effectuer la carte et réduire les opérations. Cependant, pour de nombreux problèmes, vous pouvez utiliser l’algorithme `parallel_transform` pour effectuer l’opération de carte en parallèle et l’algorithme `parallel_reduce` effectuer l’opération de réduction en parallèle.

L’exemple suivant compare le temps qu’il faut pour calculer la somme des nombres premiers en série et en parallèle. La phase de carte transforme les valeurs non-prime à 0 et la phase de réduction résume les valeurs.

[!code-cpp[concrt-parallel-map-reduce-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_7.cpp)]

Pour un autre exemple qui effectue une carte et de réduire l’opération en parallèle, voir [Comment effectuer la carte et réduire les opérations en parallèle](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).

[[Top](#top)]

## <a name="partitioning-work"></a><a name="partitions"></a>Travail de partitionnement

Pour paralléliser une opération sur une source de données, une étape essentielle consiste à *diviser* la source en plusieurs sections qui peuvent être consultées simultanément par plusieurs threads. Un cloisonneur précise comment un algorithme parallèle devrait répartir les gammes entre les threads. Comme expliqué précédemment dans ce document, le PPL utilise un mécanisme de partition par défaut qui crée une charge de travail initiale et utilise ensuite un algorithme de vol de travail et de vol de portée pour équilibrer ces partitions lorsque les charges de travail sont déséquilibrées. Par exemple, lorsqu’une itération en boucle complète une gamme d’itérations, le temps d’exécution redistribue le travail d’autres threads à ce thread. Cependant, pour certains scénarios, vous voudrez peut-être spécifier un mécanisme de partitionnement différent qui est mieux adapté à votre problème.

Le `parallel_for` `parallel_for_each`, `parallel_transform` , et les algorithmes fournissent des versions surchargées qui prennent un paramètre supplémentaire, `_Partitioner`. Ce paramètre définit le type de partitionneur qui divise le travail. Voici les types de partitionneurs que la PPL définit :

[concurrence::affinity_partitioner](../../parallel/concrt/reference/affinity-partitioner-class.md)<br/>
Divise le travail en un nombre fixe de plages (généralement le nombre de threads de travailleurs qui sont disponibles pour travailler sur la boucle). Ce type de `static_partitioner`partitionneur ressemble, mais améliore l’affinité cache par la façon dont il cartographie les gammes aux fils de travailleur. Ce type de partitionnement peut améliorer les performances lorsqu’une boucle est exécutée sur le même ensemble de données plusieurs fois (comme une boucle dans une boucle) et que les données s’intègrent dans le cache. Ce partitionneur ne participe pas entièrement à l’annulation. Il n’utilise pas non plus la sémantique de blocage coopératif et ne peut donc pas être utilisé avec des boucles parallèles qui ont une dépendance vers l’avenir.

[concurrence::auto_partitioner](../../parallel/concrt/reference/auto-partitioner-class.md)<br/>
Divise le travail en un nombre initial de plages (généralement le nombre de threads de travailleurs qui sont disponibles pour travailler sur la boucle). Le temps d’exécution utilise ce type par défaut lorsque vous `_Partitioner` n’appelez pas un algorithme parallèle surchargé qui prend un paramètre. Chaque plage peut être divisée en sous-gammes, ce qui permet d’équilibrer la charge. Lorsqu’une gamme de travaux se termine, le temps d’exécution redistribue les sous-gammes de travail d’autres threads à ce fil. Utilisez ce partitionneur si votre charge de travail ne relève pas de l’une des autres catégories ou si vous avez besoin d’un soutien complet pour l’annulation ou le blocage coopératif.

[concurrence::simple_partitioner](../../parallel/concrt/reference/simple-partitioner-class.md)<br/>
Divise le travail en plages de telle sorte que chaque plage a au moins le nombre d’itérations qui sont spécifiées par la taille donnée de morceau. Ce type de partitionneur participe à l’équilibrage de charge; cependant, le temps d’exécution ne divise pas les plages en sous-gammes. Pour chaque travailleur, le temps d’exécution vérifie `_Chunk_size` l’annulation et effectue l’équilibrage de charge après l’exécution terminée.

[concurrence::static_partitioner](../../parallel/concrt/reference/static-partitioner-class.md)<br/>
Divise le travail en un nombre fixe de plages (généralement le nombre de threads de travailleurs qui sont disponibles pour travailler sur la boucle). Ce type de partitionneur peut améliorer les performances parce qu’il n’utilise pas le vol de travail et a donc moins de frais généraux. Utilisez ce type de partition lorsque chaque itération d’une boucle parallèle effectue une quantité fixe et uniforme de travail et vous n’avez pas besoin de soutien pour l’annulation ou le blocage coopératif avant.

> [!WARNING]
> Les `parallel_for_each` `parallel_transform` algorithmes et les algorithmes ne prennent en charge que les conteneurs qui utilisent des itérateurs d’accès aléatoires (tels que std::[vecteur](../../standard-library/vector-class.md)) pour les partitionneurs statiques, simples et affinités. L’utilisation de contenants qui utilisent des itérateurs bidirectionnels et avant produit une erreur de compilation. Le partitionneur `auto_partitioner`par défaut, , prend en charge tous les trois de ces types d’itérateur.

Typiquement, ces partitionneurs sont utilisés de `affinity_partitioner`la même manière, sauf pour . La plupart des types de partitionneurs ne maintiennent pas l’état et ne sont pas modifiés par le temps d’exécution. Par conséquent, vous pouvez créer ces objets de partitionnement sur le site d’appel, comme indiqué dans l’exemple suivant.

[!code-cpp[concrt-static-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_8.cpp)]

Cependant, vous devez `affinity_partitioner` passer un objet`const`comme une référence non- , l-valeur de sorte que l’algorithme peut stocker l’état pour les boucles futures à réutiliser. L’exemple suivant montre une application de base qui effectue la même opération sur un ensemble de données en parallèle plusieurs fois. L’utilisation `affinity_partitioner` de peut améliorer les performances parce que le tableau est susceptible de s’adapter dans le cache.

[!code-cpp[concrt-affinity-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_9.cpp)]

> [!CAUTION]
> Faites preuve de prudence lorsque vous modifiez le code `static_partitioner` `affinity_partitioner`existant qui repose sur la sémantique de blocage coopératif à utiliser ou . Ces types de partitionneurs n’utilisent pas l’équilibrage de charge ou le vol de portée, et peuvent donc modifier le comportement de votre application.

La meilleure façon de déterminer s’il faut utiliser un partitionneur dans un scénario donné est d’expérimenter et de mesurer le temps qu’il faut aux opérations pour effectuer sous des charges représentatives et des configurations informatiques. Par exemple, le partitionnement statique peut accélérer considérablement les opérations sur un ordinateur multicœur doté de quelques cœurs, mais il peut entraîner des ralentissements sur les ordinateurs qui disposent de nombreux cœurs.

[[Top](#top)]

## <a name="parallel-sorting"></a><a name="parallel_sorting"></a>Tri parallèle

La PPL fournit trois algorithmes de tri : [la concurrence : :parallel-sort,](reference/concurrency-namespace-functions.md#parallel_sort) [la concurrence : :parallel-buffered-sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort), et [la concurrence: :parallel-radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort). Ces algorithmes de tri sont utiles lorsque vous avez un ensemble de données qui peut bénéficier d’être triés en parallèle. En particulier, le tri en parallèle est utile lorsque vous avez un grand jeu de données ou lorsque vous utilisez une opération de comparaison computationnellement coûteuse pour trier vos données. Chacun de ces algorithmes trie les éléments en place.

Les `parallel_sort` `parallel_buffered_sort` algorithmes et les algorithmes sont tous deux des algorithmes basés sur la comparaison. C’est-à-dire qu’ils comparent les éléments par valeur. L’algorithme `parallel_sort` n’a pas d’exigences de mémoire supplémentaires, et est adapté pour le tri à usage général. L’algorithme `parallel_buffered_sort` peut `parallel_sort`fonctionner mieux que, mais il nécessite O(N) espace.

L’algorithme `parallel_radixsort` est basé sur le hachage. Autrement dit, il utilise des clés integer pour trier les éléments. En utilisant des touches, cet algorithme peut calculer directement la destination d’un élément au lieu d’utiliser des comparaisons. Comme, `parallel_buffered_sort`cet algorithme nécessite o(N) l’espace.

Le tableau suivant résume les propriétés importantes des trois algorithmes de tri parallèles.

|Algorithm|Description|Mécanisme de tri|Trier la stabilité|Mémoire requise|Complexité temporelle|Accès à l’itérateur|
|---------------|-----------------|-----------------------|--------------------|-------------------------|---------------------|---------------------|
|`parallel_sort`|Type général de comparaison.|Comparer à base (ascendant)|Instable|None|O((N/P)log (N/P) - 2N ((P-1)/P))|Aléatoire|
|`parallel_buffered_sort`|Un type de comparaison plus rapide à usage général qui nécessite de l’espace O(N).|Comparer à base (ascendant)|Instable|Nécessite un espace O(N) supplémentaire|O((N/P)log(N))|Aléatoire|
|`parallel_radixsort`|Integer tri basé sur les clés qui nécessite O(N) espace.|Basé sur le haschich|Stable|Nécessite un espace O(N) supplémentaire|O(N/P)|Aléatoire|

L’illustration suivante montre les propriétés importantes des trois algorithmes de tri parallèles plus graphiquement.

![Comparaison des algorithmes de tri](../../parallel/concrt/media/concrt_parallel_sorting.png "Comparaison des algorithmes de tri")

Ces algorithmes de tri parallèles suivent les règles d’annulation et de traitement des exceptions. Pour plus d’informations sur l’annulation et le traitement des exceptions dans le Temps de fonctionnement De concurrency, voir [Annuler les algorithmes parallèles](../../parallel/concrt/cancellation-in-the-ppl.md#algorithms) et [la manipulation d’exception](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

> [!TIP]
> Ces algorithmes de tri parallèles prennent en charge la sémantique de mouvement. Vous pouvez définir un opérateur d’affectation de déménagement pour permettre aux opérations de swap de se produire plus efficacement. Pour plus d’informations sur la sémantique de déménagement et l’opérateur d’affectation de déménagement, voir [Rvalue Reference Declarator: &&](../../cpp/rvalue-reference-declarator-amp-amp.md), et [Move Constructors and Move Assignment Operators (CMD)](../../cpp/move-constructors-and-move-assignment-operators-cpp.md). Si vous ne fournissez pas d’opérateur d’affectation de déménagement ou de fonction de swap, les algorithmes de tri utilisent le constructeur de copie.

L’exemple de base `parallel_sort` suivant montre `vector` `int` comment utiliser pour trier une des valeurs. Par défaut, `parallel_sort` utilise [std::moins](../../standard-library/less-struct.md) de comparer les valeurs.

[!code-cpp[concrt-basic-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_10.cpp)]

Cet exemple montre comment fournir une fonction de comparaison personnalisée. Il utilise le [std::complex::vraie](../../standard-library/complex-class.md#real) méthode pour trier [std::complexe\<double>](../../standard-library/complex-double.md) valeurs dans l’ordre ascendant.

[!code-cpp[concrt-basic-parallel-sort#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_11.cpp)]

Cet exemple montre comment fournir une `parallel_radixsort` fonction de hachage à l’algorithme. Cet exemple trie les points 3D. Les points sont triés en fonction de leur distance par rapport à un point de référence.

[!code-cpp[concrt-parallel-sort-points#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_12.cpp)]

Pour illustrer, cet exemple utilise un ensemble de données relativement petit. Vous pouvez augmenter la taille initiale du vecteur pour expérimenter des améliorations de performances sur de plus grands ensembles de données.

Cet exemple utilise une expression lambda comme fonction de hachage. Vous pouvez également utiliser l’une des implémentations intégrées de la std::[classe de hachage](../../standard-library/hash-class.md) ou définir votre propre spécialisation. Vous pouvez également utiliser un objet de fonction de hachage personnalisé, comme indiqué dans cet exemple :

[!code-cpp[concrt-parallel-sort-points#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_13.cpp)]

[!code-cpp[concrt-parallel-sort-points#3](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_14.cpp)]

La fonction de hachage doit retourner un type intégral[(std::is_integral::la valeur](../../standard-library/is-integral-class.md) doit être **vraie**). Ce type intégral doit `size_t`être convertible au type .

### <a name="choosing-a-sorting-algorithm"></a><a name="choose_sort"></a>Choisir un algorithme de tri

Dans de `parallel_sort` nombreux cas, fournit le meilleur équilibre de la vitesse et des performances de mémoire. Cependant, lorsque vous augmentez la taille de votre ensemble de données, le `parallel_buffered_sort` nombre `parallel_radixsort` de processeurs disponibles ou la complexité de votre fonction de comparaison, ou peut être plus performant. La meilleure façon de déterminer quel algorithme de tri utiliser dans un scénario donné est d’expérimenter et de mesurer le temps qu’il faut pour trier les données typiques selon des configurations informatiques représentatives. Gardez à l’esprit les lignes directrices suivantes lorsque vous choisissez une stratégie de tri.

- La taille de votre ensemble de données. Dans ce document, un *petit* jeu de données contient moins de 1 000 éléments, un jeu de données *moyen* contient entre 10 000 et 100 000 éléments, et un *grand* jeu de données contient plus de 100 000 éléments.

- La quantité de travail que votre fonction de comparaison ou fonction de hachage effectue.

- La quantité de ressources informatiques disponibles.

- Les caractéristiques de votre ensemble de données. Par exemple, un algorithme peut bien fonctionner pour les données qui sont déjà presque triées, mais pas aussi bien pour les données qui sont complètement non triées.

- La taille du morceau. L’argument facultatif `_Chunk_size` spécifie lorsque l’algorithme passe d’un parallèle à une mise en œuvre de type sériel car il subdivise le type global en unités de travail plus petites. Par exemple, si vous fournissez 512, l’algorithme passe à la mise en œuvre en série lorsqu’une unité de travail contient 512 éléments ou moins. Une mise en œuvre en série peut améliorer les performances globales parce qu’elle élimine les frais généraux qui sont nécessaires pour traiter les données en parallèle.

Il pourrait ne pas être utile de trier un petit jeu de données en parallèle, même lorsque vous avez un grand nombre de ressources informatiques disponibles ou votre fonction de comparaison ou de fonction de hachage effectue une quantité relativement importante de travail. Vous pouvez utiliser [std::trier](../../standard-library/algorithm-functions.md#sort) la fonction pour trier les petits jeux de données. `parallel_sort` (et `parallel_buffered_sort` `sort` appelez lorsque vous spécifiez une taille `parallel_buffered_sort` de morceau qui est plus grande que le jeu de données; cependant, aurait à allouer O(N) espace, ce qui pourrait prendre plus de temps en raison de la contention de verrouillage ou l’allocation de mémoire.)

Si vous devez conserver la mémoire ou que votre `parallel_sort` allocation de mémoire est sujette à une contention de verrouillage, utilisez-le pour trier un jeu de données de taille moyenne. `parallel_sort`ne nécessite pas d’espace supplémentaire; les autres algorithmes nécessitent de l’espace O(N).

Utilisez `parallel_buffered_sort` pour trier les jeux de données de taille moyenne et lorsque votre application répond à l’exigence supplémentaire d’espace O(N). `parallel_buffered_sort`peut être particulièrement utile lorsque vous avez un grand nombre de ressources informatiques ou une fonction de comparaison coûteuse ou fonction de hachage.

Utilisez `parallel_radixsort` pour trier les grands jeux de données et lorsque votre application répond à l’exigence supplémentaire d’espace O(N). `parallel_radixsort`peut être particulièrement utile lorsque l’opération de comparaison équivalente est plus coûteuse ou lorsque les deux opérations sont coûteuses.

> [!CAUTION]
> La mise en œuvre d’une bonne fonction de hachage exige que vous connaissiez la plage de jeu de données et comment chaque élément du jeu de données est transformé en valeur non signée correspondante. Étant donné que l’opération de hachage fonctionne sur des valeurs non signées, envisagez une stratégie de tri différente si des valeurs de hachage non signées ne peuvent pas être produites.

L’exemple suivant compare `sort`les `parallel_sort` `parallel_buffered_sort`performances `parallel_radixsort` de , , et par rapport au même grand ensemble de données aléatoires.

[!code-cpp[concrt-choosing-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_15.cpp)]

Dans cet exemple, qui suppose qu’il est acceptable d’allouer de l’espace O(N) pendant le tri, `parallel_radixsort` effectue le meilleur sur ce jeu de données sur cette configuration informatique.

[[Top](#top)]

## <a name="related-topics"></a>Rubriques connexes

|Intitulé|Description|
|-----------|-----------------|
|[Comment : écrire une boucle parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)|Montre comment utiliser `parallel_for` l’algorithme pour effectuer la multiplication de matrice.|
|[Comment : écrire une boucle parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)|Montre comment utiliser `parallel_for_each` l’algorithme pour calculer le nombre de nombres premiers dans un [std::objet de tableau](../../standard-library/array-class-stl.md) en parallèle.|
|[Comment : utiliser parallel_invoke pour écrire une routine de tri parallèle](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|Montre comment utiliser l'algorithme `parallel_invoke` pour améliorer les performances de l'algorithme de tri bitonique.|
|[Comment : Utiliser parallel_invoke pour exécuter des opérations parallèles](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Montre comment utiliser l'algorithme `parallel_invoke` pour améliorer les performances d'un programme qui effectue plusieurs opérations sur une source de données partagée.|
|[Comment : exécuter des opérations de mappage et de réduction en parallèle](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|Montre comment utiliser `parallel_transform` `parallel_reduce` les algorithmes et les algorithmes pour effectuer une carte et réduire l’opération qui compte les occurrences de mots dans les fichiers.|
|[Bibliothèque de modèles parallèles](../../parallel/concrt/parallel-patterns-library-ppl.md)|Décrit le PPL, qui fournit un modèle de programmation impératif qui favorise l’évolutivité et la facilité d’utilisation pour le développement d’applications simultanées.|
|[Annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md)|Explique le rôle de l’annulation dans la PPL, comment annuler les travaux parallèles et comment déterminer quand un groupe de travail est annulé.|
|[Gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Explique le rôle de la gestion des exceptions dans le Temps d’exécution de concurrency.|

## <a name="reference"></a>Informations de référence

[parallel_for, fonction](reference/concurrency-namespace-functions.md#parallel_for)

[parallel_for_each, fonction](reference/concurrency-namespace-functions.md#parallel_for_each)

[parallel_invoke, fonction](reference/concurrency-namespace-functions.md#parallel_invoke)

[affinity_partitioner, classe](../../parallel/concrt/reference/affinity-partitioner-class.md)

[auto_partitioner, classe](../../parallel/concrt/reference/auto-partitioner-class.md)

[simple_partitioner, classe](../../parallel/concrt/reference/simple-partitioner-class.md)

[static_partitioner, classe](../../parallel/concrt/reference/static-partitioner-class.md)

[parallel_sort, fonction](reference/concurrency-namespace-functions.md#parallel_sort)

[parallel_buffered_sort, fonction](reference/concurrency-namespace-functions.md#parallel_buffered_sort)

[fonction parallel_radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort)

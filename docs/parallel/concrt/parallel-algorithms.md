---
title: Algorithmes parallèles
ms.date: 11/19/2018
helpviewer_keywords:
- parallel algorithms [Concurrency Runtime]
ms.assetid: 045dca7b-4d73-4558-a44c-383b88a28473
ms.openlocfilehash: b8a08919ce6792babb9b8b1b809e242465a200f9
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176443"
---
# <a name="parallel-algorithms"></a>Algorithmes parallèles

La bibliothèque de modèles parallèles (PPL) fournit des algorithmes qui exécutent simultanément du travail sur des collections de données. Ces algorithmes ressemblent à ceux fournis par la bibliothèque Standard C++.

Les algorithmes parallèles sont composés de fonctionnalités existantes dans le Runtime d’accès concurrentiel. Par exemple, le [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorithme utilise un [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) objet pour exécuter les itérations de boucle parallèle. Le `parallel_for` partitions d’algorithme fonctionnent de façon optimale étant donné le nombre de ressources informatiques disponibles.

##  <a name="top"></a> Sections

- [Algorithme parallel_for](#parallel_for)

- [Algorithme parallel_for_each](#parallel_for_each)

- [Algorithme parallel_invoke](#parallel_invoke)

- [Les algorithmes parallel_transform et parallel_reduce](#parallel_transform_reduce)

    - [Algorithme parallel_transform](#parallel_transform)

    - [Algorithme parallel_reduce](#parallel_reduce)

    - [Exemple : Exécution du mappage et réduction en parallèle](#map_reduce_example)

- [Partitionnement du travail](#partitions)

- [Tri parallèle](#parallel_sorting)

    - [Choix d’un algorithme de tri](#choose_sort)

##  <a name="parallel_for"></a> Algorithme parallel_for

Le [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorithme effectue à plusieurs reprises la même tâche en parallèle. Chacune de ces tâches est paramétré par une valeur d’itération. Cet algorithme est utile lorsque vous avez un corps de la boucle qui ne partage pas de ressources entre les itérations de cette boucle.

Le `parallel_for` algorithme partitionne les tâches de façon optimale pour l’exécution parallèle. Il utilise un algorithme de vol de travail et de vol pour équilibrer ces partitions lorsque les charges de travail sont déséquilibrées une plage. Lorsqu’une itération de boucle bloque de manière coopérative, le runtime redistribue la plage d’itérations est affectée au thread actuel à d’autres threads ou les processeurs. De même, lorsqu’un thread termine une plage d’itérations, le runtime redistribue travail à partir d’autres threads à ce thread. Le `parallel_for` algorithme prend également en charge *imbriqués parallélisme*. Lorsqu’une boucle parallèle contient une autre boucle parallèle, le runtime coordonne les ressources de traitement entre les instances de boucle dans un moyen efficace pour l’exécution parallèle.

Le `parallel_for` algorithme a plusieurs versions surchargées. La première version prend une valeur de début, une valeur de fin et une fonction de travail (une expression lambda, objet de fonction ou pointeur fonction). La deuxième version prend une valeur de début, une valeur de fin, une valeur par laquelle à l’étape et une fonction de travail. La première version de cette fonction utilise 1 comme valeur d’étape. Les autres versions acceptent des objets de partitionneur, qui vous permettent de spécifier comment `parallel_for` doivent partitionner des plages entre threads. Partitionneurs sont expliquées plus en détail dans la section [travail partitionnement](#partitions) dans ce document.

Vous pouvez convertir de nombreuses `for` boucles afin d’utiliser `parallel_for`. Toutefois, le `parallel_for` algorithme diffère la `for` instruction comme suit :

- Le `parallel_for` algorithme `parallel_for` n’exécute pas les tâches dans un ordre prédéterminé.

- Le `parallel_for` algorithme ne prend pas en charge les conditions d’arrêt arbitraires. Le `parallel_for` algorithme s’arrête quand la valeur actuelle de la variable d’itération est une inférieure à `last`.

- Le `_Index_type` paramètre de type doit être un type intégral. Ce type intégral peut être signé ou non signé.

- L’itération de boucle doit être vers l’avant. Le `parallel_for` algorithme lève une exception de type [std::invalid_argument](../../standard-library/invalid-argument-class.md) si le `_Step` paramètre est inférieur à 1.

- Le mécanisme de gestion des exceptions pour le `parallel_for` algorithme diffère de celle d’un `for` boucle. Si plusieurs exceptions se produisent simultanément dans un corps de boucle parallèle, le runtime propage une seule des exceptions sur le thread qui a appelé `parallel_for`. En outre, lorsqu’une itération de boucle lève une exception, le runtime n’interrompt pas immédiatement la boucle globale. Au lieu de cela, la boucle est placée dans l’état annulé et le runtime ignore les tâches qui n’ont pas encore démarré. Pour plus d’informations sur la gestion des exceptions et les algorithmes parallèles, consultez [gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Bien que le `parallel_for` algorithme ne prend pas en charge les conditions d’arrêt arbitraires, vous pouvez utiliser l’annulation pour arrêter toutes les tâches. Pour plus d’informations sur l’annulation, consultez [l’annulation dans la bibliothèque PPL](cancellation-in-the-ppl.md).

> [!NOTE]
>  Le coût de planification que les résultats à partir de l’équilibrage de charge et la prise en charge des fonctionnalités telles que l’annulation ne peuvent pas surmonter les avantages de l’exécution du corps de la boucle en parallèle, en particulier lorsque le corps de boucle est relativement faible. Vous pouvez réduire cette surcharge à l’aide d’un partitionneur dans votre boucle parallèle. Pour plus d’informations, consultez [travail partitionnement](#partitions) plus loin dans ce document.

### <a name="example"></a>Exemple

L’exemple suivant montre la structure de base de la `parallel_for` algorithme. Cet exemple imprime sur la console chaque valeur dans la plage [1, 5] en parallèle.

[!code-cpp[concrt-parallel-for-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_1.cpp)]

Cet exemple produit la sortie suivante :

```Output
1 2 4 3 5
```

Étant donné que le `parallel_for` algorithme agit sur chaque élément en parallèle, l’ordre dans lequel les valeurs sont imprimées sur la console varie.

Pour obtenir un exemple complet qui utilise le `parallel_for` algorithme, consultez [Comment : écrire une boucle parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md).

[[Haut](#top)]

##  <a name="parallel_for_each"></a> Algorithme parallel_for_each

Le [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorithme effectue des tâches sur un conteneur itératif, telles que celles fournies par la bibliothèque Standard C++, en parallèle. Il utilise la même logique de partitionnement qui le `parallel_for` algorithme utilise.

Le `parallel_for_each` algorithme ressemble à la bibliothèque Standard C++ [std::for_each](../../standard-library/algorithm-functions.md#for_each) algorithme, à ceci près que le `parallel_for_each` algorithme exécute les tâches simultanément. Comme d’autres algorithmes parallèles, `parallel_for_each` n’exécute pas les tâches dans un ordre spécifique.

Bien que le `parallel_for_each` algorithme fonctionne sur les itérateurs vers l’avant et les itérateurs d’accès aléatoire, offre de meilleures performances avec les itérateurs d’accès aléatoire.

### <a name="example"></a>Exemple

L’exemple suivant montre la structure de base de la `parallel_for_each` algorithme. Cet exemple imprime sur la console chaque valeur dans un [std::array](../../standard-library/array-class-stl.md) objet en parallèle.

[!code-cpp[concrt-parallel-for-each-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_2.cpp)]

Cet exemple produit la sortie suivante :

```Output
4 5 1 2 3
```

Étant donné que le `parallel_for_each` algorithme agit sur chaque élément en parallèle, l’ordre dans lequel les valeurs sont imprimées sur la console varie.

Pour obtenir un exemple complet qui utilise le `parallel_for_each` algorithme, consultez [Comment : écrire une boucle parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md).

[[Haut](#top)]

##  <a name="parallel_invoke"></a> Algorithme parallel_invoke

Le [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorithme exécute un ensemble de tâches en parallèle. Elle ne retourne pas jusqu'à ce que chaque tâche se termine. Cet algorithme est utile lorsque vous avez plusieurs tâches indépendantes que vous souhaitez exécuter en même temps.

Le `parallel_invoke` algorithme prend comme paramètres une série de fonctions de travail (fonctions lambda, objets de fonction ou pointeurs de fonction). Le `parallel_invoke` algorithme est surchargé pour prendre entre deux et dix paramètres. Chaque fonction que vous passez à `parallel_invoke` doit prendre les paramètres nuls.

Comme d’autres algorithmes parallèles, `parallel_invoke` n’exécute pas les tâches dans un ordre spécifique. La rubrique [parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md) explique comment la `parallel_invoke` algorithme associe à des tâches et des groupes de tâches.

### <a name="example"></a>Exemple

L’exemple suivant montre la structure de base de la `parallel_invoke` algorithme. Cet exemple appelle simultanément le `twice` fonction sur les trois variables locales et affiche le résultat sur la console.

[!code-cpp[concrt-parallel-invoke-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_3.cpp)]

Cet exemple génère la sortie suivante :

```Output
108 11.2 HelloHello
```

Pour obtenir des exemples complets qui utilisent le `parallel_invoke` algorithme, consultez [Comment : utiliser parallel_invoke pour écrire une Routine de tri parallèle](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md) et [Comment : utiliser parallel_invoke pour exécuter des opérations parallèles](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md).

[[Haut](#top)]

##  <a name="parallel_transform_reduce"></a> Les algorithmes parallel_transform et parallel_reduce

Le [concurrency::parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform) et [concurrency::parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce) algorithmes sont des versions parallèles des algorithmes de bibliothèque C++ Standard [std::transform](../../standard-library/algorithm-functions.md#transform)et [std::accumulate](../../standard-library/numeric-functions.md#accumulate), respectivement. Les versions du Runtime d’accès concurrentiel se comportent comme les versions de bibliothèque C++ Standard, à ceci près que l’ordre de l’opération n’est pas déterminé, car ils s’exécutent en parallèle. Utilisez ces algorithmes quand vous travaillez avec un jeu est assez grand pour obtenir des avantages de performance et évolutivité d’être traitées en parallèle.

> [!IMPORTANT]
>  Le `parallel_transform` et `parallel_reduce` algorithmes prennent en charge uniquement, bidirectionnel et le transfert itérateurs d’accès aléatoire, car ces itérateurs produisent des adresses mémoire stable. En outre, ces itérateurs doivent produire non -`const` l-values.

###  <a name="parallel_transform"></a> Algorithme parallel_transform

Vous pouvez utiliser le `parallel transform` algorithme pour effectuer de nombreuses opérations de parallélisation de données. Par exemple, vous pouvez :

- Ajuster la luminosité d’une image et effectuer d’autres opérations de traitement d’image.

- Additionner ou prendre le produit scalaire entre deux vecteurs et effectuer d’autres calculs numériques sur les vecteurs.

- Effectuer un rayon 3D, où chaque itération fait référence à un pixel qui doit être restitué.

L’exemple suivant montre la structure de base qui est utilisée pour appeler le `parallel_transform` algorithme. Cet exemple inverse chaque élément d’un std ::[vecteur](../../standard-library/vector-class.md) objet de deux manières. La première méthode utilise une expression lambda. La deuxième méthode utilise [std::negate](../../standard-library/negate-struct.md), qui dérive à son [std::unary_function](../../standard-library/unary-function-struct.md).

[!code-cpp[concrt-basic-parallel-transform#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_4.cpp)]

> [!WARNING]
>  Cet exemple illustre l’utilisation de base de `parallel_transform`. Étant donné que la fonction de travail n’effectue pas une quantité importante de travail, une augmentation significative des performances n’est pas attendue dans cet exemple.

Le `parallel_transform` algorithme a deux surcharges. La première surcharge prend une plage d’entrée et une fonction unaire. La fonction unaire peut être une expression lambda qui prend un argument, un objet de fonction ou un type qui dérive de `unary_function`. La deuxième surcharge prend deux plages d’entrée et une fonction binaire. La fonction binaire peut être une expression lambda qui prend deux arguments, un objet de fonction ou un type qui dérive de [std::binary_function](../../standard-library/binary-function-struct.md). L’exemple suivant illustre ces différences.

[!code-cpp[concrt-parallel-transform-vectors#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_5.cpp)]

> [!IMPORTANT]
>  L’itérateur que vous fournissez pour la sortie de `parallel_transform` doit chevaucher complètement l’itérateur d’entrée ou se chevauchent pas du tout. Le comportement de cet algorithme n’est pas spécifié si les itérateurs d’entrée et de sortie se chevauchent partiellement.

###  <a name="parallel_reduce"></a> Algorithme parallel_reduce

Le `parallel_reduce` algorithme est utile lorsque vous disposez d’une séquence d’opérations qui répondent à la propriété associative. (Cet algorithme ne nécessite pas la propriété commutative.) Voici les opérations que vous pouvez effectuer avec `parallel_reduce`:

- Multiplier les séquences de matrices pour produire une matrice.

- Multiplie un vecteur par une séquence de matrices pour produire un vecteur.

- Calculer la longueur d’une séquence de chaînes.

- Associer une liste d’éléments, tels que les chaînes, dans un seul élément.

L’exemple de base suivant montre comment utiliser le `parallel_reduce` algorithme à combiner une séquence de chaînes en une seule chaîne. Comme avec les exemples pour `parallel_transform`, des gains de performances ne sont pas attendus dans cet exemple de base.

[!code-cpp[concrt-basic-parallel-reduce#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_6.cpp)]

Dans de nombreux cas, vous pouvez considérer `parallel_reduce` comme raccourci pour l’utilisation de la `parallel_for_each` algorithme avec le [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) classe.

###  <a name="map_reduce_example"></a> Exemple : Exécution du mappage et réduction en parallèle

Un *carte* opération applique une fonction à chaque valeur dans une séquence. Un *réduire* opération combine les éléments d’une séquence en une seule valeur. Vous pouvez utiliser la bibliothèque Standard C++ [std::transform](../../standard-library/algorithm-functions.md#transform) et [std::accumulate](../../standard-library/numeric-functions.md#accumulate) fonctions pour effectuer le mappage et réduire les opérations. Toutefois, pour nombreux problèmes, vous pouvez utiliser la `parallel_transform` algorithme pour effectuer l’opération de mappage en parallèle et le `parallel_reduce` algorithme effectuer l’opération de réduction en parallèle.

L’exemple suivant compare le temps nécessaire pour calculer la somme des nombres premiers en série et en parallèle. La phase de mappage transforme les valeurs non prime sur 0 et les sommes de phase de réduction les valeurs.

[!code-cpp[concrt-parallel-map-reduce-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_7.cpp)]

Pour un autre exemple qui effectue un mappage et réduire les opérations en parallèle, consultez [Comment : effectuer un mappage et réduire les opérations en parallèle](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).

[[Haut](#top)]

##  <a name="partitions"></a> Partitionnement du travail

Pour paralléliser une opération sur une source de données, une étape essentielle consiste à *partition* la source en plusieurs sections accessibles simultanément par plusieurs threads. Un partitionneur spécifie comment un algorithme parallèle doit-elle partitionner des plages entre threads. Comme expliqué précédemment dans ce document, la bibliothèque PPL utilise une valeur par défaut, mécanisme qui crée une charge de travail initial, puis utilise un algorithme de vol de travail et de vol pour équilibrer ces partitions lorsque les charges de travail sont déséquilibrées une plage de partitionnement. Par exemple, lorsqu’une itération de boucle termine une plage d’itérations, le runtime redistribue travail à partir d’autres threads à ce thread. Toutefois, dans certains scénarios, vous souhaiterez spécifier un autre mécanisme de partitionnement qui convient le mieux à votre problème.

Le `parallel_for`, `parallel_for_each`, et `parallel_transform` algorithmes fournissent des versions surchargées qui prennent un paramètre supplémentaire, `_Partitioner`. Ce paramètre définit le type de partitionneur qui divise le travail. Voici les types de partitionneurs la bibliothèque PPL définit :

[Concurrency::affinity_partitioner](../../parallel/concrt/reference/affinity-partitioner-class.md)<br/>
Divise fonctionne en un nombre fixe de plages (en général, le nombre de threads de travail qui sont disponibles pour travailler sur la boucle). Ressemble à ce type de partitionneur `static_partitioner`, mais améliore l’affinité du cache selon la manière dont il est mappé à des plages aux threads de travail. Ce type de partitionneur peut améliorer les performances quand une boucle est exécutée sur le même jeu de données plusieurs fois (par exemple, une boucle dans une boucle) et les données tiennent dans le cache. Ce partitionneur ne participe pas entièrement à l’annulation. Il n’utilise pas la sémantique blocage coopérative et ne peut donc pas être utilisée avec des boucles parallèles qui ont une dépendance directe.

[Concurrency::auto_partitioner](../../parallel/concrt/reference/auto-partitioner-class.md)<br/>
Divise fonctionne dans un nombre initial de plages (en général, le nombre de threads de travail qui sont disponibles pour travailler sur la boucle). Le runtime utilise ce type par défaut lorsque vous n’appelez pas un algorithme parallèle surchargé qui prend un `_Partitioner` paramètre. Chaque plage peut être divisé en sous-plages, et ce qui permet l’équilibrage de charge doit avoir lieu. Lorsqu’une plage de travail se termine, le runtime redistribue les sous-plages de travail à partir d’autres threads pour ce thread. Utilisez ce partitionneur si votre charge de travail n’est pas comprise dans une des autres catégories, ou vous avez besoin de prise en charge complète pour l’annulation ou de blocage coopératif.

[Concurrency::simple_partitioner](../../parallel/concrt/reference/simple-partitioner-class.md)<br/>
Divise fonctionne en plages telles que chaque plage ait au moins le nombre d’itérations qui sont spécifiées par la taille de segment donné. Ce type de partitionneur participe à l’équilibrage de charge ; Toutefois, le runtime ne pas divise des plages en sous-plages. Pour chaque travail, le runtime vérifie l’annulation et effectue l’équilibrage de charge après `_Chunk_size` effectuer des itérations.

[Concurrency::static_partitioner](../../parallel/concrt/reference/static-partitioner-class.md)<br/>
Divise fonctionne en un nombre fixe de plages (en général, le nombre de threads de travail qui sont disponibles pour travailler sur la boucle). Ce type de partitionneur peut améliorer les performances, car elle n’utilise pas de vol de travail et par conséquent a moins de surcharge. Utilisez ce type de partitionneur lors de chaque itération d’une boucle parallèle effectue une quantité fixe et uniforme de travail et ne pas besoin d’assistance pour l’annulation ou de transférer le blocage coopératif.

> [!WARNING]
>  Le `parallel_for_each` et `parallel_transform` algorithmes prennent en charge uniquement les conteneurs qui utilisent des itérateurs d’accès aléatoire (tels que std ::[vecteur](../../standard-library/vector-class.md)) pour les partitionneurs statique, simple et une affinité. L’utilisation de conteneurs qui utilisent bidirectionnel et itérateurs génère une erreur de compilation. Le partitionneur par défaut, `auto_partitioner`, prend en charge les trois de ces types d’itérateur.

En règle générale, ces partitionneurs sont utilisés de la même façon, à l’exception de `affinity_partitioner`. La plupart des types de partitionneur ne conservent pas l’état et ne sont pas modifiées par le runtime. Par conséquent, vous pouvez créer ces objets partitionneur sur le site d’appel, comme illustré dans l’exemple suivant.

[!code-cpp[concrt-static-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_8.cpp)]

Toutefois, vous devez passer un `affinity_partitioner` objet en tant que non -`const`, l-value de référence afin que l’algorithme peut stocker l’état pour les futures boucles à réutiliser. L’exemple suivant montre une application de base qui effectue la même opération sur un jeu de données en parallèle plusieurs fois. L’utilisation de `affinity_partitioner` peut améliorer les performances, car le tableau est susceptible d’être contenue dans le cache.

[!code-cpp[concrt-affinity-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_9.cpp)]

> [!CAUTION]
>  Soyez prudent lorsque vous modifiez le code existant qui s’appuie sur la sémantique de blocage coopérative à utiliser `static_partitioner` ou `affinity_partitioner`. Ces types de partitionneur n’utilisent pas l’équilibrage de charge ou de vol de plage et par conséquent peuvent modifier le comportement de votre application.

La meilleure façon de déterminer s’il faut utiliser un partitionneur dans un scénario donné consiste à faire des essais et mesurer la durée d’opérations se terminent sous configurations de l’ordinateur et de charges représentatives. Par exemple, le partitionnement statique peut accélérer considérablement les opérations sur un ordinateur multicœur doté de quelques cœurs, mais il peut entraîner des ralentissements sur les ordinateurs qui disposent de nombreux cœurs.

[[Haut](#top)]

##  <a name="parallel_sorting"></a> Tri parallèle

La bibliothèque PPL fournit trois algorithmes de tri : [concurrency::parallel_sort](reference/concurrency-namespace-functions.md#parallel_sort), [concurrency::parallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort), et [concurrency::parallel_radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort). Ces algorithmes de tri sont utiles lorsque vous avez un jeu de données qui peuvent tirer parti en cours de tri en parallèle. En particulier, de tri en parallèle est utile lorsque vous avez un jeu de données volumineux ou lorsque vous utilisez une opération de comparaison coûtent cher en calcul trier vos données. Chacun de ces algorithmes trie les éléments en place.

Le `parallel_sort` et `parallel_buffered_sort` algorithmes sont les deux algorithmes en fonction de comparaison. Autrement dit, ils comparent les éléments par valeur. Le `parallel_sort` algorithme ne présente aucune mémoire supplémentaire et convient pour le tri à usage général. Le `parallel_buffered_sort` réalisables par algorithme mieux que `parallel_sort`, mais il nécessite d’espace o (n).

Le `parallel_radixsort` algorithme est basé sur hachage. Autrement dit, il utilise des clés de type entier pour trier des éléments. À l’aide de clés, cet algorithme peut calculer directement de la destination d’un élément au lieu d’utiliser des comparaisons. Comme `parallel_buffered_sort`, cet algorithme nécessite d’espace o (n).

Le tableau suivant récapitule les propriétés importantes des trois algorithmes de tri parallèle.

|algorithme|Description|Mécanisme de tri|Stabilité de tri|Besoins en mémoire|Complexité du temps|Itérateur|
|---------------|-----------------|-----------------------|--------------------|-------------------------|---------------------|---------------------|
|`parallel_sort`|À usage général tri basé sur la comparaison.|En fonction de comparaison (croissant)|Instable|Aucun.|O((N/P)log(N/P) + 2N((P-1)/P))|Aléatoire|
|`parallel_buffered_sort`|Plus rapidement à usage général basée sur la comparaison de tri qui nécessite d’espace o (n).|En fonction de comparaison (croissant)|Instable|Nécessite plus d’espace o (n)|O((N/P)log(N))|Aléatoire|
|`parallel_radixsort`|Entier basé sur clé tri qui nécessite d’espace o (n).|En fonction de hachage|Stable|Nécessite plus d’espace o (n)|O(N/P)|Aléatoire|

L’illustration suivante montre les propriétés importantes des trois algorithmes de tri parallèle plus graphiquement.

![Comparaison des algorithmes de tri](../../parallel/concrt/media/concrt_parallel_sorting.png "comparaison des algorithmes de tri")

Ces algorithmes de tri parallèle suivent les règles de l’annulation et la gestion des exceptions. Pour plus d’informations sur l’annulation et la gestion des exceptions dans le Runtime d’accès concurrentiel, consultez [annulation d’algorithmes parallèles](../../parallel/concrt/cancellation-in-the-ppl.md#algorithms) et [gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

> [!TIP]
>  Ces algorithmes de tri parallèle prend en charge une sémantique de déplacement. Vous pouvez définir un opérateur d’assignation de déplacement pour permettre les opérations de permutation se produise plus efficacement. Pour plus d’informations sur la sémantique de déplacement et l’opérateur d’assignation de déplacement, consultez [déclarateur de référence Rvalue : & &](../../cpp/rvalue-reference-declarator-amp-amp.md), et [constructeurs de déplacement et opérateurs d’assignation déplacer (C++)](../../cpp/move-constructors-and-move-assignment-operators-cpp.md). Si vous ne fournissez pas un opérateur d’assignation de déplacement ou de la fonction de l’échange, les algorithmes de tri utilisent le constructeur de copie.

L’exemple de base suivant montre comment utiliser `parallel_sort` pour trier un `vector` de `int` valeurs. Par défaut, `parallel_sort` utilise [std::less](../../standard-library/less-struct.md) pour comparer des valeurs.

[!code-cpp[concrt-basic-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_10.cpp)]

Cet exemple montre comment fournir une fonction de comparaison personnalisée. Il utilise le [std::complex::real](../../standard-library/complex-class.md#real) méthode trier [std::complex\<double >](../../standard-library/complex-double.md) valeurs dans l’ordre croissant.

[!code-cpp[concrt-basic-parallel-sort#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_11.cpp)]

Cet exemple montre comment fournir une fonction de hachage pour le `parallel_radixsort` algorithme. Cet exemple trie les points 3D. Les points sont triés en fonction de leur distance par rapport à un point de référence.

[!code-cpp[concrt-parallel-sort-points#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_12.cpp)]

À titre d’illustration, cet exemple utilise un jeu de données relativement faible. Vous pouvez augmenter la taille initiale du vecteur à faire des essais avec les améliorations des performances sur gros volumes de données.

Cet exemple utilise une expression lambda en tant que la fonction de hachage. Vous pouvez également utiliser une des implémentations intégrées de la std ::[hash, classe](../../standard-library/hash-class.md) ou définir vos propres spécialisation. Vous pouvez également utiliser un objet de fonction de hachage personnalisé, comme illustré dans cet exemple :

[!code-cpp[concrt-parallel-sort-points#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_13.cpp)]

[!code-cpp[concrt-parallel-sort-points#3](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_14.cpp)]

La fonction de hachage doit retourner un type intégral ([std::is_integral::value](../../standard-library/is-integral-class.md) doit être **true**). Ce type intégral doit être convertible en type `size_t`.

###  <a name="choose_sort"></a> Choix d’un algorithme de tri

Dans de nombreux cas, `parallel_sort` fournit le meilleur compromis entre les performances de vitesse et de la mémoire. Toutefois, en tant que vous augmentez la taille de votre jeu de données, le nombre de processeurs disponibles ou la complexité de votre fonction de comparaison, `parallel_buffered_sort` ou `parallel_radixsort` peut être plus performant. La meilleure façon de déterminer quel algorithme de tri à utiliser dans un scénario donné consiste à faire des essais et de mesurer le temps nécessaire pour trier les données par défaut en fonction des configurations d’ordinateur représentatives. Gardez les instructions suivantes à l’esprit lorsque vous choisissez une stratégie de tri.

- La taille de votre jeu de données. Dans ce document, un *small* jeu de données contient moins de 1 000 éléments, un *moyenne* dataset contienne entre 10 000 et 100 000 éléments et un *volumineux* dataset contient plus de 100 000 éléments.

- La quantité de travail qui effectue de votre fonction de comparaison ou d’une fonction de hachage.

- La quantité de ressources informatiques disponibles.

- Les caractéristiques de votre jeu de données. Par exemple, un algorithme peut effectuer bien pour les données qui sont déjà presque triées, mais pas aussi bien pour les données qui ne sont pas entièrement triées.

- La taille de segment. Le paramètre facultatif `_Chunk_size` argument spécifie quand l’algorithme passe d’un parallèle pour une implémentation de tri en série comme elle subdivise le tri global en plus petites unités de travail. Par exemple, si vous fournissez 512, l’algorithme passe à l’implémentation en série lorsqu’une unité de travail contient des éléments de moins de 512. Une implémentation en série peut améliorer les performances globales, car elle élimine la surcharge requise pour traiter les données en parallèle.

Il peut être utile de trier un petit jeu de données en parallèle, même lorsque vous avez un grand nombre de ressources informatiques disponibles ou de votre fonction de comparaison ou d’une fonction de hachage effectue une quantité relativement importante de travail. Vous pouvez utiliser [std::sort](../../standard-library/algorithm-functions.md#sort) (fonction) pour trier les petits jeux de données. (`parallel_sort` et `parallel_buffered_sort` appeler `sort` lorsque vous spécifiez une taille de segment est plus grande que le jeu de données ; Toutefois, `parallel_buffered_sort` aurait à allouer de l’espace o (n), ce qui pouvait prendre plus de temps en raison de l’allocation de mémoire ou de contention de verrouillage.)

Si vous devez économiser la mémoire ou votre allocateur de mémoire est soumis à des conflits de verrouillage, utilisez `parallel_sort` pour trier un jeu de données de taille moyenne. `parallel_sort` ne nécessite aucun espace supplémentaire ; les autres algorithmes nécessitent d’espace o (n).

Utilisez `parallel_buffered_sort` pour trier les jeux de données moyennes et lorsque votre application répond à la condition d’espace o (n) supplémentaire. `parallel_buffered_sort` peut être particulièrement utile lorsque vous avez un grand nombre de ressources de calcul ou une fonction compare coûteuse ou la fonction de hachage.

Utilisez `parallel_radixsort` pour trier les jeux de données volumineux et lorsque votre application répond à la condition d’espace o (n) supplémentaire. `parallel_radixsort` peut être particulièrement utile lorsque l’opération de comparaison équivalente est plus onéreuse ou lorsque les deux opérations sont coûteuses.

> [!CAUTION]
>  Implémentation d’une bonne fonction de hachage, vous devez la plage de jeu de données et comment chaque élément dans le jeu de données est transformé en une valeur non signée correspondante. Étant donné que l’opération de hachage fonctionne sur les valeurs non signées, envisager une stratégie de tri différente si les valeurs de hachage non signé ne peut pas être générés.

L’exemple suivant compare les performances de `sort`, `parallel_sort`, `parallel_buffered_sort`, et `parallel_radixsort` par rapport au même jeu volumineux de données aléatoires.

[!code-cpp[concrt-choosing-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_15.cpp)]

Dans cet exemple, ce qui suppose qu’il est acceptable d’allouer de l’espace d’o (n) pendant le tri, `parallel_radixsort` offre les meilleures performances sur ce jeu de données sur cet ordinateur.

[[Haut](#top)]

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Guide pratique pour écrire une boucle parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)|Montre comment utiliser le `parallel_for` algorithme pour effectuer une multiplication de matrice.|
|[Guide pratique pour écrire une boucle parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)|Montre comment utiliser le `parallel_for_each` algorithme pour calculer le nombre de nombres premiers dans un [std::array](../../standard-library/array-class-stl.md) objet en parallèle.|
|[Guide pratique pour utiliser parallel_invoke pour écrire une routine de tri parallèle](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|Montre comment utiliser l'algorithme `parallel_invoke` pour améliorer les performances de l'algorithme de tri bitonique.|
|[Guide pratique pour utiliser parallel_invoke pour exécuter des opérations parallèles](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Montre comment utiliser l'algorithme `parallel_invoke` pour améliorer les performances d'un programme qui effectue plusieurs opérations sur une source de données partagée.|
|[Guide pratique pour exécuter des opérations de mappage et de réduction en parallèle](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|Montre comment utiliser le `parallel_transform` et `parallel_reduce` algorithmes pour effectuer un mappage et de réduire les opérations qui compte les occurrences de mots dans des fichiers.|
|[Bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Décrit la bibliothèque PPL, qui fournit un modèle de programmation impérative qui favorise l’évolutivité et la facilité d’utilisation pour le développement d’applications simultanées.|
|[Annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md)|Explique le rôle de l’annulation dans la bibliothèque PPL, comment annuler un travail parallèle et comment déterminer quand un groupe de tâches est annulé.|
|[Gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Explique le rôle de gestion des exceptions dans le Runtime d’accès concurrentiel.|

## <a name="reference"></a>Référence

[parallel_for (fonction)](reference/concurrency-namespace-functions.md#parallel_for)

[parallel_for_each, fonction](reference/concurrency-namespace-functions.md#parallel_for_each)

[parallel_invoke, fonction](reference/concurrency-namespace-functions.md#parallel_invoke)

[affinity_partitioner, classe](../../parallel/concrt/reference/affinity-partitioner-class.md)

[auto_partitioner, classe](../../parallel/concrt/reference/auto-partitioner-class.md)

[simple_partitioner, classe](../../parallel/concrt/reference/simple-partitioner-class.md)

[static_partitioner, classe](../../parallel/concrt/reference/static-partitioner-class.md)

[parallel_sort, fonction](reference/concurrency-namespace-functions.md#parallel_sort)

[parallel_buffered_sort, fonction](reference/concurrency-namespace-functions.md#parallel_buffered_sort)

[parallel_radixsort, fonction](reference/concurrency-namespace-functions.md#parallel_radixsort)

